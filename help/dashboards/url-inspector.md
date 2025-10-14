---
title: Inspecteur d’URL
description: Découvrez comment utiliser l’Inspecteur d’URL pour analyser les performances de pages spécifiques de votre domaine dans les recherches par IA.
feature: URL Inspector
source-git-commit: c6e37395362262eb5fe8366473e76086e36d77e9
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# Inspecteur d’URL

L’Inspecteur d’URL vous permet d’analyser les performances de pages spécifiques de votre domaine dans les recherches par IA. Il combine la visibilité, le trafic des agents et les données de référence au niveau de l’URL pour vous donner une vue granulaire des URL citées et de leur fréquence d’apparition dans les réponses.

![&#x200B; Inspecteur d’URL &#x200B;](/help/dashboards/assets/url-insp.png)

## Filtres

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** - Sélectionnez la période pour les données affichées. Par exemple, les 4 dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Catégorie** - Filtrez les résultats affichés par catégories.
* **Platform** - Choisissez le moteur d’IA à analyser.
* **Type de contenu de page** - Filtrez par type de contenu.
* **Région** - Filtrez les résultats par zone géographique. Toutes les régions ne seront pas disponibles au lancement.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Mesures de vue d’ensemble

L’Inspecteur d’URL fournit plusieurs mesures d’aperçu afin que vous puissiez évaluer rapidement les performances de vos pages dans les recherches par IA. Les mesures suivantes sont fournies :

* **Invites uniques avec citations détenues** - Nombre total d’invites d’IA uniques avec citations détenues.
* **Nombre total d’invites uniques** - Nombre total d’invites uniques de l’IA.
* **URL citées uniques** - Nombre d’URL détenues uniques qui ont été citées.
* **Nombre total de fois citées** - Nombre total de fois où une URL détenue a été citée dans les réponses générées par l’IA.
<!-- * **Total agentic hits** - The total number of hits from AI agents on your URLs.
* **Referral hits from LLMs** - The total number of hits directed from AI-generated answers to your URLs.-->

Les indicateurs de tendance pour chaque mesure d’aperçu montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

## Les URL citées

La vue des URL citées répertorie toutes les URL de votre marque qui ont été citées dans les réponses générées par l’IA, avec des mesures annexes. Le tableau de données comporte également un champ de recherche pour un accès rapide à des URL spécifiques. Vous pouvez également utiliser l’option **Exporter** pour télécharger le fichier csv de la table et partager les informations avec votre équipe ou inclure la table dans les rapports d’exécution.

![URL citées](/help/dashboards/assets/cited-urls.png)

Les mesures suivantes sont fournies :

* **URL** - URL analysée.
* **Nombre de citations** - Nombre de fois où l’URL a été citée dans des réponses générées par l’IA.
* **Invites citées en** - Nombre d’invites d’IA uniques ayant cité l’URL.
* **Catégories** - Catégories de produits ou rubriques associées à l’URL.
* **Régions** - Région géographique dans laquelle l’URL a été citée.
* **Accès aux agents** - Nombre total d’accès provenant des agents AI sur les URL.
* **Accès aux références** - Nombre d’accès dirigés depuis les réponses générées par l’IA vers les URL.

## Tendance des URL en concurrence pour les citations

Les URL de tendance en concurrence pour la vue des citations mettent en évidence les URL externes qui sont actuellement citées dans les réponses pertinentes pour votre marque, mesurant qui gagne des citations dans votre espace perso. Le tableau de données comporte un champ de recherche pour un accès rapide à des URL spécifiques. Vous pouvez également utiliser l’option **Exporter** pour télécharger le fichier csv de la table et partager les informations avec votre équipe ou inclure la table dans les rapports d’exécution.

![URL de tendance en concurrence pour les citations](/help/dashboards/assets/trend-url.png)

Les mesures suivantes sont fournies :

* **URL** - URL analysée
* **Type de contenu** - Type de contenu (détenu, social, gagné, autre).
* **Nombre de citations** - Nombre de fois où l’URL a été citée dans des réponses générées par l’IA.
* **Invites citées en** - Nombre d’invites d’IA uniques ayant cité l’URL.
* **Catégories** - Catégories de produits ou rubriques associées à l’URL.
* **Régions** - Région géographique dans laquelle l’URL a été citée.

### Fenêtre Détails

Pour les vues citées et de tendance, les URL comportent un bouton **Détails** lorsque vous placez le pointeur de la souris sur une URL spécifique. Cliquez sur le bouton pour afficher une fenêtre distincte avec des détails supplémentaires. La fenêtre de détails indique la fréquence de citation de l’URL, le sentiment des réponses de l’IA lorsqu’elle est mentionnée, les sujets et les invites dans lesquels elle apparaît et les tendances du trafic d’agent et de référence au fil du temps (pour les URL détenues).

![Fenêtre Détails](/help/dashboards/assets/details-url.png)
