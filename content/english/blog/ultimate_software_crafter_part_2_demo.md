---
title: "Ultimate Software Crafter - Partie 2 - Agents autonomes de codage, voyez par vous-même !"
meta_title: "Agents autonomes de codage, voyez par vous-même !"
date: 2024-06-25T22:48:13+02:00
draft: false
author: "Wassel Alazhar"
authors: ["Wassel Alazhar", "Naji Alazhar"]
categories: ["Software Engineering", "AI", "Automation"]
tags: ["LLM", "BENCHMARK", "SWE-Agent", "SWE-bench", "AI", "Automation", "Software Engineering", "Test-Driven Development", "TDD", "Demo", "DIY"]
---

Dans cet article, je vous propose de plonger dans l'univers des agents autonomes de codage. Après avoir exploré le concept dans [la première partie](https://umans.tech/blog/ultimate_software_crafter_part_1_intro_sota/), il est temps de passer à la pratique avec trois démonstrations en vidéo. Nous mettrons à l'épreuve plusieurs agents dans des contextes réels pour voir de quoi ils sont capables et comment ils peuvent être intégrés dans des environnements professionnels. Préparez-vous, le monde du développement logiciel est en ébullition, et ce n'est que le début.

## Vidéo 1 : Résolution d'Issue avec un Agent Autonome de codage [SWE-crafter 🤖]

<!-- markdownlint-disable MD033 -->
<div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 10px; max-width: 100%; margin: 0 auto;">
    <iframe width="1156" height="650" src="https://www.youtube.com/embed/acDNJ12zQCo?list=PLgGDmRSp6p-OMy42xSFbkkwhMwq_B8Cvk" title="Résolution d&#39;Issue avec un Agent Autonome de codage SWE crafter 🤖" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
    </iframe>
</div>
<!-- markdownlint-enable MD033 -->

Pour cette première démonstration, j'ai mis [**SWE-crafter**](https://github.com/umans-tech/SWE-crafter), notre agent autonome maison, sur le coup d'une issue GitHub concernant une librairie Python. L'idée est simple : observer comment il s'y prend pour le résoudre en autonomie, en suivant le principe du **Test-Driven Development**.

L'agent commence par écrire un test pour reproduire le bug. Sans instructions spécifiques pour configurer l'environnement local, il se débrouille malgré quelques obstacles, comme des dépendances manquantes. Mais il ne se laisse pas décourager et parvient à faire passer le test.

Je lui ai d'abord demandé de résoudre le bug en utilisant le modèle **DeepSeek Coder**, ce qu'il a réussi avec succès. Puis, je lui ai proposé de refaire la même tâche avec **GPT-4**, et là encore, il a réussi. C'était intéressant de comparer les deux approches : l'un est efficace et va droit au but, l'autre apporte une finesse supplémentaire dans le code généré.

---

## Vidéo 2 : Intégration de SWE-Crafter dans GitLab-CI/GitHub Actions
<!-- markdownlint-disable MD033 -->
<div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 10px; max-width: 100%; margin: 0 auto;">
    <iframe width="1006" height="653" src="https://www.youtube.com/embed/QF-DxapUTWM?list=PLgGDmRSp6p-OMy42xSFbkkwhMwq_B8Cvk" title="Quand Gitlab-CI bosse, moi je plonge 🏊‍♂️💻 : Démo d’un agent autonome dans vos pipelines 🤖" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
    </iframe>
</div>
<!-- markdownlint-enable MD033 -->

Dans cette deuxième vidéo, j'ai poussé l'expérience plus loin en intégrant [SWE-crafter](https://github.com/umans-tech/SWE-crafter) directement dans une pipeline **GitLab-CI**. L'objectif ? Automatiser la résolution de bugs depuis la CI/CD, avec un minimum d'intervention humaine.

Dans la vidéo, je lance manuellement une pipeline en lui fournissant un numéro d'issue. La pipeline instancie l'agent, qui se charge de résoudre le bug en suivant une approche **Test-First**. Il soumet ensuite les modifications dans une PR opérationnelle.

Cette approche ouvre des perspectives intéressantes. On pourrait imaginer accélérer la résolution de certains bugs et réduire le temps passé sur des tâches répétitives. Mais cela soulève aussi des questions sur l'efficacité réelle de cette automatisation et son impact sur le flux de travail des développeurs.

> Si vous souhaitez tester cette intégration dans vos propres pipelines, j'ai mis à disposition quelques templates open-source que vous pouvez trouver ici : <https://github.com/umans-tech/issue-solver-bots>.
> C'est encore expérimental, mais j'ai l'intention d'ajouter pas mal de fonctionnalités.

---

## Vidéo 3 : Développement et déploiement d'une Application Web avec Replit Agent en quelques minutes

<!-- markdownlint-disable MD033 -->
<div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 10px; max-width: 100%; margin: 0 auto;">
    <iframe width="1156" height="650" src="https://www.youtube.com/embed/_GNx17F_DDA?list=PLgGDmRSp6p-OMy42xSFbkkwhMwq_B8Cvk" title="Développement et déploiement d&#39;une Application Web avec Replit Agent en quelques minutes" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
    </iframe>
</div>

<!-- markdownlint-enable MD033 -->

Pour la troisième démonstration, j'ai testé l'agent de développement fraîchement annoncé par [**Replit**](https://replit.com/~). Je lui ai demandé de développer une application de réservation d'hôtel. En quelques minutes, l'agent propose une architecture avec **Flask**, **Vanilla JS** et **PostgreSQL**.

Il code l'application, configure l'environnement et déploie un prototype fonctionnel. Il intègre même des fonctionnalités avancées comme le paiement avec **Stripe**. Certes, le design est basique, mais pour un prototype réalisé en un temps record, c'est bluffant.

---

### Conclusion

On pourrait être tenté de conclure rapidement que plus d'automatisation équivaut à plus de productivité et de gain de temps. Mais mon expérience en développement m'a appris à adopter une analyse plus systémique. En réalité, nous manquons encore de recul.

Nous pourrions être à l'aube d'une ère de collaboration intensive entre l'intelligence humaine et l'IA, où il nous faudra redécouvrir et réinventer nos méthodes de travail. Par exemple, l'automatisation de la résolution de bugs pourrait sembler un gain de temps, mais tant qu'elle nécessite une revue humaine (et pour l'instant, c'est le cas), il n'est pas certain que le gain soit réel. La mise en production reste conditionnée par le rythme de revue des développeurs humains.

De plus, si l'effort de configuration et de revue s'avère finalement supérieur à la tâche de développement elle-même, est-ce que cela en vaut vraiment la peine ? Surtout que les tâches complexes, celles qui échappent encore aux agents, sont souvent les plus critiques.

Et si, au final, faire fonctionner ces agents demande de plus en plus d'expertise pour les maintenir opérationnels, le bénéfice est-il toujours là ? Sans oublier que trop d'automatisation pourrait priver les développeurs d'opportunités d'apprentissage, au point que la complexité générée ne soit plus maîtrisée.

Le marché est en effervescence, chaque jour apporte son lot de nouveautés, et il y a un immense terrain à explorer et à tester. Mais il est crucial de prendre le temps d'évaluer l'impact réel de ces outils sur notre travail et de réfléchir à la meilleure façon de les intégrer dans nos pratiques sans perdre de vue l'essentiel.

Dans le prochain article de cette série, nous plongerons dans les coulisses de ces agents pour comprendre comment ils fonctionnent réellement. Préparez-vous, car les choses deviennent vraiment intéressantes.
