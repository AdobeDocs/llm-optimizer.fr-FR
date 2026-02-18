---
title: Présence de la marque
description: Découvrez comment utiliser le tableau de bord de présence de la marque pour comprendre comment votre marque est perçue au niveau des réponses générées par l’IA.
feature: Brand Presence
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: ht
source-wordcount: '1299'
ht-degree: 100%

---


# Présence de la marque {#brand-presence}

Le tableau de bord de présence de la marque fournit un aperçu détaillé de la manière dont votre marque est perçue au niveau des réponses générées par l’IA.Il indique où, à quelle fréquence et dans quel contexte votre marque est mentionnée.Vous pouvez utiliser ce tableau de bord pour mesurer la visibilité, suivre les citations et explorer les tendances du sentiment.Le tableau de bord est divisé en plusieurs sections, chacune fournissant des informations différentes.Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

![Présence de la marque](/help/dashboards/assets/brand-main.png)

Cette page contient les éléments suivants :

* [Filtres](#filters)
* [Métriques générales](##key-metrics)
* [Comparaison avec les autres](##others-comparison)
* [Évolution du sentiment](#sentiment-trend)
* [Informations sur les données](#data-insights)

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue.Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord.Vous pouvez personnaliser les éléments suivants :

* **Période** pour sélectionner la période pour les données affichées.Par exemple, les quatre dernières semaines.Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Catégorie** pour filtrer les résultats affichés par catégories prédéfinies ou catégories personnalisées.
* **Rubrique** pour filtrer par rubrique pour analyser les thèmes de contenu et les domaines pour lesquels votre marque apparaît dans les réponses de l’IA.
* **Plateforme** afin de choisir le moteur d’IA à analyser.LLM Optimizer prend actuellement en charge ChatGPT, Google AI Overviews, Google AI Mode, Microsoft Co-pilot, Google Gemini, et Perplexity.
* **Origine des prompts** pour sélectionner l’origine des prompts.L’origine peut être saisie par l’utilisateur, l’utilisatrice ou générée par l’IA.
* **Branding de prompt** pour filtrer les résultats par prompt de marque ou prompt sans marque.
* **Région** pour filtrer les résultats par zone géographique.Toutes les régions ne seront pas disponibles au lancement.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Métriques générales {#overview-metrics}

Le tableau de bord met en évidence trois mesures très importantes en haut de la page : score de visibilité, mentions et citations.Plus le nombre de ces méesures est faible, plus votre marque est mal perçue et vous devez agir pour améliorer sa présence.Vous trouverez ci-dessous une brève description de chaque mesure et de ce qu’elle représente.

![Mesures générales](/help/dashboards/assets/overview-metrics.png)

### Score de visibilité {#visibility-score}

Le score de visibilité se compose de plusieurs facteurs tels que : mentions, citations, sentiment et rang.Chaque facteur est associé à un certain « poids » qui s’ajoute au score final.

### Mentions de marque {#mentions}

Cette mesure représente le nombre total de fois où votre marque ou vos catégories ont été mentionnées dans les prompts d’IA échantillonnés.Par exemple, si vous disposez de la marque « Café B », avec les catégories « Machines » et « Accessoires », cette mesure comptabilise le nombre total de fois qu’elles apparaissent dans les réponses de l’IA échantillonnées.

### Citations {#citations}

Cette mesure représente le nombre de fois où votre site a été référencé en tant que source.

Les indicateurs de tendance pour chaque mesure clé montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

## Comparaison avec les autres {#others-comparison}

Dans la section de comparaison avec les autres marques, vous pouvez sélectionner jusqu’à cinq autres marques et comparer leurs mentions et citations par rapport à votre marque.Vous pouvez ainsi afficher et comparer vos performances par rapport à celles d’autres marques.

![Comparaison avec les autres](/help/dashboards/assets/other-comparison.png)

La sélection des autres marques s’effectue dans la liste déroulante et les graphiques sont mis à jour lorsque vous cliquez sur **Appliquer les filtres**.Les graphiques affichent côte à côte les mentions de la marque hebdomadaires et les références hebdomadaires à la marque.Vous pouvez également placer le pointeur de la souris sur le graphique pour voir l’évolution des données sur l’ensemble de la période hebdomadaire.

## Analyse de l&#39;évolution du sentiment {#sentiment-trend}

Dans la section analyse de l&#39;évolution du sentiment, vous pouvez suivre la manière dont votre marque est perçue dans les réponses échantillonnées de l’IA.La mesure de l&#39;évolution du sentiment peut être positive, neutre ou négative.Par exemple, elle peut être positive si les réponses mettent en évidence la qualité du produit, ou négative si elles mentionnent un service de mauvaise qualité.Le graphique des tendances montre les changements dans la perception de la marque d’une semaine à l’autre.Cette section n’est renseignée qu’une fois votre marque mentionnée.

![Évolution du sentiment](/help/dashboards/assets/sentiment-trend.png)

## Données et part de voix {#data-insights}

Pour résumer, dans le tableau de bord se trouvent deux tableaux importants : Données et Part de voix.Les informations présentées dans ces tableaux vous aideront à déterminer les points forts de votre marque et les éléments qui nécessitent une optimisation.

En utilisant le tableau **Données**, vous pouvez explorer les rubriques et les questions des utilisateurs et des utilisatrices pour évaluer et optimiser l’impact du contenu.Les résultats sont détaillés par rubrique et par prompt.Le tableau **Part de voix**, quant à lui, compare la voix de votre marque à celle des autres marques dans les différentes rubriques et vous aide à identifier les lacunes et à classer par priorité les rubriques futures.

![Données](/help/dashboards/assets/data-insights.png)

Les deux tableaux comportent un champ de recherche pour un accès rapide aux rubriques et vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**.Vous pouvez également utiliser l’option **Exporter** pour télécharger le fichier CSV du tableau et partager les informations avec votre équipe ou inclure le tableau dans les rapports destinés aux cadres.

Cliquez sur les onglets ci-dessous pour obtenir plus d’informations sur chaque tableau et sur les mesures associées.

>[!BEGINTABS]

>[!TAB Données]

Le tableau Données vous permet d’explorer les rubriques, ainsi que les prompts des utilisateurs et des utilisatrices, pour évaluer et optimiser l’impact du contenu.Il affiche les mesures suivantes :

* **Rubrique** - La catégorie de rubrique représente les mots-clés d’optimisation pour les moteurs de recherche et les questions des utilisateurs et des utilisatrices concernant votre marque.Vous pouvez cliquer pour développer chaque rubrique et voir les prompts individuels analysés pour déterminer la présence de la marque.Chaque rubrique comporte un bouton **Détails** qui s’affiche lorsque vous placez le pointeur de la souris dessus.Cliquez sur le bouton pour afficher une fenêtre séparée qui inclut des détails supplémentaires.
* **Zone géographique** - Affiche l’emplacement géographique des prompts.
* **Popularité** - La catégorie de popularité représente le volume de recherche pour cette rubrique par rapport à toutes les autres rubriques de l’analyse.La valeur peut être Élevée, Moyenne ou Basse.
* **Score de visibilité** - Le score de visibilité de cette rubrique.Il reflète des facteurs pondérés tels que les mentions, les références, le sentiment et le classement.
* **Mentions** - Nombre de fois où votre marque a été mentionnée dans les réponses de l’IA pour cette rubrique ou cette combinaison rubrique/prompt.
* **Sentiment** - Perception de la marque dans les réponses de l’IA en ce qui concerne chaque rubrique, calculée sous la forme d’une moyenne de toutes les semaines.Uniquement renseigné lorsque votre marque est mentionnée.
* **Position** - La prédominance relative de votre marque dans les réponses de l’IA, calculée sous la forme d’une moyenne de toutes les semaines.
* **Toutes les citations** - Nombre de sources uniques citées dans les réponses de l’IA pour cette rubrique ou cette combinaison rubrique/prompt (inclut les citations détenues).
* **Citations détenues** - Nombre de fois où votre marque a été citée dans les réponses de l’IA pour ce mot-clé ou cette combinaison mot-clé/question.  <!--* **Executions**-->

Vous pouvez également afficher des détails supplémentaires pour chaque rubrique en cliquant sur les icônes **Détails** situées à la fin de chaque ligne.

>[!TAB Part de voix]

Le tableau Part de voix fournit un aperçu comparatif des performances de votre marque sur des rubriques clés dans les réponses de l’IA générative.Il vous permet d’identifier les écarts de visibilité, de suivre les performances concurrentielles et de déterminer les domaines à optimiser en priorité.Il affiche les mesures suivantes :

* **Rubrique** - La rubrique analysée.
* **Popularité** - Le volume de recherche de cette rubrique par rapport à toutes les autres rubriques de votre analyse.
* **Mentions** - Le nombre de fois où votre marque a été mentionnée dans les réponses de l’IA pour cette rubrique ou cette combinaison rubrique/prompt.
* **Classement** - Le classement de la part de voix de votre marque par rapport à toutes les autres marques identifiées.
* **Part de voix** - Pourcentage du nombre total de mentions de votre marque dans les réponses générées par l’IA.
* **Top 5 des autres marques** - Les cinq marques les plus fréquemment mentionnées pour les mêmes rubriques.Les marques sont organisées en fonction de leur part de voix (de la plus élevée à la plus faible).

>[!ENDTABS]

### Utiliser le tableau des données {#using-data-insights}

Le tableau des données vous permet de passer des mesures aux actions en répartissant les performances au niveau des rubriques et des prompts.

Principales façons d’utiliser le tableau :

* Hiérarchisez les sujets à forte popularité avec une faible visibilité : privilégiez l’optimisation lorsque la demande d’audience est forte mais que votre présence de marque est faible.
* Suivez les changements de sentiment : repérez les sujets pour lesquels les mentions ont tendance à être négatives ou neutres, et coordonnez votre réponse.
* Comparez les citations aux citations détenues : identifiez les prompts où votre marque est mentionnée mais où le contenu d’une autre marque est cité, ce qui indique un écart de contenu.
* Évaluez la plage de positions : surveillez si votre marque apparaît tôt dans les réponses de l’IA (positions 1 à 3) ou plus bas (6 à 10).
