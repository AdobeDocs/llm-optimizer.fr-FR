---
title: Analyse des sentiments des utilisateurs cités
description: Découvrez comment LLM Optimizer analyse les URL les plus citées pour générer des recommandations qui améliorent la perception et la visibilité de votre marque dans les résultats de recherche optimisée par l’IA.
feature: Opportunities
autotag-review: '2026-07-15T17:45:11.828Z'
TQID: 'https://experienceleague.adobe.com/B-gDBklZ7XjMCQx-HaYx8H8yr9eZbXBvuRTAUfqJ-QU'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ab7fdb62-bd53-4cfd-8c2c-169f7e47f20e
subfeature_v2: id: cd42f7fa-7c4e-41cf-ba86-6e0de16ed456
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1030
ht-degree: 100%

---


# Analyse des sentiments des utilisateurs cités

Lorsque les systèmes d’IA répondent à des questions sur votre marque, ils s’appuient sur un ensemble d’URL qui sont le plus citées : il s’agit de pages web tierces fréquemment référencées dans les réponses générées par l’IA. La manière dont votre marque est présentée sur ces pages détermine directement la manière dont les systèmes d’IA la représentent pour les utilisateurs et les utilisatrices.

L’opportunité d’analyse des sentiments des utilisateurs et utilisatrices pour les éléments cités analyse les URL les plus mentionnées détectées dans les prompts de votre ensemble de prompts du tableau de bord de présence de la marque. Elle évalue les mentions de marque, le sentiment, la part de voix et les rubriques récurrentes sur ces pages. Ensuite, elle présente les recommandations prioritaires pour améliorer la manière dont votre marque est perçue dans le contenu sur lequel les systèmes d’IA s’appuient le plus.

Elle présente quatre mesures clés :

- **Pages analysées** : nombre de pages web citées examinées pour les mentions de marque et le sentiment.
- **Pages ignorées** : nombre de pages qui n’ont pas pu être analysées (par exemple, en raison de restrictions d’accès).
- **Mentions de marque (pages)** : fréquence à laquelle votre marque est mentionnée sur les pages analysées.
- **Sentiment général (pages)** : sentiment global envers votre marque sur les pages web analysées.

>[!NOTE]
>L’analyse des sentiments pour les éléments cités est actuellement en version bêta. Les fonctionnalités et la disponibilité peuvent évoluer avec le développement.

![Tableau de bord d’analyse des sentiments pour les éléments cités](/help/dashboards/opportunities/assets/cited-sentiment-overview.png)

## Fonctionnement

LLM Optimizer identifie les URL les plus citées apparaissant dans les réponses générées par l’IA pour les prompts de l’ensemble de prompts de votre tableau de bord de présence de la marque. Il analyse ces pages en fonction des mentions de marque, du sentiment, de la part de voix et des citations de l’IA. Il compare la performance de votre marque par rapport à celle de vos concurrents sur le marché, identifie les rubriques récurrentes et génère des recommandations pour combler les lacunes de perception sur les pages qui comptent le plus pour les systèmes d’IA.

Si aucune URL citée n’est détectée pour les prompts de votre ensemble de prompts, cette opportunité n’apparaîtra pas dans votre tableau de bord.

Les résultats s’affichent dans deux onglets : **Suggestions** et **Performances**.

## Suggestions

Cet onglet affiche des recommandations pour améliorer la perception de votre marque dans les URL les plus citées. Les suggestions sont organisées en trois sous-onglets : **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**.

![Onglet Suggestions](/help/dashboards/opportunities/assets/cited-sentiment-suggestions.png)

Le tableau des suggestions comprend les colonnes suivantes :

- **Suggestion** — L’amélioration recommandée pour améliorer la perception.
- **Priorité** — Niveau d’urgence (Critique, Élevé, Moyen, Faible).
- **Mesures pour agir** : ouvre un panneau contenant des étapes précises pour mettre en œuvre la recommandation, incluant les équipes responsables.

Le développement d’une suggestion révèle une section **Analyse de l’IA** qui comprend les éléments suivants :

- **Pourquoi cela nécessite une amélioration** : explication de l’écart de perception identifié, incluant les URL citées qui sous-représentent votre marque et votre contexte concurrentiel.
- **Solutions d’amélioration** : conseils spécifiques sur la sensibilisation, la création de contenu ou les actions de partenariat pour combler l’écart.
- **Résultat attendu** : le résultat escompté de la mise en œuvre de la recommandation.

## Performances

L’onglet **Performances** fournit une analyse détaillée des performances de votre marque sur les pages les plus citées. Il est composé de quatre sections.

### Paysage du marché

Compare les performances de votre marque par rapport aux marques associées et aux concurrents en fonction des mentions dans les pages citées.

![Panorama du marché](/help/dashboards/opportunities/assets/cited-sentiment-landscape.png)

Vous y trouverez ce qui suit :

- **Mentions de la marque dans les pages** : votre part de voix par rapport aux marques associées et aux concurrents.
- **Suivi du marché** : graphique filtrable où vous pouvez sélectionner jusqu’à cinq marques concurrentes pour comparer leurs parts de voix dans les pages analysées.

### Analyse des sentiments

Effectue le suivi de la perception de la marque sur les pages analysées avec un graphique de **distribution des sentiments** indiquant la répartition en pourcentage des sentiments favorables, neutres et défavorables sur les différentes pages.

![Analyse des sentiments](/help/dashboards/opportunities/assets/cited-sentiment-distribution.png)

### Pages

Tableau détaillé des pages web citées et analysées, avec les colonnes suivantes :

- **Page** : URL de la page analysée.
- **Mentions de marque** : nombre de vos mentions de marque par rapport au nombre total de mentions sur la page.
- **Part de voix** — La part de mentions de votre marque par rapport à toutes les marques mentionnées.
- **Top 5 des marques** : les marques les plus mentionnées sur la page.
- **Sentiment** : sentiment global envers votre marque sur la page.
- **Citations d’IA** : nombre de réponses d’IA ayant cité cette page.

### Rubriques

Tableau des rubriques récurrentes identifiées sur les pages analysées, présentant les éléments suivants :

- **Rubrique** : thème ou sujet récurrent identifié.
- **Mentions de la marque** — Nombre de mentions de la marque associées au sujet en question.
- **Sentiment** — Sentiment global associé au sujet en question.

Cliquez sur **Détails** sur n’importe quelle rubrique pour ouvrir une analyse récapitulative et les pages source correspondantes.

## Tester l’opportunité avec la démo

Voir l’opportunité d’analyse des sentiments des éléments cités en action en utilisant l’environnement de démonstration Frescopa - [Voir l’analyse des sentiments des éléments cités dans la démonstration Frescopa](https://play.llmo.now/org/demo-org/opportunities/cited-analysis/d3a8b217-9f4c-4e88-a612-6b7f91e5c044?siteId=frescopa-demo).

## Questions fréquentes

**Pourquoi les URL les plus citées sont-elles importantes pour la recherche optimisée par l’IA ?**

Les URL les plus citées sont les pages tierces auxquelles les systèmes d’IA font le plus souvent référence lorsqu’ils génèrent des réponses qui concernent votre marque. Le sentiment et le contexte de ces pages ont une influence directe et considérable sur la façon dont l’IA représente votre marque, plus que les pages qui sont rarement citées. L’amélioration de la représentation de votre marque sur ces pages spécifiques est l’une des actions les plus efficaces que vous pouvez entreprendre pour assurer votre visibilité dans l’IA.

**Pourquoi cette opportunité ne s’affiche-t-elle pas dans mon tableau de bord ?**

Cette opportunité s’affiche uniquement lorsque des URL citées sont détectées pour les prompts de l’ensemble de prompts de votre tableau de bord de présence de la marque. Si aucune URL citée n’a été identifiée pour ces prompts, l’opportunité ne s’affichera pas.

**Que sont les pages ignorées ?**

Les pages ignorées sont des URL citées qui n’ont pas pu être analysées, généralement parce que la page se trouve derrière une restriction d’accès payant, nécessite une authentification ou bloque les accès automatisés. Ces pages sont comptabilisées, mais exclues de l’analyse des sentiments et de la mention de marque.

**Qu’est-ce que la part de voix ?**

La part de voix est le pourcentage de mentions de marque totales de votre marque sur une page donnée ou sur toutes les pages analysées, par rapport à toutes les autres marques mentionnées.

**Que sont les citations d’IA ?**

Les citations d’IA indiquent combien de réponses d’IA ont cité une page donnée. Un nombre élevé de citations d’IA indique que la page est activement utilisée par les systèmes d’IA pour générer des réponses sur des rubriques associées. Dans ce cas, le sentiment exprimé dans ces pages est particulièrement important pour la représentation de votre marque par l’IA.

**Comment les concurrents sont-ils identifiés ?**

Les concurrents sont identifiés automatiquement en fonction du secteur de votre marque et des marques les plus fréquemment co-mentionnées dans les pages analysées. Vous pouvez sélectionner manuellement jusqu’à cinq marques pour les comparer dans le graphique de suivi du marché.

**À quelle fréquence l’analyse est-elle mise à jour ?**

L’analyse reflète les URL citées détectées jusqu’à la date indiquée dans l’en-tête du tableau de bord. Revenez sur cette opportunité après la mise en œuvre des recommandations afin de suivre l’évolution du sentiment et de la part de voix.
