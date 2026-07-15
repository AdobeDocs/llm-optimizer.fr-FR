---
title: Analyse des sentiments des utilisateurs sur Reddit
description: Découvrez comment LLM Optimizer analyse les fils de discussion Reddit pour générer des recommandations qui améliorent la perception et la visibilité de votre marque dans les résultats de recherche optimisée par l’IA.
feature: Opportunities
autotag-review: '2026-07-15T18:05:47.495Z'
TQID: 'https://experienceleague.adobe.com/trt7J6hxXtRdGat8Ohhd32JkwwIAJ26G8M98pBrN1CY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2:
  - id: fe92ae96-fc87-4fea-96a0-adc06310d4f4
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1163
ht-degree: 100%

---


# Analyse des sentiments des utilisateurs sur Reddit

Reddit constitue une source de données essentielle pour les grands modèles de langage. Lorsque les utilisateurs et utilisatrices interrogent les assistants IA à propos de votre marque, les réponses sont influencées par les sentiments du contenu de Reddit. La manière dont on parle de votre marque dans les subreddits détermine directement la manière dont les systèmes d’IA la comprennent et la représentent dans les réponses générées.

L’opportunité d’analyse des sentiments sur Reddit s’affiche lorsque des fils de discussion Reddit sont détectés comme citations pour les prompts présents dans votre ensemble de prompts de votre tableau de bord de présence de la marque. Elle analyse les sentiments, la part de voix et les rubriques récurrentes dans ces fils de discussion cités et leurs commentaires. Elle affiche ensuite les recommandations prioritaires afin d’améliorer la manière dont votre marque est perçue et citée par les systèmes d’IA.

Elle analyse votre marque selon quatre critères :

- **Publications analysées** : nombre de publications Reddit examinées pour les mentions de marque et les sentiments.
- **Commentaires analysés** : nombre de commentaires examinés dans les publications analysées.
- **Mentions de marque (fils de discussion)** : la fréquence à laquelle votre marque est mentionnée dans les fils de discussion analysés.
- **Sentiment général (fils de discussion)** : sentiment global envers votre marque dans les fils de discussion analysés.

>[!NOTE]
>L’analyse des sentiments pour Reddit est actuellement en version bêta. Les fonctionnalités et la disponibilité peuvent évoluer avec le développement.

![Tableau de bord de l’analyse des sentiments pour Reddit](/help/dashboards/opportunities/assets/reddit-sentiment-overview.png)

## Fonctionnement

LLM Optimizer surveille les fils de discussion Reddit cités par les systèmes d’IA lorsqu’ils correspondent à des prompts inclus dans votre ensemble de prompts du tableau de bord de présence de la marque. Lorsque des fils de discussion cités sont détectées, il analyse ces fils et leurs commentaires afin d’identifier les mentions de marque, le sentiment, la part de voix et les citations d’IA. Il compare la performance de votre marque par rapport à celle de vos concurrents, identifie les rubriques récurrentes qui engendrent les sentiments et génère des recommandations pour améliorer la perception.

Si aucun fil de discussion Reddit cité n’est détecté pour les prompts de votre ensemble de prompts, cette opportunité n’apparaîtra pas dans votre tableau de bord.

Les résultats s’affichent dans deux onglets : **Suggestions** et **Performances**.

## Suggestions

Cet onglet affiche des recommandations pour améliorer la perception de votre marque sur Reddit. Les suggestions sont réparties en trois sous-onglets : **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**.

![Onglet Suggestions](/help/dashboards/opportunities/assets/reddit-sentiment-suggestions.png)

Le tableau des suggestions comprend les colonnes suivantes :

- **Suggestion** — L’amélioration recommandée pour améliorer la perception.
- **Priorité** — Niveau d’urgence (Critique, Élevé, Moyen, Faible).
- **Mesure pour agir** : ouvre un panneau contenant les étapes pour mettre en œuvre la recommandation, incluant les équipes responsables (par exemple, relations publiques, gestion de communauté, marketing produit).
- **Preuves** : ouvre un tableau Sources montrant les fils de discussion Reddit utilisés pour la suggestion.

Développer une suggestion fait apparaître une section **Analyse IA** qui contient ce qui suit :

- **Pourquoi il est nécessaire d’apporter une amélioration** : explication de l’écart de perception identifié, avec le contexte concurrentiel et la façon dont le problème se produit dans les fils de discussion Reddit.
- **Solutions d’amélioration** — Des conseils sur le contenu ou des actions qui permettraient d’améliorer la perception.
- **Résultat attendu** — Le résultat escompté de la mise en œuvre de la recommandation.

Le tableau **Sources** montre les fils de discussion Reddit à l’origine de la suggestion, avec les colonnes suivantes :

- **Fil de discussion** : titre et lien vers le fil de discussion Reddit.
- **Subreddit** — Le subreddit dans lequel le thread a été publié.
- **Engagement** — Niveau d’engagement (Faible, Moyen, Élevé).
- **Mentions de marque** — Nombre de mentions de votre marque par rapport au nombre total de mentions dans le thread.
- **Part de voix** — Part des mentions concernant votre marque par rapport à toutes les marques mentionnées.
- **Top 5 des marques** — Les marques les plus mentionnées dans le thread.
- **Sentiment** — Sentiment général à l’égard de votre marque dans le thread.
- **Citations de l’IA** — Nombre de réponses de l’IA qui ont cité ce thread.

## Performances

L’onglet **Performances** offre une analyse détaillée des performances de votre marque dans l’ensemble du contenu Reddit. Il est composé de quatre sections.

### Paysage du marché

Compare les performances de votre marque à celles des marques associées et des concurrents en s’appuyant sur les mentions dans les threads.

![Panorama du marché](/help/dashboards/opportunities/assets/reddit-sentiment-landscape.png)

Vous y trouverez ce qui suit :

- **Mentions de marque dans les threads** — Votre part de voix par rapport à celle des marques associées et des concurrents.
- **Suivi du marché** — Graphique filtrable dans lequel vous pouvez sélectionner jusqu’à cinq marques concurrentes pour comparer la part de voix entre les threads.

### Analyse des sentiments

Effectue le suivi de la perception de la marque sur les threads analysés avec un graphique de **répartition des sentiments** indiquant le pourcentage de sentiments favorables, neutres et défavorables sur les threads.

![Analyse des sentiments des utilisateurs](/help/dashboards/opportunities/assets/reddit-sentiment-distribution.png)

### Threads

Tableau détaillé des threads Reddit analysés avec les colonnes suivantes :

- **Fil de discussion** : titre et lien vers le fil de discussion Reddit.
- **Subreddit** — Le subreddit dans lequel le thread a été publié.
- **Engagement** — Niveau d’engagement (Faible, Moyen, Élevé).
- **Mentions de marque** — Nombre de mentions de votre marque par rapport au nombre total de mentions dans le thread.
- **Part de voix** — Part des mentions concernant votre marque par rapport à toutes les marques mentionnées.
- **Top 5 des marques** — Les marques les plus mentionnées dans le thread.
- **Sentiment** — Sentiment général à l’égard de votre marque dans le thread.
- **Citations de l’IA** — Nombre de réponses de l’IA qui ont cité ce thread.

### Rubriques

Tableau des sujets récurrents identifiés dans les threads analysés contenant les éléments suivants :

- **Rubrique** : thème ou sujet récurrent identifié.
- **Mentions de la marque** — Nombre de mentions de la marque associées au sujet en question.
- **Sentiment** — Sentiment global associé au sujet en question.

Cliquez sur **Détails** sur n’importe quel sujet pour ouvrir un panneau d’analyse avec deux onglets :

- **Analyse** — Résumé de la manière dont votre marque est évoquée dans les threads Reddit associés à ce sujet.
- **Sources** — Les threads Reddit qui reflètent le sentiment associé au sujet.

## Tester l’opportunité avec la démo

Découvrez l’opportunité Analyse des sentiments des utilisateurs sur Reddit dans l’environnement de démo Frescopa.

[Voir l’opportunité Analyses des sentiments des utilisateurs sur Reddit dans la démo Frescopa](https://play.llmo.now/org/demo-org/opportunities/reddit-analysis/b7e4d9a0-3c1f-4e2b-9d5a-8f2c1e0a7b4d?siteId=frescopa-demo)

## Questions fréquentes

**Pourquoi Reddit est-il important pour recherche optimisée par l’IA ?**

Reddit est l’une des sources les plus influentes dans les données d’entraînement des LLM et la récupération en temps réel. Lorsque les systèmes d’IA génèrent des réponses sur les marques, les produits et les sujets, les discussions de Reddit façonnent souvent le ton, les affirmations factuelles de ces réponses et la façon de les présenter. Une marque dont on parle de manière défavorable ou inexacte sur Reddit est plus susceptible d’être présentée de cette manière dans les réponses générées par l’IA.

**Pourquoi cette opportunité ne s’affiche-t-elle pas dans mon tableau de bord ?**

Cette opportunité s’affiche uniquement lorsque des threads Reddit sont détectés dans les réponses à vos invites de référence du tableau de bord de Présence de la marque. Si aucun thread Reddit n’est cité pour ces réponses, l’opportunité ne s’affiche pas. À mesure que votre marque gagne en visibilité sur Reddit et que ces threads sont citées par les systèmes d’IA en réponse à vos invites de référence, cette opportunité finira par s’afficher.

**Qu’est-ce que le sentiment général ?**

Le sentiment général fait référence au ton employé pour mentionner votre marque dans les threads (favorable, neutre ou défavorable), calculé à partir de tous les threads analysés.

**Qu’est-ce que la part de voix ?**

La part de voix correspond au pourcentage de mentions de votre marque parmi toutes les marques mentionnées dans un thread donné ou dans l’ensemble des threads analysés.

**Que sont les citations d’IA ?**

Les citations d’IA indiquent combien de réponses d’IA ont cité un thread donné. Un nombre élevé de citations d’IA indique que le thread est activement utilisé par les systèmes d’IA pour générer des réponses sur des sujets associés. Dans ce cas, le sentiment exprimé dans ces threads particulièrement important pour la représentation de votre marque par l’IA.

**Comment les concurrents du marché sont-ils identifiés ?**

Les concurrents sont identifiés automatiquement en fonction du secteur de votre marque et des marques les plus fréquemment mentionnées avec la vôtre dans les threads analysés. Vous pouvez sélectionner manuellement jusqu’à cinq marques pour les comparer dans le graphique de suivi du marché.

**À quelle fréquence l’analyse est-elle mise à jour ?**

L’analyse Reddit reflète le contenu analysé jusqu’à la date indiquée dans l’en-tête du tableau de bord. Revenez sur cette opportunité après la mise en œuvre des recommandations afin de suivre l’évolution du sentiment et de la part de voix.
