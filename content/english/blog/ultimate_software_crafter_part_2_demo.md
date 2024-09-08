---
title: "Ultimate Software Crafter - Partie 2 - Agents autonomes de codage, voyez par vous-même !"
meta_title: "Agents autonomes de codage, voyez par vous-même !"
date: 2024-06-25T22:48:13+02:00
draft: false
author: "Wassel Alazhar"
authors: ["Wassel Alazhar", "Naji Alazhar"]
categories: ["Software Engineering", "AI", "Automation"]
tags: ["LLM", "BENCHMARK", "SWE-Agent", "SWE-bench", "AI", "Automation", "Software Engineering", "Test-Driven Development", "TDD"]
---

Dans cet article, je vous propose de plonger dans l'univers des agents autonomes de codage. Après avoir exploré le concept dans la première partie, il est temps de passer à la pratique avec trois démonstrations en vidéo. Nous mettrons à l'épreuve plusieurs agents dans des contextes réels pour voir de quoi ils sont capables et comment ils peuvent être intégrés dans des environnements professionnels.

## Vidéo 1 : Résolution d'Issue avec un Agent Autonome de codage [SWE-crafter 🤖]

<!-- markdownlint-disable MD033 -->
<div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 10px; max-width: 100%; margin: 0 auto;">
    <iframe width="1156" height="650" src="https://www.youtube.com/embed/acDNJ12zQCo" title="Résolution d&#39;Issue avec un Agent Autonome de codage SWE crafter 🤖" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
    </iframe>
</div>
<!-- markdownlint-enable MD033 -->

Dans cette vidéo, on se lance dans l'aventure avec SWE-crafter, notre agent autonome de codage maison. Objectif : résoudre une issue GitHub sur une librairie Python. Le principe est simple : on donne un problème à l'agent, et il doit se débrouiller pour configurer l'environnement, écrire des tests, corriger le bug, et proposer une PR finale. Facile, non ?

On commence par lui donner l'issue, et l'agent écrit un test pour reproduire le bug. Il n’y arrive pas du premier coup, mais il est tenace. Après quelques allers-retours avec des dépendances Python capricieuses (parce que bon, Python et l’indentation, c’est toujours fun), il finit par faire passer le test. La correction est minimale – un petit arrondi dans le code – mais efficace.

Côté analyse, on met en avant les différences entre deux modèles : Deepseek coder et GPT-4o. Le premier fait le boulot sans trop de fioritures, mais le second semble un peu plus malin, notamment en nettoyant le code superflu. Bref, SWE-crafter n’est pas encore parfait, mais il apprend vite. Résultat : une PR propre, prête à être mergée.

---

## Vidéo 2 : Intégration de SWE-Crafter dans GitLab-CI/GitHub Actions

[Lien vers la vidéo]

---

## Vidéo 3 : Développement et déploiement d'une Application Web avec Replit Agent en quelques minutes

<!-- markdownlint-disable MD033 -->
<div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 10px; max-width: 100%; margin: 0 auto;">
    <iframe width="1156" height="650" src="https://www.youtube.com/embed/_GNx17F_DDA" title="Développement et déploiement d&#39;une Application Web avec Replit Agent en quelques minutes" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
    </iframe>
</div>

<!-- markdownlint-enable MD033 -->

Là, on change d’agent et de contexte. On teste un agent de développement fraîchement annoncé par Replit, et autant dire que cet agent ne fait pas les choses à moitié. Il ne se contente pas de générer du code : il configure, déploie et te fait presque le café.

On lui donne une tâche simple : développer une application de réservation d'hôtel. Pas de panique, en quelques minutes, l’agent propose un plan avec Flask, Vanilla JS et PostgreSQL. Sympa. Il code, configure l’environnement, et nous sort un premier prototype fonctionnel. Le tout en temps réel, avec une interaction digne d’un vrai développeur (ou presque).

L’agent va même plus loin, en proposant une intégration de paiement avec Stripe, et en modifiant au fur et à mesure l’interface de l’appli. Le résultat ? Un MVP opérationnel, déployé en production. Côté design, ça ne casse pas trois pattes à un canard (on dirait Bootstrap des années 2010), mais pour un premier jet en 15 minutes, c’est bluffant. Quelques bugs ici et là, mais l’agent s’en sort bien. On déploie, et voilà, l'application est en ligne.

---

### Conclusion

Ces trois démonstrations illustrent clairement le potentiel des agents autonomes de codage pour automatiser une grande partie du processus de développement, que ce soit dans la résolution d'issues, l'intégration dans des pipelines CI/CD, ou même le déploiement d'applications complètes. Si ces agents montrent des capacités impressionnantes, il est également crucial de comprendre comment ils fonctionnent en profondeur.

Dans le prochain article de la série, nous explorerons précisément cela : comment marchent ces agents autonomes ? Quels sont les mécanismes derrière leur prise de décision et leur capacité à interagir avec un environnement de développement ? Restez connectés pour plonger dans les coulisses de cette technologie prometteuse !

---

Qu'en penses-tu ?
