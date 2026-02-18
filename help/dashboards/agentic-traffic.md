---
title: Trafic généré par l’IA agentique
description: Découvrez comment utiliser le tableau de bord du trafic généré par l’IA agentique afin de voir comment les agents d’IA interagissent avec votre site.
feature: Agentic Traffic
source-git-commit: 26926f3ed4df3a408b74b0208f0d1eb064b97d28
workflow-type: ht
source-wordcount: '1316'
ht-degree: 100%

---


# Trafic généré par l’IA agentique {#agentic-traffic}

Le tableau de bord du trafic généré par l’IA agentique montre comment les agents d’IA (robots d’exploration et chatbots) interagissent avec votre site.Cette vue vous permet de suivre le nombre total de requêtes et les mesures générales liées aux performances.Vous pouvez également afficher la distribution du trafic sur les marchés, les catégories, les pages et les agents.Les données utilisées par ce tableau de bord proviennent des journaux CDN. Vous devez donc configurer le **transfert des journaux CDN** pour afficher les mesures.Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

![Répartition du trafic](/help/dashboards/assets/ag-main.png)

Cette page contient les éléments suivants :

* [Filtres](#filters)
* [Configuration du réseau CDN](#cdn-setup)
* [Répartition du trafic](#traffic-distribution)
* [Tendances du trafic généré par l’IA agentique](#agentic-trends)
* [Meilleures et pires performances](#top-bottom-movers)
* [Analyse des performances des URL et des agents utilisateurs](#user-url-performance)

## Transfert de journaux CDN {#cdn-setup}

Sans **transfert des journaux CDN**, le tableau de bord du trafic généré par l’IA agentique est vide.Pour afficher les interactions agentiques, vous devez configurer le **transfert des journaux CDN**.Lors de la première connexion, un message s’affiche, comme illustré dans l’image ci-dessous.

![Configuration du réseau CDN](/help/dashboards/assets/ag-log-forward1.png)

Sélectionnez **Accéder à la configuration** et vous accéderez automatiquement à l’onglet **Configuration du réseau CDN** du tableau de bord [Configuration cliente](/help/dashboards/customer-configuration.md).

![Intégrer la configuration CDN](/help/dashboards/assets/ag-log-forward2.png)

Sur cet onglet, sélectionnez **Intégrer le réseau CDN**.La fenêtre du fournisseur de réseau CDN s’affiche.

<!-- [CDN Provider](/help/dashboards/assets/ag-log-forward3.png)-->Dans la fenêtre **Fournisseur de réseau CDN intégré** :

1. Sélectionnez votre fournisseur de réseau CDN (par exemple, Akamai, Fastly géré par Adobe, Fastly, AWS Cloudfront, Azure CDN, Cloudflare ou autre).
2. Cliquez sur **Intégration** pour activer le transfert des journaux.

Si vous sélectionnez **Autre**, vous devrez contacter llmo-now@adobe.com pour obtenir de l’aide.

Une fois activés, les journaux sont ingérés et le tableau de bord est renseigné avec des mesures telles que le nombre total d’interactions de l’agent, le taux de succès, les accès par marché, l’analyse des agents utilisateurs et les performances au niveau de l’URL.

LLM Optimizer traite un sous-ensemble de champs des journaux du réseau CDN.Bien que les noms des champs de journaux bruts varient selon le fournisseur de réseau CDN, ils sont normalisés et présentés comme suit :

* URL (chemin uniquement)
* Agent utilisateur
* Code d’état
* En-tête du référent
* En-tête de l’hôte
* Time to first byte (TTFB)
* Méthode de requête
* Date et heure
* Type de contenu

Ces champs normalisés sont exposés via la vue agentique.Sur le tableau de bord [Trafic de recommandation](/help/dashboards/referral-traffic.md), les journaux du réseau CDN sont utilisés pour afficher les mesures d’accès à la page.Aucune information d’identification personnelle (PII) n’est traitée ou stockée à quelque étape que ce soit de l’ingestion des journaux du réseau CDN ou de la gestion des données ultérieure.

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue.Les filtres que vous choisissez affecteront **toutes** les sections présentes dans le tableau de bord.Vous pouvez personnaliser les éléments suivants :

* **Période** : sélectionnez la période pour les données affichées.Par exemple, les quatre dernières semaines.Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Catégorie** : filtrez les résultats affichés par catégories prédéfinies ou par catégories personnalisées.
* **Plateforme** : choisissez le moteur d’IA à analyser.
* **Type d’agent** : filtrez selon le type d’agent d’IA qui a interagi avec votre site.Vous pouvez filtrer les robots d’indexation, les chatbots, ou tous les agents.
* **Taux de succès** : filtrez selon la qualité de l’interaction (élevée, moyenne ou faible).Cette mesure représente le pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies (codes d’état 2xx) et les redirections (codes d’état 3xx).
* **Type de contenu** : affichez l’interaction agentique pour différents types de contenu, tels qu’HTML, PDF, etc.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Répartition du trafic {#traffic-distribution}

La vue Répartition du trafic montre comment le trafic agentique est réparti sur les marchés, les catégories et les types de page.Cette vue vous permet donc de déterminer les zones géographiques, les zones de produits ou les formats de contenu auxquels les agents IA accèdent le plus souvent lors de leur interaction avec votre site.

![Répartition du trafic](/help/dashboards/assets/ag-main.png)

En haut de la page se trouvent trois mesures clés que vous devez connaître :

* **Interactions agentiques** : cette mesure représente le nombre total de requêtes effectuées par des agents IA vers votre site web.Elle inclut tout le trafic provenant des moteurs de recherche, des chatbots et du trafic non humain.
* **Taux de succès** : cette mesure représente le pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies et les redirections.
* **TTFB moyen** : mesure le temps nécessaire pour que le premier octet de données soit reçu à partir du serveur.La valeur moyenne est pondérée en fonction du nombre de requêtes renvoyant chaque code et exclut les requêtes qui ont donné lieu à des réponses 5xx.Des valeurs faibles indiquent des temps de réponse du serveur plus rapides.

Les indicateurs de tendance pour chaque mesure clé montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

## Tendances du trafic généré par l’IA agentique {#agentic-trends}

Utilisez le graphique Tendances du trafic généré par l’IA agentique pour effectuer le suivi des totaux hebdomadaires des accès réussis, échoués et généraux.Ainsi, vous pouvez surveiller les modifications de l’activité et des performances des agents au fil du temps.Vous pouvez également placer le pointeur de la souris sur le graphique pour voir l’évolution des données sur l’ensemble de la période hebdomadaire.

![Tendances du trafic généré par l’IA agentique](/help/dashboards/assets/ag-trends.png)

## Meilleures et pires performances {#top-bottom-movers}

La vue Meilleures et pires performances met en évidence les URL présentant les plus grands changements de trafic généré par l’IA agentique d’une semaine à l’autre, à savoir les visites ou les accès provenant des systèmes d’IA qui accèdent à votre contenu.**La section Meilleures performances** affiche les pages qui gagnent en visibilité ou en engagement, tandis que la section **Pires performances** révèle les URL qui connaissent les baisses les plus importantes.Cela vous permet d’identifier rapidement le contenu dont les tendances sont à la hausse, celui qui peut nécessiter une attention particulière et les emplacements où les modèles de découverte basés sur l’IA changent.

![Meilleures et pires performances](/help/dashboards/assets/movers.png)

## Analyse des performances des URL et des agents utilisateurs {#user-url-performance}

Les vues Analyse des agents utilisateurs et Analyse des performances des URL fournissent des répartitions de données supplémentaires sur la manière dont les robots d’indexation et les chatbots interagissent avec votre site.Cliquez sur les onglets ci-dessous pour obtenir des descriptions détaillées.

![Analyse des agents utilisateurs et analyse des performances des URL](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB Analyse des agents utilisateurs]

Le tableau Analyse des agents utilisateurs fournit une répartition du trafic par type de page et par type d’agent (par exemple, robots d’indexation ou chatbots).Il permet de savoir facilement quels agents IA explorent quelles parties de votre site.Il contient les catégories suivantes :

* **Type de page** : le type de page.
* **Type d’agent** : l’agent IA qui explore la page, soit un robot d’indexation, soit un chatbot.
* **Accès** : nombre total de requêtes effectuées par les agents IA pour ce type de page spécifique.

Vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**.

>[!TAB Analyse des performances des URL]

Le tableau Analyse des performances des URL affiche une vue détaillée des URL individuelles.Il inclut les accès, les agents uniques, l’agent principal, les taux de succès et les catégories.Vous pouvez ainsi identifier les pages à forte valeur ajoutée, détecter les lacunes en matière d’exploration et optimiser le contenu pour les moteurs d’IA.Les URL sont classées par volume de trafic.Le tableau contient les catégories suivantes :

* **URL** : URL examinée.
* **Total d’accès** : nombre total de demandes effectuées par des agents d’IA sur cette URL.
* **Agents uniques** : nombre d’agents d’IA différents ayant accédé à l’URL.
* **Agent le plus performant** : agent d’IA qui a généré le plus de trafic vers l’URL.
* **Type d’agent le plus performant** : type de l’agent d’IA qui a généré le plus de trafic vers cette URL.
* **Taux de succès** : pourcentage de requêtes HTTP réussies, y compris les réponses directes réussies et les redirections.
* **Catégorie** : catégorie qui correspond le mieux au contenu de votre page.
* **TTFB moyen (ms)** : temps moyen jusqu’au premier octet en millisecondes. Mesure le temps nécessaire pour que le premier octet de données soit reçu du serveur.La valeur moyenne est pondérée en fonction du nombre de requêtes renvoyant chaque code et exclut les requêtes qui ont donné lieu à des réponses 5xx.Des valeurs faibles indiquent des temps de réponse du serveur plus rapides.
* **Codes de réponse** : les codes d’état HTTP observés pour l’URL.

Le tableau Performances des URL comporte un champ de recherche pour un accès rapide aux URL et vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**.Vous pouvez également afficher des détails supplémentaires pour chaque URL en cliquant sur l’icône **Détails** à la fin de chaque ligne.

![Détails de l’URL](/help/dashboards/assets/details.png)

La vue Détails de l’URL offre une compréhension holistique des performances d’une page, indiquant la fréquence à laquelle elle est citée, le sentiment des réponses de l’IA où elle est mentionnée, les sujets et les prompts dans lesquels elle apparaît et les tendances du trafic généré par l’IA agentique et du trafic de recommandation au fil du temps.

>[!ENDTABS]

Sur les deux tableaux, vous pouvez utiliser l’option **Exporter** pour télécharger le tableau au format `.csv` et partager les informations avec votre équipe ou inclure les tableaux dans les rapports à la direction.
