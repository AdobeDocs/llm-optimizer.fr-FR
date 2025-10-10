---
title: Trafic d’agent
description: Voici la présentation de l’article.
source-git-commit: f92ca3eaa81d05135c65df60267280314c6e2d6f
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 0%

---


# Trafic d’agent {#agentic-traffic}

Le tableau de bord Trafic agent vous montre comment les agents d’IA (robots d’exploration et chatbots) interagissent avec votre site. Cette vue vous permet de suivre le nombre total de requêtes et les mesures générales liées aux performances. Vous pouvez également afficher la distribution du trafic sur les marchés, les catégories, les pages et les agents. Les données utilisées par ce tableau de bord proviennent des journaux CDN. Vous devez donc configurer le **transfert des journaux CDN** pour afficher les mesures. Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

Cette page présente les éléments suivants :

* [Filtres](#filters)
* [Configuration du réseau CDN](#cdn-setup)
* [Répartition du trafic](#traffic-distribution)
* [Tendances du trafic des agences](#agentic-trends)
* [Déplacements en haut et en bas](#top-bottom-movers)
* [Analyse des performances de l’agent utilisateur et de l’URL](#user-url-performance)

## Configuration du réseau CDN {#cdn-setup}

Lors de la première connexion, le tableau de bord Trafic d’agent est vide. Pour afficher les interactions génétiques, vous devez configurer le **transfert du journal CDN**. **À déterminer, pointez vers la configuration du réseau CDN dans le démarrage rapide/l’intégration ?**

![Configuration du réseau CDN](/help/dashboards/assets/ag-log-forward.png)

1. Sélectionnez votre fournisseur de réseau CDN (par exemple, Akamai, Fastly géré par Adobe, Fastly, AWS Cloudfront, Azure CDN, Cloudflare ou autre).
2. Saisissez l’adresse e-mail principale du contact.
3. Cliquez sur **Demander l’activation** pour activer le transfert du journal.

Une fois activés, les journaux sont ingérés et le tableau de bord est renseigné avec des mesures telles que le nombre total d’interactions de l’agent, le taux de succès, les accès par marché, l’analyse des agents utilisateur et les performances au niveau de l’URL.

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** - Sélectionnez la période pour les données affichées. Par exemple, les 4 dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Catégorie** - Filtrez les résultats affichés par catégories prédéfinies. Vous pouvez également ajouter des catégories personnalisées à ce champ (**SR**-how ?).
* **Platform** - Choisissez le moteur d’IA à analyser.
* **Type d’agent** - Filtrez par le type d’agent d’IA qui a interagi avec votre site. Vous pouvez filtrer entre les robots d’exploration, les chatbots ou tous les agents.
* **Taux de succès** - Filtrez par la qualité de l’interaction (élevée, moyenne ou faible). Cette mesure représente le pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies et les redirections.
* **Type de contenu** - Filtrez par type de contenu (HTML ou txt).

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Répartition du trafic {#traffic-distribution}

La vue Distribution du trafic montre comment le trafic de l’agent est réparti sur les marchés, les catégories et les types de page. Cette vue vous permet donc de déterminer les zones géographiques, les zones de produits ou les formats de contenu auxquels les agents d’IA accèdent le plus souvent lors de leur interaction avec votre site.

![Distribution du trafic](/help/dashboards/assets/ag-main.png)

En haut de la page, il y a trois mesures clés que vous devez connaître :

* **Interactions avec les agents** - Cette mesure représente le nombre total de requêtes effectuées par des agents AI sur votre site web. Cela inclut tout le trafic provenant des moteurs de recherche, des chatbots et d’autres trafics non humains.
* **Taux de succès** - Cette mesure représente le pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies et les redirections.
* **TTFB moyen** - Le temps jusqu’au premier octet (TTFB) mesure le temps nécessaire pour que le premier octet de données soit reçu du serveur. Des valeurs faibles indiquent des temps de réponse du serveur plus rapides.

Les indicateurs de tendance pour chaque mesure clé montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

## Tendances du trafic des agences {#agentic-trends}

Utilisez le graphique Tendances du trafic d’agent pour effectuer le suivi des totaux hebdomadaires des accès réussis, en échec et globaux. Ainsi, vous pouvez surveiller les modifications de l’activité et des performances des agents au fil du temps. Vous pouvez également placer le pointeur de la souris sur le graphique pour voir l’évolution des données sur la période hebdomadaire.

![Tendances du trafic des agences](/help/dashboards/assets/ag-trends.png)

## Déplacements en haut et en bas {#top-bottom-movers}

Ces deux mesures trient les URL comme suit :

* **Principaux déménageurs** - Les URL qui connaissent la plus forte augmentation du trafic des agents de la semaine la plus ancienne à la plus récente.
* **Bottom Movers** - URL présentant la plus forte diminution du trafic des agents de la semaine la plus ancienne à la plus récente.

## Analyse des performances de l’agent utilisateur et de l’URL {#user-url-performance}

Les vues Agent utilisateur et Analyse des performances des URL fournissent d’autres répartitions de données sur la manière dont les robots d’exploration et les chatbots interagissent avec votre site. Cliquez sur les onglets ci-dessous pour obtenir une description détaillée.

![Analyse des performances de l’agent utilisateur et des URL](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB User Agent Analysis]

Le tableau Analyse de l’agent utilisateur fournit une répartition du trafic par type de page et type d’agent (par exemple, robots d’exploration ou chatbots). De cette manière, il est facile de comprendre quels agents d’IA analysent quelles parties de votre site. Il contient les catégories suivantes :

* **Type de page** - Type de page.
* **Type d’agent** - L’agent d’IA qui analyse la page, soit un robot d’exploration, soit un chatbot.
* **Accès** - Nombre total de requêtes effectuées par les agents d’IA pour ce type de page spécifique.

Vous pouvez également utiliser l’option **Exporter** pour télécharger le tableau .csv et partager l’analyse de l’agent avec votre équipe ou l’inclure dans les rapports d’exécution.

>[!TAB Analyse des performances des URL]

Le tableau Analyse des performances des URL affiche une vue détaillée des URL individuelles. Cela inclut les accès, les agents uniques, les principaux agents, les taux de succès et les catégories. Vous pouvez ainsi identifier les pages à forte valeur ajoutée, détecter les écarts d’analyse et optimiser le contenu pour les moteurs d’IA. Les URL sont classées par volume de trafic. Le tableau contient les catégories suivantes :

* **URL** - URL examinée.
* **Nombre total d’accès** - Nombre total de requêtes effectuées par des agents AI sur l’URL.
* **Agents uniques** - Nombre d’agents AI différents ayant accédé à l’URL.
* **Agent principal** - L’agent d’IA qui a généré le plus de trafic vers l’URL.
* **Type d’agent principal** - Type de l’agent AI qui a généré le plus de trafic vers cette URL.
* **Taux de succès** - Pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies et les redirections.
* **Catégorie** - La catégorie qui correspond le mieux au contenu de votre page.

Le tableau Performances des URL comporte un champ de recherche pour un accès rapide aux URL. Vous pouvez également utiliser l’option **Exporter** pour télécharger le fichier csv de la table et partager les informations avec votre équipe ou inclure la table dans les rapports d’exécution.

>[!ENDTABS]
