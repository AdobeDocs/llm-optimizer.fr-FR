---
title: Analyse du Sentiment Reddit
description: Découvrez comment LLM Optimizer analyse les threads Reddit pour afficher des recommandations qui améliorent la perception et la visibilité de votre marque dans les résultats Recherche optimisée par l'IA.
feature: Opportunities
source-git-commit: fa8b994aa55869cf7f2607e792acc4e8abc213e7
workflow-type: tm+mt
source-wordcount: '1163'
ht-degree: 1%

---


# Analyse du Sentiment Reddit

Reddit est une source de données essentielle pour les modèles de langue volumineux. Lorsque les utilisateurs interrogent les assistants d&#39;IA sur votre marque, les réponses sont influencées par le sentiment de contenu Reddit. La manière dont votre marque est discutée au sein des subreddits détermine directement la manière dont les systèmes d’IA la comprennent et la représentent dans les réponses générées.

L’opportunité d’analyse du Sentiment Reddit s’affiche lorsque des threads Reddit sont détectés comme citations pour les invites dans l’ensemble d’invites de votre tableau de bord Présence des marques. Il analyse les fils de discussion cités et leurs commentaires pour le sentiment, la part de voix et les sujets récurrents. L’opportunité affiche ensuite les recommandations prioritaires afin d’améliorer la manière dont votre marque est perçue et citée par les systèmes d’IA.

Il analyse votre marque à travers quatre dimensions :

- **Publications analysées** — Nombre de publications Reddit examinées pour les mentions de marque et le sentiment.
- **Commentaires analysés** — Nombre de commentaires examinés dans les publications analysées.
- **Mentions de marque (threads)** — Fréquence à laquelle votre marque est mentionnée dans les threads analysés.
- **sentiment global (threads)** - sentiment agrégé vers votre marque sur les threads analysés.

>[!NOTE]
>L&#39;analyse du Sentiment Reddit est actuellement en version bêta. Les fonctionnalités et la disponibilité peuvent changer à mesure que la fonctionnalité continue de se développer.

![Tableau de bord Reddit Sentiment Analysis](/help/dashboards/opportunities/assets/reddit-sentiment-overview.png)

## Fonctionnement

LLM Optimizer surveille les threads Reddit cités par les systèmes d’IA pour les invites dans le jeu d’invites de votre tableau de bord Présence des marques. Lorsque des threads cités sont détectés, il analyse ces threads et leurs commentaires pour les citations de mentions de marque, de sentiment, de part de voix et d’IA. Il compare la performance de votre marque par rapport à celle de vos concurrents, identifie les sujets récurrents qui alimentent le sentiment et génère des recommandations pour combler les écarts de perception.

Si aucun thread Reddit n’est cité pour les invites de votre jeu d’invites, cette opportunité n’apparaîtra pas dans votre tableau de bord.

Les résultats s’affichent dans deux onglets : **Suggestions** et **Performances**.

## Suggestions

Cet onglet affiche des recommandations pour améliorer la perception de votre marque sur Reddit. Les suggestions sont organisées en trois sous-onglets : **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**.

![Onglet Suggestions](/help/dashboards/opportunities/assets/reddit-sentiment-suggestions.png)

Le tableau des suggestions comprend les colonnes suivantes :

- **Suggestion** — L&#39;amélioration recommandée pour combler un écart de perception.
- **Priorité** — Niveau d’urgence (critique, élevé, Medium, faible).
- **Éléments action** — Ouvre un panneau contenant des étapes spécifiques pour mettre en œuvre la recommandation, y compris les équipes responsables (par exemple, relations publiques, gestion de la communauté, marketing produit).
- **Preuve** — Ouvre une table Sources montrant les threads Reddit derrière la suggestion.

Le développement d’une suggestion révèle une section **Analyse IA** avec :

- **Pourquoi cela nécessite une amélioration** — Une explication de l&#39;écart de perception identifié, y compris le contexte concurrentiel et comment le problème se forme dans les fils Reddit.
- **Comment l’améliorer** — Orientations spécifiques sur le contenu ou les actions qui permettraient de combler le fossé.
- **Résultat prévu** — Résultat prévu de la mise en œuvre de la recommandation.

Le tableau **Sources** montre les threads Reddit qui pilotent la suggestion, avec les colonnes suivantes :

- **Thread** — Titre et lien vers le thread Reddit.
- **Subreddit** — Le subreddit où le thread a été publié.
- **Engagement** — Niveau d’engagement (faible, Medium, élevé).
- **Mentions de marque** — Nombre de vos mentions de marque par rapport au nombre total de mentions dans le thread.
- **Part de voix** — Part des mentions de votre marque par rapport à toutes les marques mentionnées.
- **Top 5 des marques** — Les marques les plus mentionnées dans le fil.
- **Sentiment** — sentiment global envers votre marque dans le thread.
- **Citations de l’IA** — Nombre de réponses de l’IA qui ont cité ce fil.

## Performances

L’onglet **Performances** fournit une répartition détaillée des performances de votre marque sur l’ensemble du contenu Reddit. Il est organisé en quatre sections.

### Paysage du marché

Compare les performances de votre marque par rapport aux marques associées et aux concurrents du marché en fonction des mentions dans les fils de discussion.

![Paysage du marché](/help/dashboards/opportunities/assets/reddit-sentiment-landscape.png)

Il montre :

- **Mentions de marque dans les threads** — Votre part de voix par rapport aux marques associées et aux concurrents du marché.
- **Suivi du marché** — Graphique filtrable dans lequel vous pouvez sélectionner jusqu’à cinq marques concurrentes pour comparer la part de voix entre les threads.

### Analyse des sentiments

Effectue le suivi de la perception de la marque sur les threads analysés avec un graphique de **distribution des Sentiments** indiquant la répartition en pourcentage des sentiments favorables, neutres et défavorables sur les threads.

![Analyse de Sentiment &#x200B;](/help/dashboards/opportunities/assets/reddit-sentiment-distribution.png)

### Threads

Tableau détaillé des threads Reddit analysés avec les colonnes suivantes :

- **Thread** — Titre et lien vers le thread Reddit.
- **Subreddit** — Le subreddit où le thread a été publié.
- **Engagement** — Niveau d’engagement (faible, Medium, élevé).
- **Mentions de marque** — Nombre de vos mentions de marque par rapport au nombre total de mentions dans le thread.
- **Part de voix** — Part des mentions de votre marque par rapport à toutes les marques mentionnées.
- **Top 5 des marques** — Les marques les plus mentionnées dans le fil.
- **Sentiment** — sentiment global envers votre marque dans le thread.
- **Citations de l’IA** — Nombre de réponses de l’IA qui ont cité ce fil.

### Rubriques

Un tableau des rubriques récurrentes identifiées dans les threads analysés, présentant :

- **Sujet** — Thème ou sujet récurrent identifié.
- **Mentions de marque** — Nombre de mentions de marque associées à la rubrique.
- **Sentiment** — sentiment global associé à la rubrique.

Cliquez sur **Détails** sur n’importe quelle rubrique pour ouvrir un panneau d’analyse avec deux onglets :

- **Analyse** — Un résumé de la façon dont votre marque est discutée dans les threads associés à cette rubrique.
- **Sources** — Les threads Reddit spécifiques qui contribuent au signal de sentiment du sujet.

## Faites un essai dans la démonstration

Découvrez l’opportunité Reddit Sentiment Analysis en action en utilisant l’environnement de démonstration Frescopa.

[Afficher l&#39;analyse du Sentiment Reddit dans la démo Frescopa](https://play.llmo.now/org/demo-org/opportunities/reddit-analysis/b7e4d9a0-3c1f-4e2b-9d5a-8f2c1e0a7b4d?siteId=frescopa-demo)

## Questions fréquentes

**Pourquoi Reddit est-il important pour Recherche optimisée par l&#39;IA ?**

Reddit est l&#39;une des sources les plus pondérées dans les données de formation LLM et la récupération en temps réel. Lorsque les systèmes d&#39;IA génèrent des réponses sur les marques, les produits et les sujets, les discussions de Reddit éclairent souvent le ton, le cadrage et les affirmations factuelles de ces réponses. Une marque dont on parle de manière défavorable ou inexacte sur Reddit est plus susceptible d&#39;être représentée de cette manière dans les réponses générées par l&#39;IA.

**Pourquoi cette opportunité ne s’affiche-t-elle pas dans mon tableau de bord ?**

Cette opportunité s’affiche uniquement lorsque des threads Reddit sont détectés comme citations pour les invites dans votre ensemble d’invites du tableau de bord de Présence des marques. Si aucun thread Reddit n’est cité pour ces invites, l’opportunité ne s’affichera pas. À mesure que votre marque gagnera en couverture Reddit et que ces fils de discussion seront cités par les systèmes d&#39;IA pour votre prompteur, l&#39;opportunité deviendra disponible.

**Que signifie Sentiment global ?**

Le sentiment global reflète le ton agrégé des threads dans lesquels votre marque est mentionnée : favorable, neutre ou défavorable calculé sur tous les threads analysés.

**Qu’est-ce que la Part de voix ?**

La part de voix est le pourcentage de mentions de marque totales de votre marque dans un thread donné ou dans tous les threads analysés, par rapport à toutes les autres marques mentionnées.

**Que sont les citations d’IA ?**

Les citations d’IA indiquent le nombre de réponses d’IA citées par un thread donné. Un nombre plus élevé de citations par l’IA indique que le thread est activement utilisé par les systèmes d’IA lors de la génération de réponses sur des sujets connexes, ce qui rend le sentiment dans ces threads particulièrement important pour la représentation de l’IA de votre marque.

**Comment les concurrents du marché sont-ils identifiés ?**

Les concurrents sont identifiés automatiquement en fonction du secteur de votre marque et des marques les plus fréquemment co-mentionnées dans les threads analysés. Vous pouvez également sélectionner manuellement jusqu’à cinq marques à comparer dans le graphique de suivi du marché.

**À quelle fréquence l’analyse est-elle mise à jour ?**

L’analyse Reddit reflète le contenu analysé jusqu’à la date affichée dans l’en-tête du tableau de bord. Revoyez l’opportunité après la mise en œuvre des recommandations pour suivre les changements de sentiment et de part de voix.
