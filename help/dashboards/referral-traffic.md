---
title: Trafic de recommandation
description: Découvrez comment utiliser le tableau de bord du Trafic de recommandation pour voir comment les visiteurs accèdent à votre site à partir de plateformes externes, de citations d’IA et de liens de référence.
feature: Referral Traffic
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 2%

---


# Trafic de recommandation

Le trafic de recommandation montre comment les visiteurs et visiteuses accèdent à votre site à partir de plateformes externes, de citations d’IA et de liens de référence. Il suit et analyse les sources de trafic, les modèles de référence et les mesures de conversion des sites web et plateformes externes. Cela vous aidera à comprendre quelles sources, régions et pages génèrent le trafic le plus engagé. <!--Data is sourced from the CDN logs, a privacy-preserving source that does not capture personal user data.--> Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

![Page de référence](/help/dashboards/assets/referral-traffic.png)

Cette page présente les éléments suivants :

* [Configuration](#setup)
* [Filtres](#filters)
* [Performance globale de référence](#overall-performance)
* [Principales URL de recommandation](#top-referrals)
* [Détails du trafic de recommandation](#traffic-details)

## Configuration {#setup}

Lors de la première connexion, le tableau de bord du Trafic de recommandation peut apparaître vide. Pour afficher vos données, vous devez configurer le [transfert du journal CDN](/help/dashboards/customer-configuration.md#cdn-configuration) en sélectionnant **Accéder à la configuration**.

![Configuration du parrainage](/help/dashboards/assets/referral-setup1.png)

<!--- 1. Select your Source (either CDN logs or AEM Operational Telemetry).
2. Enter a primary contact email.
3. Click **Request activation** to enable data ingestion. Hiding this until confirmation from PM-->

Une fois activé, le tableau de bord sera renseigné avec les mesures de trafic de recommandation.

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** - Sélectionnez la période pour les données affichées. Par exemple, les 4 dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Platform** - Sélectionnez une source de trafic spécifique telle que Google, OpenAI ou les médias sociaux.
* **Motif de la page** - Filtrez le trafic de recommandation par motif de l’utilisateur.
* **Channel Source** - Filtrez par source du canal. Les options incluent : canaux de référence LLM, Earned, pay ou mixte.
* **Type d’appareil** - Analysez le trafic par type d’appareil du visiteur, que ce soit un ordinateur, un appareil mobile ou tous les appareils.
  **Région** - Affichez les schémas de recommandation dans différentes zones géographiques.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Performance globale de référence {#overall-performance}

Le tableau de bord met en évidence les performances globales des références en affichant des mesures clés, notamment :

* **Trafic de recommandation total** - trafic de recommandation total, toutes sources confondues.
* **Trafic de recommandation depuis les LLM** - trafic de recommandation total depuis les LLM.
* **Taux de consentement** - Pourcentage de visiteurs et visiteuses qui acceptent une invite de consentement.
* **Taux de rebond** - Pourcentage de sessions provenant de sources de référence qui n’ont eu aucun événement d’engagement.

![Page de référence](/help/dashboards/assets/referral-traffic.png)

Outre les mesures de performances globales présentées ci-dessus, trois panneaux supplémentaires présentent la distribution du trafic sur différents marchés, différentes sources de référence et différentes catégories d’intention de page <!-- the **Top Regions** panel breaks down traffic by geography. Meanwhile, the **Top Referral Sources** panel shows the platforms driving the most visits. Trend indicators for the metrics show how these values are changing over time compared to the previous period.-->

<!--## Top Referral URLs {#top-referrals}

The Top Referral URLs list surfaces your site's most visited pages from referrals.

![Top Referral URLs](/help/dashboards/assets/top-url.png)-->

## Détails sur les sources de référence et analyse des performances des URL {#traffic-details}

Les tableaux Détails des sources de référence et Analyse des performances des URL vous permettent d’évaluer à la fois le volume et la qualité du trafic. Cliquez sur chaque onglet ci-dessous pour plus de détails :

![Détails du Trafic de recommandation ](/help/dashboards/assets/traffic-details.png)

>[!BEGINTABS]

>[!TAB Détails des sources de référence]

La vue Détails des sources de référence répartit le trafic provenant de différentes plateformes telles qu’OpenAI, Microsoft, Google et Perplexity. Il affiche des mesures clés telles que les visites, le taux de rebond et le type de canal, ce qui vous aide à comprendre quelles sources d’IA et de recherche génèrent le trafic le plus engagé sur votre site.

* **Source** - Source du trafic de recommandation.
* **Visites** - Nombre total de visites pour chaque source.
* **Taux de rebond** - Pourcentage de sessions provenant de la source de référence qui n’ont eu aucun événement d’engagement.
* **Canal** - Le canal de la source, gagnée, payée ou les deux.

>[!TAB Analyse des performances des URL]

La vue Analyse des performances des URL classe les pages les plus performantes en fonction du volume de trafic de recommandation provenant des LLM et d’autres sources. Il met en évidence des mesures telles que le trafic, le taux de rebond, le taux de consentement et l’intention de page, ce qui vous permet d’identifier les pages qui attirent et conservent les visiteurs les plus engagés grâce aux recommandations pilotées par l’IA. Le tableau comporte un champ de recherche pour un accès rapide aux rubriques.

>[!ENDTABS]

Sur les deux tableaux, vous pouvez utiliser l’option **Exporter** pour télécharger le tableau .csv et partager les informations avec votre équipe ou inclure les tableaux dans les rapports d’exécution. De plus, pour les deux tableaux, vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**.
