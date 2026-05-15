---
title: Trafic de recommandation
description: Découvrez comment utiliser le tableau de bord du trafic de recommandation pour voir comment les visiteurs et visiteuses accèdent à votre site à partir de plateformes externes, de citations d’IA et de liens de recommandation.
feature: Referral Traffic
autotag-review: '2026-05-15T17:57:28.534Z'
TQID: 'https://experienceleague.adobe.com/rMSltSJf-UH4FHoST9NhmeY-hGVNLXsFXbCLzZenW5w'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: e3c08d81-9e25-4503-9df5-8dd1f489aa99
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 09e228275cf84316ee2e8990636bb3b8865ac263
workflow-type: tm+mt
source-wordcount: 750
ht-degree: 78%

---


# Trafic de recommandation

Le trafic de recommandation montre comment les visiteurs et visiteuses accèdent à votre site à partir de plateformes externes, de citations d’IA et de liens de recommandation. Il suit et analyse les sources de trafic, les tendances de recommandation et les mesures de conversion des sites web et plateformes externes. Cela vous aidera à comprendre quelles sources, régions et pages génèrent le trafic le plus engagé. <!--Data is sourced from the CDN logs, a privacy-preserving source that does not capture personal user data.--> Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

>[!NOTE]
>Par défaut, ce tableau de bord génère des informations sur le trafic à partir des **journaux CDN**. Si votre entreprise fait partie d’une offre payante, vous pouvez connecter **&#x200B;**&#x200B;ou **Google Analytics 4**(GA4) afin d’ajouter des données qui mesurent l’engagement sur le site et la découverte pilotée par l’IA. Ces données sont disponibles dans l’onglet **Impact commercial**. Notez que sans intégration à Adobe Analytics ou GA4, l’onglet n’est pas renseigné. Pour plus d’informations[&#128279;](/help/dashboards/adobe-analytics-integration.md) consultez Intégration d’Adobe Analytics ou [Intégration de Google Analytics](/help/dashboards/google-analytics-integration.md).

![Page de recommandation](/help/dashboards/assets/referral-traffic.png)

Cette page contient les éléments suivants :

* [Configuration](#setup)
* [Filtres](#filters)
* [Vue d’ensemble des performances globales de recommandation](#overall-performance)
* [Principales URL de recommandation](#top-referrals)
* [Détails du trafic de recommandation](#traffic-details)

Si vous utilisez l’[expérience orientée marque](/help/overview/quick-start.md#brand-centric-experience), accédez à **Trafic de recommandation** et sélectionnez le site pour lequel vous souhaitez afficher les informations sur le Trafic de recommandation LLM.

![Trafic de recommandation — sélecteur de site (expérience centrée sur la marque)](/help/assets/brand-centric-experience/referral-traffic-dashboard.png)

## Configuration {#setup}

Lors de la première connexion, le tableau de bord du trafic de recommandation peut apparaître vide. Pour afficher vos données, vous devez configurer le transfert du journal du réseau CDN.

Pour les clients qui utilisent l’[expérience orientée marque](/help/overview/quick-start.md#brand-centric-experience), vous pouvez ajouter des informations sur le transfert de journal CDN en accédant à **Gestion des marques** et en cliquant sur le libellé **CDN**.

**Configuration du client (expérience classique) :** configurer [transfert du journal CDN](/help/dashboards/customer-configuration.md#cdn-configuration) en sélectionnant **Accéder à la configuration**.

![Configuration du trafic de recommandation](/help/dashboards/assets/referral-setup1.png)

<!--
1. Select your Source (either CDN logs or AEM Operational Telemetry).
2. Enter a primary contact email.
3. Click **Request activation** to enable data ingestion. Hiding this until confirmation from PM
-->

Une fois activé, le tableau de bord sera renseigné avec les mesures de trafic de recommandation.

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez affecteront **toutes** les sections présentes dans le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** pour sélectionner la période pour les données affichées. Par exemple, les quatre dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Plateforme** : sélectionnez une source de trafic spécifique telle que Google, OpenAI ou des réseaux sociaux.
* **Intention de la page** : filtrez le trafic de recommandation par intention utilisateur.
* **Source du canal** : filtrez par source du canal. Les options incluent : LLM, canaux de recommandation gagnés, payants ou mixtes.
* **Type d’appareil** : analysez le trafic par type d’appareil du visiteur ou de la visiteuse, que ce soit un ordinateur, un appareil mobile ou tous les appareils.
* **Région** : affichez les tendances de recommandation dans différentes zones géographiques.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Vue d’ensemble des performances globales de recommandation {#overall-performance}

Le tableau de bord met en évidence les performances globales de recommandation en affichant des mesures clés, notamment :

* **Total du trafic de recommandation** : total du trafic de recommandation de toutes les sources.
* **Trafic de recommandation depuis les LLM** : trafic de recommandation total depuis les LLM.
* **Taux de consentement** : pourcentage de visiteurs et visiteuses qui acceptent un prompt de consentement.
* **Taux de rebond** : pourcentage de sessions provenant de sources de recommandation qui n’ont eu aucun événement d’engagement.

![Page de recommandation](/help/dashboards/assets/referral-traffic.png)

Outre les mesures de performances globales présentées ci-dessus, trois panneaux supplémentaires présentent la répartition du trafic sur différents marchés, différentes sources de recommandation et différentes catégories d’intention de page <!-- the **Top Regions** panel breaks down traffic by geography. Meanwhile, the **Top Referral Sources** panel shows the platforms driving the most visits. Trend indicators for the metrics show how these values are changing over time compared to the previous period.-->.

<!--
## Top Referral URLs {#top-referrals}

The Top Referral URLs list surfaces your site's most visited pages from referrals.

![Top Referral URLs](/help/dashboards/assets/top-url.png)
-->

## Détails sur les sources de recommandation et analyse des performances des URL {#traffic-details}

Les tableaux Détails des sources de recommandation et Analyse des performances des URL vous permettent d’évaluer à la fois le volume et la qualité du trafic. Cliquez sur chaque onglet ci-dessous pour plus de détails :

![Détails du trafic de recommandation](/help/dashboards/assets/traffic-details.png)

>[!BEGINTABS]

>[!TAB Détails des sources de recommandation]

La vue Détails des sources de recommandation répartit le trafic provenant de différentes plateformes telles qu’OpenAI, Microsoft, Google et Perplexity. Elle affiche des mesures clés telles que les visites, le taux de rebond et le type de canal, ce qui vous aide à comprendre quelles sources d’IA et de recherche génèrent le trafic le plus engagé sur votre site.

* **Source** : source du trafic de recommandation.
* **Visites** : nombre total de visites pour chaque source.
* **Taux de rebond** : pourcentage de sessions provenant de la source de recommandation qui n’ont eu aucun événement d’engagement.
* **Canal** : canal de la source, gagné, payé ou les deux.

>[!TAB Analyse des performances des URL]

La vue Analyse des performances des URL classe les pages les plus performantes en fonction du volume de trafic de recommandation provenant des LLM et d’autres sources. Elle met en évidence des mesures telles que le trafic, le taux de rebond, le taux de consentement et l’intention de page, ce qui vous permet d’identifier les pages qui attirent et conservent les visiteurs et les visiteuses les plus engagés grâce aux recommandations basées sur l’IA. Le tableau comporte un champ de recherche pour un accès rapide aux rubriques.

>[!ENDTABS]

Sur les deux tableaux, vous pouvez utiliser l’option **Exporter** pour télécharger le tableau au format .csv et partager les informations avec votre équipe ou inclure les tableaux dans les rapports destinés aux cadres. De plus, pour les deux tableaux, vous pouvez personnaliser les mesures affichées en cliquant sur le bouton **Configurer les colonnes**.
