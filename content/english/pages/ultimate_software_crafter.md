---
title: "Ultimate Software Crafter"
date: 2024-06-25T22:48:13+02:00
draft: false
authors: Wassel Alazhar, Naji Alazhar
---

**"Ultimate Software Crafter"**—un titre qui résonne avec une touche de provocation. L'artisanat logiciel serait-il en voie de disparition ?

Depuis des années, les développeurs s'efforcent de rehausser les standards de leur métier, en cherchant constamment à allier excellence technique et professionnalisme. Aujourd'hui, avec l'émergence des agents autonomes de codage, une question se pose : ces nouvelles technologies menacent-elles cette quête d'amélioration continue, ou représentent-elles une opportunité inédite ? Avec ces technologies capables de générer du code de manière autonome, quel est encore le rôle du développeur dans la création logicielle ?

Cet article se propose de démystifier ces agents, de décortiquer leur fonctionnement et de réfléchir à leur impact potentiel sur notre métier.

Nous explorerons également comment des techniques éprouvées, comme le Test-Driven Development (TDD), peuvent être appliquées à ces agents pour transformer le développement logiciel automatisé.

Suivez-nous dans cette exploration où l'avenir du métier se dessine.

## Un Sujet Brûlant

L'agitation autour des agents autonomes de codage est palpable. Les annonces se succèdent, alimentées par des promesses parfois démesurées. Devin, par exemple, s'est fait connaître comme le "premier ingénieur logiciel IA", mais a rapidement sombré dans la controverse. Les attentes étaient énormes, mais les résultats bien en deçà. D'autres, comme GitHub Copilot Workspace, n'ont pas échappé au même sort, accumulant les démos ratées qui laissent le public sceptique. Ces agents sont encore en phase de développement, loin d'être prêts pour une adoption massive. On nous parle d'une révolution imminente, mais pour l'instant, seuls des produits fermés et des listes d'attente sont disponibles.

Heureusement, des alternatives open-source commencent à voir le jour, offrant un peu plus de transparence et de compréhension. Parmi elles, SWE-Agent se distingue, montrant que tout n'est pas qu'une question de marketing. Mais la tendance actuelle ne va pas s'atténuer de sitôt. Les débats autour de ces technologies, entre espoir et désillusion, continuent d'alimenter la conversation. Dans ce contexte bouillonnant, il devient crucial de démêler le vrai du faux et d'explorer ce dont ces agents sont vraiment capables.

Nous entrerons maintenant dans le vif du sujet en analysant les capacités actuelles des agents de codage autonomes. Que peuvent-ils réellement accomplir ?

## Quelles sont les capacités actuelles des agents de codage ? État de l'art

La réponse à cette question n'est pas simple
Mais le mieux qu'on a trouvé pour répondre à cette question sont :

1. **SWE-Agent: Agent-Computer Interfaces Enable Automated Software Engineering** - [Lire sur arXiv](https://arxiv.org/abs/2405.15793)
2. **SWE-Bench: Can Language Models Resolve Real-World GitHub Issues?** - [Lire sur arXiv](https://arxiv.org/abs/2310.06770)

### Examen des capacités actuelles des agents de codage, au-delà du battage médiatique

Dans cette partie on va s'intéresser aux agents de codage qui ont la capacité de soumettre en toute autonomie une PR à partir d'une demande de changement (issue / tâche / US) du texte qu'on donne à l'agent ou auquel il peut y accéder depuis un outil de ticketing (comme github issue par exemple, ou Jira ou Notion...)

### Présentation du benchmark SWE-Bench et de ses résultats, y compris les taux de résolution des problèmes par les agents

Expliquer le protocol de SWE-BENCH [à partir du papier](https://arxiv.org/abs/2310.06770)

Annoncer les résultats

2 remarques principales :

- Ça va vite, très vite. Illustrer par un graphe avec le max des taux à chaque date
- Méfiez-vous des résultats publiés dans le leaderboard. On a vérifié quelques un et on a trouvé que les résultats publiés sont trompeurs. Par exemple, les 19% annoncé de "🤠 AutoCodeRover (v20240408) + GPT 4 (0125)" sont issue des résultats aggrégés de 3 executions (Pass@3) en plus il est trop lent par rapport à SWE-agent. On expliquera plus tard l'impact, l'intérêt et les challenges d'aggréger les résultats de plusieurs executions.

Pour l'instant, dans un climat où il est difficile de voir clair, notre recommendation c'est de ne s'intéresser dans ce leaderboard qu'aux résultats qui cochent toutes les cases (open source pour la transparence, vérifiés et le taux concerne une seul execution Pass @1)
avec ça on arrive à  18.13% aujourdh'hui (13% au moment quand nous avons fait notre présentaiton la première fois le 25/06/2024) et 26.67% pour le dataset bench-lite.

Expliquer la différence entre SWE-BENCH et [SWE-BENCH lite](https://www.swebench.com/lite.html)

### Opportunités et limitations observées avec l'utilisation des agents dans l'automatisation de l'ingénierie logicielle

#### Limitations

Dans l'état, les agents ne savent pas encore résoudre :

- Issues that don't require many changes
- The issue description is concise and self-contained
Dans cette étude on focalise sur travail entre l'issue et la PR, càd la partie du travail du développeur qui une fois le besoin du changement est formulé et lécriture du code càd avant sa revue et sonintégration de ce changement à la base principale ce qui exclue :
- Work after the PR (review, test, release, monitor...)
- Work before the issue (conversation, formulation...)

#### Opportunités

Déjà dans l'état, on pourrait pensait qu'il aurait un intérêt économique;
Si on se met dans la peau d'un décideur, on pourrait être facilement tenté par l'idée avec ce calcul approximatif :

149.58 man day
for 600$
instead of 75K$*

(*) assuming 500$ average daily rate

Détail du calcul :
Cost:

- < 2$ per issue (Gpt-4o LLM api)
- few $ for the agent execution infrastructure
- 300 issue => ~600$
Expected benefits:
- 54 / 300 issues solved
- 2.77 man day / issue (avg)
- 18% *2.77* 300 = 149.58 man days
- (300 * 2$) / 149.58 = 4.01 $ cost per man day
- 2-10 min / issue

“It costs on average ~2.77 days for developers to create pull requests…” [samples from SWE-Bench-Lite dataset]
Source: “AutoCodeRover: Autonomous Program Improvement” paper. <https://arxiv.org/pdf/2404.05427>

Et pour 26.67%

221.63 man day
for 50$
instead of 111K$*

détail du calcul :
Cost :

- 0.15 $ per issue (Sonnet 3.5 LLM api)
- few $ for the agent execution infrastructure
- 300 issue => ~50$
Expected benefits:
- 2.77 man day / issue (avg)
- 26.67% *2.77* 300 = 221.63 man days
- 50$ / 221.63 ~ 0.23 $ cost per man day
- 2-10 min / issue

#### Potentiel d'amélioration grâce aux executions multiples

En réalité, ces taux peuvent être améliorés de manière sygnificative sans améliorer l'agent ou le modèle qu'il y a derrière. Il suffit de relancer plusieurs fois (et là on explique l'impact du Pass@k) qu'on avait introduit avant en citant la source ci-dessous

Extrait de <https://arxiv.org/pdf/2405.15793> :
B.5 Performance Variance and Pass@k Rate
Since running SWE-agent on SWE-bench can be rather expensive, we perform, all results, unless
otherwise stated, are reported using a pass@1 metric (% Resolved). However, we also test our main
SWE-agent configuration for a higher number of runs to test the variance and pass@k performance
for k ∈ {3, 6}. These results are shown in Table 10, suggesting that average performance variance is
relatively low, though per-instance resolution can change considerably.
Table 10: Performance for 6 separate runs of SWE-agent with GPT-4 on SWE-bench Lite. The %
Resolved rate for each individual run is shown in the first table, and the pass@k rate in the second.
SWE-bench Lite
Run 1 Run 2 Run 3 Run 4 Run 5 Run 6 Avg.
Resolve % 17.33 18.00 18.00 18.67 17.33 18.33 17.940.49
Pass@1 Pass@2 Pass@3 Pass@4 Pass@5 Pass@6
Pass@k 17.94 23.89 27.35 29.67 31.33 32.67

#### Potentiel d'amélioration en améliorant la qualité du feedback dont dispose l'agent pendant la résolution

En réalité nous pensons, que ce taux peux être encore amélioré en l'état

## Démonstration en Direct (## Live Demo)

- Description détaillée de la démonstration en direct présentée dans le talk.
- Explication des concepts de base des agents autonomes et de leur fonctionnement.
- Analyse de la performance des agents en utilisant une approche "Test-First".

issue marshmallow:

- Démo avec swe-agent gpt-4o en tdd
- puis swe-agent deepseek-coder v2 en TDD
- puis avec Gitlab-ci

## Comment Fonctionnent les Agents de codage ?

(Alternative de titre : ## Comment ça marche un agent autonome de développement ?)

- Exploration des principes de base des agents autonomes.
- Analyse des principales conclusions sur leur fonctionnement, y compris l'importance des démos et des exemples.
- Discussion sur les défis et les solutions pour améliorer la performance des agents.

## L'Impact de l'Approche "Test-First"

- Discussion sur comment l'approche "Test-First" améliore la performance des agents.
- Importance des cycles de rétroaction pour corriger les erreurs et améliorer les résultats des agents.
- Perspectives sur l'avenir de l'ingénierie logicielle automatisée avec une adoption plus large de TDD (Test-Driven Development).

## Défis Principaux et Directions Futures

- Identification des principaux défis liés aux modèles, au contexte, aux coûts et aux données.
- Exploration des futures directions, y compris l'amélioration des interfaces d'agents et l'intégration avec des systèmes de surveillance et de gestion des exceptions en temps réel.

## Conclusion et Appel à la Discussion

(Alternative de titre : ## Et après ? Discutons-en !)

- Synthèse des points abordés dans la présentation.
- Invitation à discuter des implications de ces innovations pour l'avenir de l'ingénierie logicielle.

## Références

### Publications académiques et articles

1. **SWE-Agent: Agent-Computer Interfaces Enable Automated Software Engineering** - [Lire sur arXiv](https://arxiv.org/abs/2405.15793)
2. **SWE-Bench: Can Language Models Resolve Real-World GitHub Issues?** - [Lire sur arXiv](https://arxiv.org/abs/2310.06770)
3. **AutoCodeRover: Autonomous Program Improvement** - [Lire sur arXiv](https://arxiv.org/pdf/2404.05427)
4. **Canon TDD, by Kent Beck** - [Lire sur Tidy First](https://tidyfirst.substack.com/p/canon-tdd)
5. **ReAct: Synergizing Reasoning and Acting in Language Models** - [Lire sur arXiv](https://arxiv.org/abs/2210.03629)
6. **Applying Generative AI to CVE remediation – early vulnerability patching in Continuous Integration Pipelines** - [Lire l'article](https://aws.amazon.com/fr/blogs/containers/applying-generative-ai-to-cve-remediation-early-vulnerability-patching-in-continuous-integration-pipelines/)
7. **Map Evolution not Maturity, by Simon Wardley** - [Lire sur Medium](https://medium.com/@swardley/map-evolution-not-maturity-bae6ea1a2743)
8. **Wardley Maps, by Simon Wardley** - [Télécharger le PDF](https://coach-agile.com/wp-content/uploads/2022/09/Wardley-Maps-Simon-Wardley-compresse.pdf)
9. **Clean Code, Robert C. Martin (2008)** - Citation : "One might argue that a book about code is somehow behind the times that code is no longer the issue; that we should be concerned about models and requirements instead."

### Liens, tweets et vidéos (par ordre d'apparition)

1. **Debunking Devin: "First AI Software Engineer" Upwork lie exposed!** - [YouTube](https://www.youtube.com/watch?v=tNmgmwEtoWE)
2. **Analyse critique de Devin par Gergely Orosz** - [Twitter](https://twitter.com/GergelyOrosz/status/1779035184978866332)
3. **Annonce de GitHub Copilot Workspace** - [Twitter](https://x.com/github/status/1785006787755721210)
4. **Vidéo YouTube sur les démos ratées de GitHub Copilot** - [YouTube](https://www.youtube.com/watch?v=75Hv0RUFIrQ)
5. **Vidéo TikTok sur l'approche Test-First utilisée par Micro Agent** - [TikTok](https://www.tiktok.com/@steve8708/video/7382315491341126955)
6. **Tweet d'Alex Albert sur la tendance du code généré par LLMs** - [Twitter](https://x.com/alexalbert__/status/1803804677701869748)
7. **Alberto Brandolini sur l'importance de la compréhension des développeurs** - [Twitter](https://twitter.com/ziobrando)
8. **Gregor Hohpe sur les problèmes inutiles en informatique d'entreprise** - [Twitter](https://x.com/ghohpe/status/1782429303948583284)
9. **Derek Comartin sur les développeurs et les goulots d'étranglement du codage** - [Twitter](https://x.com/codeopinion/status/1601987262559944705)
10. **Présentation "Le vieux monde se meurt, le nouveau monde tarde à apparaître, et dans ce clair-obscur surgissent les monstres" par Arnaud Lemaire** - [Speaker Deck](https://speakerdeck.com/lilobase/le-vieux-monde-se-meurt-le-nouveau-monde-tarde-a-apparaitre-et-dans-ce-clair-obscur-surgissent-les-monstres-agile-pays-basque-2019?slide=107)
11. **Kent Beck sur l'impact des cycles de feedback** - [Twitter](https://x.com/KentBeck/status/1148263160006107136)

### Repositories de code liés à SWE-Agent et micro-agent

- **SWE-Agent sur GitHub** - [Princeton NLP](https://github.com/princeton-nlp/SWE-agent)
- **Micro-Agent sur GitHub** - [BuilderIO](https://github.com/BuilderIO/micro-agent)
