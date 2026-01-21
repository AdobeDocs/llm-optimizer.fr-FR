---
title: Trafic d’agent
description: Découvrez comment utiliser le tableau de bord du trafic d’agents afin de voir comment les agents d’IA interagissent avec votre site.
feature: Agentic Traffic
source-git-commit: 26926f3ed4df3a408b74b0208f0d1eb064b97d28
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---


# Trafic d’agent {#agentic-traffic}

Le tableau de bord du trafic d’agents montre comment les agents d’IA (robots d’exploration et chatbots) interagissent avec votre site. Cette vue vous permet de suivre le nombre total de requêtes et les mesures générales liées aux performances. Vous pouvez également afficher la distribution du trafic sur les marchés, les catégories, les pages et les agents. Les données utilisées par ce tableau de bord proviennent des journaux CDN. Vous devez donc configurer le **transfert des journaux CDN** pour afficher les mesures. Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

![Distribution du trafic](/help/dashboards/assets/ag-main.png)

Cette page présente les éléments suivants :

* [Filtres](#filters)
* [Configuration du réseau CDN](#cdn-setup)
* [Répartition du trafic](#traffic-distribution)
* [Tendances du trafic des agences](#agentic-trends)
* [Déplacements en haut et en bas](#top-bottom-movers)
* [Analyse des performances de l’agent utilisateur et de l’URL](#user-url-performance)

## Transfert du journal CDN {#cdn-setup}

Sans **transfert du journal CDN**, le tableau de bord du trafic agent est vide. Pour afficher les interactions génétiques, vous devez configurer le **transfert du journal CDN**.  Lors de la première connexion, un message s’affiche, comme illustré dans l’image ci-dessous.

![Configuration du réseau CDN](/help/dashboards/assets/ag-log-forward1.png)

Sélectionnez **Aller à la configuration** et vous accéderez automatiquement à l’onglet **Configuration du réseau CDN** du tableau de bord [configuration du client](/help/dashboards/customer-configuration.md).

![Configuration du réseau CDN intégrée](/help/dashboards/assets/ag-log-forward2.png)

Sur cet onglet, sélectionnez **Réseau CDN intégré**. Et la fenêtre du fournisseur de réseau CDN s’affiche.

<!-- [CDN Provider](/help/dashboards/assets/ag-log-forward3.png)-->
Dans la fenêtre **Fournisseur de réseau CDN intégré** :

1. Sélectionnez votre fournisseur de réseau CDN (par exemple, Akamai, Fastly géré par Adobe, Fastly, AWS Cloudfront, Azure CDN, Cloudflare ou autre).
2. Cliquez sur **Intégration** pour activer le transfert du journal.

Si vous sélectionnez **Autre**, vous devrez contacter llmo-now@adobe.com pour obtenir de l’aide.

Une fois activés, les journaux sont ingérés et le tableau de bord est renseigné avec des mesures telles que le nombre total d’interactions de l’agent, le taux de succès, les accès par marché, l’analyse des agents utilisateur et les performances au niveau de l’URL.

LLM Optimizer traite un sous-ensemble de champs des journaux du réseau CDN. Bien que les noms des champs de journal bruts varient selon le fournisseur de réseau CDN, ils sont normalisés et présentés comme suit :

* URL (chemin uniquement)
* Agent utilisateur
* Code de statut
* En-tête du référent
* En-tête de l’hôte
* Temps jusqu’au premier octet (TTFB)
* Méthode de requête
* Date et heure
* Type de contenu

Ces champs normalisés sont exposés via la vue agentique. Sur le tableau de bord [Trafic de référence](/help/dashboards/referral-traffic.md), les journaux CDN sont utilisés pour afficher les mesures d’accès à la page. Aucune information d’identification personnelle (PII) n’est traitée ou stockée à quelque étape que ce soit de l’ingestion des journaux du réseau CDN ou de la gestion des données ultérieure.

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** - Sélectionnez la période pour les données affichées. Par exemple, les 4 dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Catégorie** - Filtrez les résultats affichés par catégories prédéfinies ou catégories personnalisées.
* **Platform** - Choisissez le moteur d’IA à analyser.
* **Type d’agent** - Filtrez par le type d’agent d’IA qui a interagi avec votre site. Vous pouvez filtrer entre les robots d’exploration, les chatbots ou tous les agents.
* **Taux de succès** - Filtrez par la qualité de l’interaction (élevée, moyenne ou faible). Cette mesure représente le pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies (codes d’état 2xx) et les redirections (codes d’état 3xx).
* **Type de contenu** - Affichez l’interaction agent pour différents types de contenu, tels qu’HTML, PDF, etc.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Répartition du trafic {#traffic-distribution}

La vue Distribution du trafic montre comment le trafic de l’agent est réparti sur les marchés, les catégories et les types de page. Cette vue vous permet donc de déterminer les zones géographiques, les zones de produits ou les formats de contenu auxquels les agents d’IA accèdent le plus souvent lors de leur interaction avec votre site.

![Distribution du trafic](/help/dashboards/assets/ag-main.png)

En haut de la page, il y a trois mesures clés que vous devez connaître :

* **Interactions avec les agents** - Cette mesure représente le nombre total de requêtes effectuées par des agents AI sur votre site web. Cela inclut tout le trafic provenant des moteurs de recherche, des chatbots et d’autres trafics non humains.
* **Taux de succès** - Cette mesure représente le pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies et les redirections.
* **TTFB moyen** - Le temps jusqu’au premier octet (TTFB) mesure le temps nécessaire pour que le premier octet de données soit reçu du serveur. La valeur moyenne est pondérée en fonction du nombre de requêtes renvoyant chaque code et exclut les requêtes qui ont donné lieu à des réponses 5xx. Des valeurs faibles indiquent des temps de réponse du serveur plus rapides.

Les indicateurs de tendance pour chaque mesure clé montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

## Tendances du trafic des agences {#agentic-trends}

Utilisez le graphique Tendances du trafic d’agent pour effectuer le suivi des totaux hebdomadaires des accès réussis, en échec et globaux. Ainsi, vous pouvez surveiller les modifications de l’activité et des performances des agents au fil du temps. Vous pouvez également placer le pointeur de la souris sur le graphique pour voir l’évolution des données sur la période hebdomadaire.

![Tendances du trafic des agences](/help/dashboards/assets/ag-trends.png)

## Déplacements en haut et en bas {#top-bottom-movers}

La vue des déménageurs en haut et en bas met en évidence les URL présentant les plus grands changements de trafic d’agent d’une semaine à l’autre, à savoir les visites ou les accès des systèmes d’IA accédant à votre contenu. Le tableau **Principaux déménageurs** montre les pages qui gagnent en visibilité ou en engagement, tandis que le tableau **Principaux déménageurs** révèle les URL qui connaissent les déclins les plus importants. Cela vous permet d’identifier rapidement le contenu à la hausse, celui qui peut nécessiter une attention particulière et les endroits où les modèles de découverte pilotés par l’IA se modifient.

![Déplacements haut et bas](/help/dashboards/assets/movers.png)

## Analyse des performances de l’agent utilisateur et de l’URL {#user-url-performance}

Les vues Agent utilisateur et Analyse des performances des URL fournissent d’autres répartitions de données sur la manière dont les robots d’exploration et les chatbots interagissent avec votre site. Cliquez sur les onglets ci-dessous pour obtenir une description détaillée.

![Analyse des performances de l’agent utilisateur et des URL](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB User Agent Analysis]

Le tableau Analyse de l’agent utilisateur fournit une répartition du trafic par type de page et type d’agent (par exemple, robots d’exploration ou chatbots). De cette manière, il est facile de comprendre quels agents d’IA analysent quelles parties de votre site. Il contient les catégories suivantes :

* **Type de page** - Type de page.
* **Type d’agent** - L’agent d’IA qui analyse la page, soit un robot d’exploration, soit un chatbot.
* **Accès** - Nombre total de requêtes effectuées par les agents d’IA pour ce type de page spécifique.

Vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**.

>[!TAB Analyse des performances des URL]

Le tableau Analyse des performances des URL affiche une vue détaillée des URL individuelles. Cela inclut les accès, les agents uniques, les principaux agents, les taux de succès et les catégories. Vous pouvez ainsi identifier les pages à forte valeur ajoutée, détecter les écarts d’analyse et optimiser le contenu pour les moteurs d’IA. Les URL sont classées par volume de trafic. Le tableau contient les catégories suivantes :

* **URL** - URL examinée.
* **Nombre total d’accès** - Nombre total de requêtes effectuées par des agents AI sur l’URL.
* **Agents uniques** - Nombre d’agents AI différents ayant accédé à l’URL.
* **Agent principal** - L’agent d’IA qui a généré le plus de trafic vers l’URL.
* **Type d’agent principal** - Type de l’agent AI qui a généré le plus de trafic vers cette URL.
* **Taux de succès** - Pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies et les redirections.
* **Catégorie** - La catégorie qui correspond le mieux au contenu de votre page.
* **TTFB moyen (ms)** - Temps jusqu’au premier octet (TTFB) mesure le temps nécessaire au premier octet de données à recevoir du serveur (en millisecondes). La valeur moyenne est pondérée en fonction du nombre de requêtes renvoyant chaque code et exclut les requêtes qui ont donné lieu à des réponses 5xx. Des valeurs faibles indiquent des temps de réponse du serveur plus rapides.
* **Codes de réponse** - les codes d’état HTTP observés pour l’URL.

Le tableau Performances des URL comporte un champ de recherche pour un accès rapide aux URL et vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**. Vous pouvez également afficher des détails supplémentaires pour chaque URL en cliquant sur l’icône **Détails** à la fin de chaque ligne.

![détails de l’URL](/help/dashboards/assets/details.png)

La vue Détails de l’URL offre une compréhension holistique des performances d’une page, montrant la fréquence à laquelle elle est citée, le sentiment des réponses de l’IA où elle est mentionnée, les sujets et les invites dans lesquels elle apparaît et les tendances du trafic d’agents et de recommandations au fil du temps.

>[!ENDTABS]

Sur les deux tableaux, vous pouvez utiliser l’option **Exporter** pour télécharger le `.csv` du tableau et partager les informations avec votre équipe ou inclure les tableaux dans les rapports d’exécution.
