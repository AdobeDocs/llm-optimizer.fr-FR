---
title: Inspecteur d’URL
description: Découvrez comment utiliser l’Inspecteur d’URL pour analyser les performances de pages spécifiques de votre domaine dans les recherches optimisées par l’IA.
feature: URL Inspector
source-git-commit: 625807b8905f741aa89d551483d89cca2ef91873
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 95%

---


# Inspecteur d’URL

L’Inspecteur d’URL vous permet d’analyser les performances de pages spécifiques de votre domaine dans les recherches optimisées par l’IA. Il combine la visibilité, le trafic généré par l’IA agentique et les données de recommandation au niveau de l’URL pour vous donner une vue granulaire des URL citées et de leur fréquence d’apparition dans les réponses.

![Inspecteur d’URL](/help/dashboards/assets/url-insp.png)

Si vous utilisez l’[expérience orientée marque](/help/overview/quick-start.md#brand-centric-experience), accédez à **Inspecteur d’URL** et sélectionnez le site pour lequel vous souhaitez afficher les informations.

![Inspecteur d’URL — sélecteur de site (expérience orientée marque)](/help/assets/brand-centric-experience/url-inspector-dashboard.png)

## Filtres

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez affecteront **toutes** les sections présentes dans le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** pour sélectionner la période pour les données affichées. Par exemple, les quatre dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Catégorie** : filtrez les résultats affichés par catégories.
* **Plateforme** : choisissez le moteur d’IA à analyser.
* **Type de contenu de page** : filtrez par type de contenu.
* **Région** pour filtrer les résultats par zone géographique. Toutes les régions ne seront pas disponibles au lancement.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Métriques générales

L’Inspecteur d’URL fournit plusieurs mesures générales afin que vous puissiez évaluer rapidement les performances de vos pages dans les recherches optimisées par l’IA. Les mesures suivantes sont fournies :

* **Prompts uniques avec citations détenues** : nombre total de prompts d’IA uniques avec citations détenues.
* **Nombre de prompts uniques** : nombre total de prompts d’IA uniques.
* **URL citées uniques** : nombre d’URL détenues uniques qui ont été citées.
* **Nombre total de citations** : nombre total de citations d’une URL détenue dans les réponses générées par l’IA.
* **Total des accès agentiques** : nombre total d’accès à partir de vos URL provenant d’agents IA.
* **Accès de recommandation provenant des LLM** : nombre total d’accès allant des réponses générées par l’IA vers votre URL.

Les indicateurs de tendance de chaque mesure générale montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

## Vos URL citées

La vue des URL citées répertorie toutes les URL de votre marque qui ont été citées dans les réponses générées par l’IA, avec des mesures annexes. Les deux tableaux comportent un champ de recherche pour un accès rapide aux rubriques et vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**. Vous pouvez également utiliser l’option **Exporter** pour télécharger le fichier CSV du tableau et partager les informations avec votre équipe ou inclure le tableau dans les rapports à la direction.

![URL citées](/help/dashboards/assets/cited-urls.png)

Les mesures suivantes sont fournies :

* **URL** : URL analysée.
* **Nombre de citations** : nombre de fois où l’URL a été citée dans des réponses générées par l’IA.
* **Prompts avec citation** : nombre de prompts d’IA uniques ayant cité l’URL.
* **Catégories** : catégories de produits ou rubriques associées à cette URL.
* **Régions** : régions géographiques où l’URL a été citée.
* **Accès agentique** : nombre total d’accès des agents IA aux URL.
* **Accès de recommandation** : nombre d’accès dirigés depuis les réponses générées par l’IA vers les URL.

## URL de tendance en concurrence pour les citations

La vue des URL de tendance en concurrence pour les citations met en évidence les URL externes qui sont actuellement citées dans les réponses pertinentes pour votre marque, mesurant qui gagne des citations dans votre domaine. Le tableau de données comporte un champ de recherche pour un accès rapide à des URL spécifiques. Vous pouvez également utiliser l’option **Exporter** pour télécharger le fichier CSV du tableau et partager les informations avec votre équipe ou inclure le tableau dans les rapports à la direction.

![URL de tendance en concurrence pour les citations](/help/dashboards/assets/trend-url.png)

Les mesures suivantes sont fournies :

* **URL** : URL analysée
* **Type de contenu** : type de contenu (détenu, social, gagné, autre).
* **Nombre de citations** : nombre de fois où l’URL a été citée dans des réponses générées par l’IA.
* **Prompts avec citation** : nombre de prompts d’IA uniques ayant cité l’URL.
* **Catégories** : catégories de produits ou rubriques associées à cette URL.
* **Régions** : régions géographiques où l’URL a été citée.

### Fenêtre des détails

Pour les vues citées et de tendance, les URL comportent un bouton **Détails** à la fin de chaque ligne. Cliquez sur le bouton pour afficher une fenêtre distincte avec des détails supplémentaires. La fenêtre des détails indique la fréquence à laquelle l’URL est citée, <!--the sentiment of AI responses where it is mentioned,--> les rubriques et les prompts dans lesquels elle apparaît et les tendances en matière de trafic généré par l’IA agentique et de trafic de recommandation au fil du temps (pour les URL détenues).

![Fenêtre des détails](/help/dashboards/assets/details-url.png)
