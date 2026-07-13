---
title: "GLM 5.2 NVFP4: Fast, Cheap, and Not Worth Serving"
meta_title: "Why Umans chose not to serve GLM 5.2 in NVFP4"
description: "We served GLM 5.2 quantized to NVFP4 at 200 tokens per second and could have gone faster. We retired it anyway. If the tokens are not useful, they are not worth serving, no matter how efficiently we can produce them."
date: 2026-07-13T00:00:00Z
image: "/images/image-placeholder.png"
categories: ["AI", "Infrastructure"]
author: "Wassel Alazhar"
tags: ["LLM", "NVFP4", "Quantization", "GLM", "Kimi", "Inference", "SWE-bench"]
draft: true
---

We ran a public experiment: serving GLM 5.2 quantized to NVFP4 on our own GPUs. The infrastructure side worked. We sustained around 200 tokens per second ([the archived status page tells the story](https://status.umans.ai/status/umans-glm-5.2-nvfp4)), and we know how to serve it even faster.

We retired it anyway.

**If the tokens are not useful, they are not worth serving, no matter how efficiently we can produce them.** 🙂

## What we tried

NVFP4 is NVIDIA's 4-bit floating-point format. On recent GPUs it roughly halves the memory footprint of an FP8 model and unlocks significantly higher throughput per dollar. For a coding platform like ours, where users run long agentic sessions with huge contexts, that efficiency is not a nice-to-have. It decides what we can offer and at what price.

So when an NVFP4 checkpoint of GLM 5.2 became available, we put it in front of real users as a time-boxed experiment: a dedicated model endpoint, a public status page, and a cohort of volunteers from our community who opted in and hammered it on real work.

## What we found

The serving side delivered. Throughput was strong from day one, latency was competitive, and the remaining engineering headroom was clear.

The output quality was not there. On software engineering evaluations and, more visibly, on long-running agentic tasks, GLM 5.2 NVFP4 fell measurably short of GLM 5.2 served at its native precision (FP8). Small per-step degradations that a chat benchmark barely registers compound quickly when a model works autonomously across hundreds of tool calls.

### What participants said

The Discord threads from the experiment tracked the whole arc, verbatim:

> "this thing is fast"

> "i feel like nvfp4 doenst reduce all that much quality [...] i got a fix for that, make it the main glm 5.2!!"

> "we need longer test before rush decision"

> "hopefully someone releases a QAT fork of nvidia's NVFP4 quant, that should bring the quality back up to on-par with fp8/fp16"

<!-- attribution (get consent or keep anonymous before publishing): 1) bazsi1__ 2) scanash 3) crazy_banana168 4) timgreen; all from the "GLM 5.2 nvfp4 is down (as expected)" thread in service-updates, 2026-06-30 to 07-02 -->

The enthusiasm for the speed was real, and some participants genuinely liked the model. But by the time we wrapped up, the summary we posted wrote itself: "feedback was consistent: speed was great, but for serious work the gap with fp8 was clear. so we're keeping quality first and closing this one out."

And that last participant quote, hoping for a QAT fork, anticipates exactly where the next section goes.

## Why it fell short (and why NVFP4 is not the villain)

The problem is not the 4-bit format. The problem is a precision mismatch between training and serving.

GLM 5.2 was not post-trained for NVFP4. There was no quantization-aware training (QAT) at that precision, so quantizing it after the fact shifts the numerics away from what the weights were trained to tolerate. Post-training quantization can be good enough for short interactions, but agentic coding is the worst case for it: long trajectories give every small error a chance to compound.

Contrast that with Kimi K2.7, which we also serve and which we have tested in NVFP4. K2.7 is post-trained with QAT at that same precision, which makes the quantization essentially lossless. On SWE-bench, K2.7 in NVFP4 performs on par with the full-precision weights. It even scores slightly higher in our runs, though the difference sits inside the confidence interval, so the honest claim is parity. That is what a format looks like when the model was trained to live in it.

Same format, opposite outcomes. The difference is not NVFP4. It is whether the lab shipped a model that was trained for it.

## The decision

Efficiency multiplies usefulness. Two hundred fast tokens per second of a model that cannot finish the job is not a product, it is a demo. So we chose not to serve GLM 5.2 NVFP4, and we keep serving GLM 5.2 at native precision.

The recipe stays on the shelf, ready for checkpoints that earn it: models post-trained at the precision we serve them at, validated on the benchmarks that match our users' workloads. K2.7 already proves the path works.

## Thank you

This experiment was only possible because members of our community volunteered their real workloads and their patience. Thank you. The fastest way to a trustworthy model lineup is users who tell us, bluntly, when the tokens are not useful.
