---
title: Présence de la marque
description: Découvrez comment utiliser le tableau de bord des Présences des marques pour comprendre comment votre marque est perçue au niveau des réponses générées par l’IA.
feature: Brand Presence
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 1%

---


# Présence de la marque {#brand-presence}

Le tableau de bord de la Présence des marques fournit un aperçu détaillé de la manière dont votre marque est perçue au niveau des réponses générées par l’IA. Il indique où, à quelle fréquence et dans quel contexte votre marque est mentionnée. Vous pouvez utiliser le tableau de bord pour mesurer la visibilité, suivre les citations et explorer les évolutions du sentiment. Le tableau de bord est divisé en plusieurs sections, chacune fournissant des informations différentes. Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

![Présence des marques &#x200B;](/help/dashboards/assets/brand-main.png)

Cette page présente les éléments suivants :

* [Filtres](#filters)
* [Mesures de vue d’ensemble](##key-metrics)
* [Comparaison des autres](##others-comparison)
* [Tendance du sentiment](#sentiment-trend)
* [Informations sur les données](#data-insights)

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** - Sélectionnez la période pour les données affichées. Par exemple, les 4 dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Catégorie** - Filtrez les résultats affichés par catégories prédéfinies ou catégories personnalisées.
* **Sujet** - Filtrez par sujet afin d’analyser les thèmes du contenu et les domaines où votre marque apparaît dans les réponses de l’IA.
* **Platform** - Choisissez le moteur d’IA à analyser. LLM Optimizer prend actuellement en charge le ChatGPT, les présentations de l’IA Google, le mode Google AI, le copilote Microsoft, Google Gemini et Perplexity.
* **Origine des invites** - Sélectionnez l’origine des invites. L’origine peut être saisie par l’utilisateur ou générée par l’IA.
* **Branding de prompt** - Filtrez les résultats par invites de marque ou invites sans marque.
* **Région** - Filtrez les résultats par zone géographique. Toutes les régions ne seront pas disponibles au lancement.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Mesures de vue d’ensemble {#overview-metrics}

Le tableau de bord met en évidence trois mesures très importantes en haut de la page : score de visibilité, mentions et citations. Plus le nombre de ces mesures est faible, plus votre marque est mal perçue et vous devez agir pour améliorer votre présence des marques. Vous trouverez ci-dessous une brève description de chaque mesure et de ce qu’elle représente.

![Mesures d’aperçu](/help/dashboards/assets/overview-metrics.png)

### Score de visibilité {#visibility-score}

Le score de visibilité se compose de facteurs tels que : mentions, citations, sentiment et rang. Chaque facteur est associé à un certain « poids » qui s’ajoute au score final.

### Mentions de marque {#mentions}

Cette mesure représente le nombre total de fois où votre marque ou vos catégories ont été mentionnées dans les invites d’IA échantillonnées. Par exemple, si vous disposez de la marque « Café B », avec les catégories « Machines » et « Accessoires », cette mesure comptabilise le nombre total de fois qu’elles apparaissent dans les réponses de l’IA échantillonnée.

### Citations {#citations}

Cette mesure représente le nombre de fois où votre site a été référencé en tant que source.

Les indicateurs de tendance pour chaque mesure clé montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

## Comparaison des autres {#others-comparison}

Dans la section de comparaison des autres marques, vous pouvez sélectionner jusqu’à cinq autres marques et comparer leurs mentions et citations par rapport à votre marque. Vous pouvez ainsi afficher et comparer vos performances par rapport à celles d’autres marques.

![Comparaison d’autres utilisateurs](/help/dashboards/assets/other-comparison.png)

Les autres marques sont sélectionnées dans la liste déroulante et les graphiques sont mis à jour lorsque vous cliquez sur **Appliquer des filtres**. Les graphiques affichent côte à côte les mentions de marque hebdomadaires et les citations hebdomadaires de la marque. Vous pouvez également placer le pointeur de la souris sur le graphique pour voir l’évolution des données sur la période hebdomadaire.

## Analyse des tendances des sentiments {#sentiment-trend}

Dans la section analyse de l&#39;évolution du sentiment , vous pouvez suivre la manière dont votre marque est perçue dans les réponses de l’IA échantillonnée. La mesure d’évolution du sentiment peut être positive, neutre ou négative. Par exemple, il peut être positif si les réponses mettent en évidence la qualité du produit ou négatif si elles mentionnent un mauvais service. Le graphique de tendance montre les changements dans la perception de la marque d&#39;une semaine à l&#39;autre. Cette section n’est renseignée qu’une fois votre marque mentionnée.

![Évolution du sentiment &#x200B;](/help/dashboards/assets/sentiment-trend.png)

## Informations sur les données et Part de voix {#data-insights}

En arrondissant le tableau de bord, nous disposons de deux tableaux importants : informations sur les données et part de voix. Les informations présentées dans ces tableaux vous aideront à déterminer où votre marque est forte et où une optimisation est nécessaire.

Grâce au tableau **informations sur les données**, vous pouvez explorer les rubriques et répondre aux questions des utilisateurs et utilisatrices afin d’évaluer et d’optimiser l’impact du contenu. Les résultats sont détaillés par rubriques et invites. Dans le même temps, le tableau **part de voix** compare la voix de votre marque à celle d&#39;autres marques sur plusieurs sujets et vous aide à identifier les lacunes et à classer par priorité les sujets futurs.

![Data Insights](/help/dashboards/assets/data-insights.png)

Les deux tableaux comportent un champ de recherche pour un accès rapide aux rubriques et vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**. Vous pouvez également utiliser l’option **Exporter** pour télécharger le fichier csv de la table et partager les informations avec votre équipe ou inclure les tables dans les rapports d’exécution.

Cliquez sur les onglets ci-dessous pour obtenir plus d’informations sur chaque tableau et les mesures associées.

>[!BEGINTABS]

>[!TAB Data Insights]

Le tableau des informations sur les données vous permet d’explorer les rubriques et les invites des utilisateurs pour évaluer et optimiser l’impact du contenu. Elle affiche les mesures suivantes :

* **Rubrique** - La catégorie de rubrique représente les mots-clés SEO et les questions des utilisateurs liées à votre marque. Vous pouvez cliquer pour développer chaque rubrique et voir les invites individuelles analysées pour la présence des marques. Chaque rubrique comporte un bouton **Détails** lorsque vous placez le pointeur de la souris dessus. Cliquez sur le bouton pour afficher une fenêtre distincte avec des détails supplémentaires.
* **Region** : affiche la région des invites.
* **Popularité** - La catégorie de popularité représente le volume de recherche de cette rubrique par rapport à toutes les autres rubriques de l’analyse. La valeur peut être Élevée, Medium ou Faible.
* **Score de visibilité** - score de visibilité de cette rubrique. Il reflète des facteurs pondérés tels que les mentions, les citations, le sentiment et le rang.
* **Mentions** - Nombre de fois où votre marque a été mentionnée dans les réponses de l’IA pour cette rubrique ou cette combinaison rubrique/invite.
* **Sentiment** - La perception de la marque dans les réponses de l’IA en ce qui concerne chaque sujet, calculée en moyenne sur toutes les semaines. Uniquement renseigné lorsque votre marque est réellement mentionnée.
* **Position** - La prédominance relative de votre marque dans les réponses de l’IA, calculée sous la forme d’une moyenne sur toutes les semaines.
* **Toutes les citations** - Nombre de sources uniques citées dans les réponses de l’IA pour cette rubrique ou cette combinaison rubrique/invite (y compris les citations de propriété).
* **Citations de propriété** - Nombre de fois où votre marque a été citée dans les réponses de l&#39;IA pour ce mot-clé ou cette combinaison mot-clé/question.
  <!--* **Executions**-->

Vous pouvez également afficher des détails supplémentaires pour chaque rubrique en cliquant sur l’icône **Détails** à la fin de chaque ligne.

>[!TAB Part de voix ]

Le tableau des Parts de voix fournit un aperçu comparatif des performances de votre marque sur plusieurs sujets clés des réponses génératives de l’IA. Il vous permet d’identifier les écarts de visibilité, de suivre les performances concurrentielles et de hiérarchiser les domaines à optimiser. Elle affiche les mesures suivantes :

* **Rubrique** - Rubrique analysée.
* **Popularité** - Volume de recherche de la rubrique par rapport à toutes les autres rubriques de votre analyse.
* **Mentions** - Nombre de fois où votre marque a été mentionnée dans les réponses de l’IA pour la rubrique ou la combinaison rubrique/invite.
* **Classement** - Classement de la Part de voix de votre marque par rapport à toutes les autres marques identifiées.
* **Part de voix** - Pourcentage du nombre total de mentions de votre marque dans les réponses générées par l’IA.
* **Top 5 autres** - Les cinq marques les plus fréquemment mentionnées pour les mêmes sujets. Les marques sont organisées selon leur Part de voix (du plus haut au plus bas).

>[!ENDTABS]

### Utilisation du tableau Data Insights {#using-data-insights}

Le tableau des informations sur les données vous permet de passer des mesures aux actions en répartissant les performances au niveau de la rubrique et de l’invite.

Principales façons d’utiliser le tableau :

* Hiérarchisez les sujets à forte popularité avec une faible visibilité : privilégiez l’optimisation lorsque la demande d’audience est forte mais que votre présence des marques est faible.
* Suivre les changements de sentiment : repérez les sujets pour lesquels les mentions ont tendance à être négatives ou neutres, et coordonnez votre réponse.
* Comparer les citations aux citations de propriété - Identifiez les invites où votre marque est mentionnée mais où le contenu d&#39;une autre marque est cité, signalant un écart de contenu.
* Évaluer la plage de positions - surveiller si votre marque apparaît tôt dans les réponses de l&#39;IA (positions 1 à 3) ou plus bas (6 à 10).
