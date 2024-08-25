---
title: "Ultimate Software Crafter"
meta_title: "Quel est l'état de l'art des agents autonome de développement ?"
date: 2024-06-25T22:48:13+02:00
draft: false
authors: ["Wassel Alazhar", "Naji Alazhar"]
---

> Cet article fait suite à la présentation du même titre **Ultimate Software Crafter** que nous (Naji Alazhar et Wassel Alazhar) avons donnée le 25 juin 2024 au Meetup Crafting Data Science. [Cette présentation](https://speakerdeck.com/jcraftsman/the-ultimate-software-crafter-meetup-crafting-data-science) traîte de l'état de l'art des agents autonomes de développement logiciel et de leur fonctionnement.

{{< toc >}}

**"Ultimate Software Crafter"**—un titre qui résonne avec une touche de provocation. L'artisanat logiciel serait-il en voie de disparition ?

Depuis des années, les développeurs s'efforcent de rehausser les standards de leur métier, en cherchant constamment à allier excellence technique et professionnalisme. Aujourd'hui, avec l'émergence des agents autonomes de codage, une question se pose : ces nouvelles technologies menacent-elles cette quête d'amélioration continue, ou représentent-elles une opportunité inédite ? Avec ces technologies capables de générer du code de manière autonome, quel est encore le rôle du développeur dans la création logicielle ?

Cet article se propose de démystifier ces agents, de décortiquer leur fonctionnement et de réfléchir à leur impact potentiel sur notre métier.

Nous explorerons également comment des techniques éprouvées, comme le Test-Driven Development (TDD), peuvent être appliquées à ces agents pour transformer le développement logiciel automatisé.

Suivez-nous dans cette exploration où l'avenir du métier se dessine.

## Un Sujet Brûlant

L'agitation autour des agents autonomes de codage est palpable. Les annonces se succèdent, alimentées par des promesses parfois démesurées. [Devin](https://x.com/cognition_labs/status/1767548763134964000), par exemple, s'est fait connaître comme le "premier ingénieur logiciel IA", mais a rapidement [sombré dans la controverse](https://x.com/GergelyOrosz/status/1779035184978866332).

Les attentes étaient énormes, mais les résultats bien en deçà. D'autres, comme [GitHub Copilot Workspace](https://x.com/github/status/1785006787755721210), n'ont pas échappé au même sort, accumulant [les démos ratées](https://www.youtube.com/watch?v=75Hv0RUFIrQ) qui laissent le public sceptique. Ces agents sont encore en phase de développement, loin d'être prêts pour une adoption massive. On nous parle d'une révolution imminente, mais jusqu'à il n'y a pas très longtemps, seuls des produits fermés et des listes d'attente étaient disponibles.

Heureusement, des alternatives open-source commencent à voir le jour, offrant un peu plus de transparence et de compréhension. Parmi elles, [SWE-Agent](https://github.com/princeton-nlp/SWE-agent) se distingue, montrant que tout n'est pas qu'une question de marketing. Mais la tendance actuelle ne va pas s'atténuer de sitôt (avec [des modèles LLMs plus performant dans la génération de code](https://x.com/alexalbert__/status/1803804677701869748) et de plus en plus d'[alternatives open-sources avec des approches plus crédibles](https://www.tiktok.com/@steve8708/video/7382315491341126955)). Les débats autour de ces technologies, entre espoir et désillusion, continuent d'alimenter la conversation. Dans ce contexte bouillonnant, il devient crucial de démêler le vrai du faux et d'explorer ce dont ces agents sont vraiment capables.

<!-- markdownlint-disable MD033 -->

<div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 10px; max-width: 100%; margin: 0 auto;">
  <div style="flex: 1; min-width: 300px; max-width: 42%;">
    <blockquote class="twitter-tweet" data-dnt="true">
      <p lang="en" dir="ltr">
        Today we&#39;re excited to introduce Devin, the first AI software engineer.<br><br>
        Devin is the new state-of-the-art on the SWE-bench coding benchmark, has successfully passed practical engineering interviews from leading AI companies, and has even completed real jobs on Upwork… <a href="https://t.co/ladBicxEat">pic.twitter.com/ladBicxEat</a>
      </p>
      &mdash; Cognition (@cognition_labs)
      <a href="https://twitter.com/cognition_labs/status/1767548763134964000?ref_src=twsrc%5Etfw">March 12, 2024</a>
    </blockquote>
    <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
  </div>

  <div style="flex: 1; min-width: 300px; max-width: 42%;">
    <blockquote class="twitter-tweet">
      <p lang="en" dir="ltr">
        Devin (named “the world’s first AI engineer” from the start) and looked to me it’s far more marketing and hype than reality.<br><br>
        But even I didn’t assume how their own staged video would blatantly lie. It does. A software engineer looked closer. Damning:
        <a href="https://t.co/iKu8yfuFbA">https://t.co/iKu8yfuFbA</a>
      </p>
      &mdash; Gergely Orosz (@GergelyOrosz)
      <a href="https://twitter.com/GergelyOrosz/status/1779035184978866332?ref_src=twsrc%5Etfw">April 13, 2024</a>
    </blockquote>
    <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
  </div>
</div>

<!-- markdownlint-enable MD033 -->

Nous entrerons maintenant dans le vif du sujet en analysant les capacités actuelles des agents de codage autonomes. Que peuvent-ils réellement accomplir ?

## Quelles sont les capacités actuelles des agents de codage ? État de l'art

Quand nous parlons d'agent autonome de codage, nous faisons référence à un programme capable de résoudre une tâche en toute autonomie et de soumettre une Pull Request (PR) à partir d'une demande de changement (issue, tâche, ou User Story) fournie sous forme de texte ou provenant d'un outil de gestion comme GitHub Issues, Jira, ou Notion.

Répondre à la question "Quelles sont les capacités actuelles des agents de codage ?" est cependant complexe pour plusieurs raisons. Les performances de ces agents varient considérablement en fonction des tâches, des environnements, et des modèles sous-jacents utilisés. De plus, les benchmarks et les études montrent des résultats en constante évolution, rendant difficile une évaluation stable. Enfin, les contextes d'application, les types de problèmes résolus et la manière dont ces agents sont intégrés aux processus existants influencent également leurs capacités réelles.

Pour tenter de répondre à cette question, nous nous appuyons sur deux études récentes qui, malgré quelques limites et biais, restent parmi les sources les plus sérieuses disponibles :

1. **SWE-Agent: Agent-Computer Interfaces Enable Automated Software Engineering** ([Lire sur arXiv](https://arxiv.org/abs/2405.15793))
2. **SWE-bench: Can Language Models Resolve Real-World GitHub Issues?** ([Lire sur arXiv](https://arxiv.org/abs/2310.06770))

### Benchmarking et résultats

SWE-bench est une référence pour évaluer les performances des agents de codage. Le protocole est rigoureux : l'agent reçoit le commit parent d'une PR résolue et doit proposer une nouvelle PR qui sera validée en exécutant tous les tests associés. Ce processus permet de vérifier la capacité de l'agent à résoudre les problèmes de manière autonome, sans engendrer de régressions.

![SWE-bench, benchmarking protocol](/images/blog/swe-bench-protocol.png)

**SWE-bench Full** Ce dataset contient 2294 tâches à résoudre (GitHub issues) sélectionées depuis 12 des dépôts GitHub python les plus populaires (Django, flask, matplotlib, requests, scikit learn, sympy…). Les repos ciblés répondaient aux critères suivants : des guidelines de contrinutions claires, une bonne couverture de tests, globalement bien maintenu (avec des commits réguliers).

**SWE-bench Lite** est un dataset allégé, conçu pour se concentrer sur des issues plus ciblées et éliminer les variables qui pourraient biaiser les résultats. Cette version exclut, entre autres, les issues avec des dépendances externes ou des images, celles dont la description est trop courte (moins de 40 mots), ainsi que les PR touchant à plusieurs fichiers. Avec 300 issues sélectionnées pour leur clarté et leur maintenabilité, SWE-bench Lite fournit un cadre plus précis (et surtout plus économique) pour évaluer la performance des agents dans un environnement contrôlé.

![SWE-bench, The evolution of agent's issues resolution performance](/images/blog/swe-bench-evolution.png)

Les résultats obtenus peuvent impressionner, mais ils doivent être interprétés avec précaution. L'évolution rapide des performances, comme illustré dans le graphique ci-dessus, montre une amélioration continue des taux de résolution. Cependant, tous les résultats ne sont pas toujours comparables. Par exemple, AutoCodeRover avec GPT-4 a atteint 19 % de réussite, mais cela inclut trois exécutions distinctes (Pass@3) et le temps de résolution est bien plus lent que d'autres agents.

Dans cet environnement de données souvent complexes, nous recommandons de se concentrer sur des résultats transparents et vérifiés, notamment ceux obtenus en open-source, avec une seule exécution (Pass@1). À ce jour, ces taux atteignent 18,13 % pour le benchmark standard et 26,67 % pour SWE-bench Lite.

> OpenAI s'est également intéressé à ce domaine, proposant [SWE-bench Verified](https://openai.com/index/introducing-swe-bench-verified/), un ensemble de 500 problèmes validés par des ingénieurs logiciels, offrant ainsi un cadre d'évaluation encore plus rigoureux.

### Limitations et Opportunités

#### Limitations

Les agents actuels montrent des lacunes lorsqu'ils doivent traiter des issues nécessitant peu de modifications ou lorsque les descriptions sont trop concises. De plus, notre analyse se concentre uniquement sur la phase allant de l'issue à la PR, excluant ainsi :

- Le travail après la PR (revue, tests, déploiement, monitoring…)
- Le travail avant l'issue (discussions, formulation des besoins…)

#### Opportunités 🚧

Malgré ces limitations, les agents autonomes présentent un potentiel économique intéressant :

- **149,58 jours-homme pour 600 $**, contre 75 000 $ en méthode traditionnelle.

Détails :

- Coût : < 2 $ par issue (API GPT-4o) + infrastructure d'exécution.
- Résultats : 54 issues résolues sur 300, soit 149,58 jours-homme.
- Coût moyen par jour-homme : 4,01 $.

Les résultats pour SWE-bench Lite sont encore plus impressionnants :

- **221,63 jours-homme pour 50 $**, contre 111 000 $ en méthode traditionnelle.

### Potentiel d'amélioration

#### Exécutions multiples

Les taux de réussite peuvent être améliorés en multipliant les tentatives. Comme le montre le Pass@k, plusieurs exécutions d'une même issue peuvent significativement augmenter les performances globales.

#### Amélioration de la qualité du feedback

Un autre levier d'amélioration réside dans la qualité du feedback fourni à l'agent pendant la résolution des issues. En intégrant une approche "test-first", nous pensons que ces taux de réussite pourraient encore augmenter. Le feedback en continu permettrait à l'agent de corriger ses erreurs plus efficacement, améliorant ainsi la qualité et la pertinence des PR générées.

### Vers une compréhension plus approfondie : Comment fonctionnent réellement les agents de codage ?

Les capacités actuelles des agents de codage ouvrent de nouvelles perspectives pour l'automatisation de l'ingénierie logicielle, mais elles soulèvent aussi des questions sur la manière dont ces technologies s'intègrent dans nos pratiques existantes. Pour approfondir notre exploration, nous allons maintenant examiner comment ces agents fonctionnent en détail et comment ils peuvent être optimisés pour un impact maximal.

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
2. **SWE-bench: Can Language Models Resolve Real-World GitHub Issues?** - [Lire sur arXiv](https://arxiv.org/abs/2310.06770)
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
5. **Tweet d'Alex Albert sur la tendance du code généré par LLMs** - [Twitter](https://x.com/alexalbert__/status/1803804677701869748)
6. **Vidéo TikTok sur l'approche Test-First utilisée par Micro Agent** - [TikTok](https://www.tiktok.com/@steve8708/video/7382315491341126955)
7. **Alberto Brandolini sur l'importance de la compréhension des développeurs** - [Twitter](https://twitter.com/ziobrando)
8. **Gregor Hohpe sur les problèmes inutiles en informatique d'entreprise** - [Twitter](https://x.com/ghohpe/status/1782429303948583284)
9. **Derek Comartin sur les développeurs et les goulots d'étranglement du codage** - [Twitter](https://x.com/codeopinion/status/1601987262559944705)
10. **Présentation "Le vieux monde se meurt, le nouveau monde tarde à apparaître, et dans ce clair-obscur surgissent les monstres" par Arnaud Lemaire** - [Speaker Deck](https://speakerdeck.com/lilobase/le-vieux-monde-se-meurt-le-nouveau-monde-tarde-a-apparaitre-et-dans-ce-clair-obscur-surgissent-les-monstres-agile-pays-basque-2019?slide=107)
11. **Kent Beck sur l'impact des cycles de feedback** - [Twitter](https://x.com/KentBeck/status/1148263160006107136)

### Repositories de code liés à SWE-Agent et micro-agent

- **SWE-Agent sur GitHub** - [Princeton NLP](https://github.com/princeton-nlp/SWE-agent)
- **Micro-Agent sur GitHub** - [BuilderIO](https://github.com/BuilderIO/micro-agent)
