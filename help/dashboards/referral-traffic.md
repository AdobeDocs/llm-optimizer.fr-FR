---
title: Trafic de référence
description: Découvrez comment utiliser le tableau de bord du trafic de référence pour voir comment les visiteurs accèdent à votre site à partir de plateformes externes, de citations d’IA et de liens de référence.
source-git-commit: 4cbfbe420a8419a04c2d6c465b6a290ee00ff3d4
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# Trafic de référence

Le trafic de référence montre comment les visiteurs et visiteuses accèdent à votre site à partir de plateformes externes, de citations d’IA et de liens de référence. Il suit et analyse les sources de trafic, les modèles de référence et les mesures de conversion des sites web et plateformes externes. Cela vous aidera à comprendre quelles sources, régions et pages génèrent le trafic le plus engagé. Les données proviennent des journaux CDN ou de la télémétrie opérationnelle d’AEM. Ces deux sources protègent la confidentialité et ne capturent pas de données personnelles des utilisateurs.

Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

Cette page présente les éléments suivants :

* [Configuration](#setup)
* [Filtres](#filters)
* [Performance globale de référence](#overall-performance)
* [Principales URL de référence](#top-referrals)
* [Détails du trafic de référence](#traffic-details)

## Configuration {#setup}

Lors de la première connexion, le tableau de bord Trafic de référence peut apparaître vide. Pour afficher vos données, vous devez configurer un fournisseur de trafic de référence en sélectionnant **Accéder à la configuration**.

![Configuration du parrainage](/help/dashboards/assets/referral-setup1.png)

<!--- 1. Select your Source (either CDN logs or AEM Operational Telemetry).
2. Enter a primary contact email.
3. Click **Request activation** to enable data ingestion. Hiding this until confirmation from PM-->

Une fois qu’un fournisseur de trafic de référence a été sélectionné, le tableau de bord s’affiche avec les mesures de trafic de référence.

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord. Vous pouvez personnaliser les éléments suivants :

* **Période** - Sélectionnez la période pour les données affichées. Par exemple, les 4 dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
* **Platform** - Sélectionnez une source de trafic spécifique telle que Google, OpenAI ou les médias sociaux.
* **Mode de consultation de la page** - Filtrez le trafic de recommandations par mode d’utilisation.
* **Channel Source** - Filtrez par source du canal. Les options incluent : canaux de référence LLM, Earned, pay ou mixte.
* **Type d’appareil** - Analysez le trafic par type d’appareil du visiteur, que ce soit un ordinateur, un appareil mobile ou tous les appareils.
  **Région** - Affichez les schémas de recommandation dans différentes zones géographiques.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Performance globale de référence {#overall-performance}

Le tableau de bord met en évidence les performances globales des références en affichant des mesures clés, notamment :

* **Trafic de référence total** - Trafic de référence total provenant de toutes les sources.
* **Taux de consentement** - Pourcentage de visiteurs et visiteuses qui acceptent une invite de consentement.
* **Taux de rebond** - Pourcentage de sessions provenant de sources de référence qui n’ont eu aucun événement d’engagement.

![Page de référence](/help/dashboards/assets/referral-traffic.png)

Outre les mesures de performances globales présentées ci-dessus, le panneau **Principales régions** répartit le trafic par zone géographique. Pendant ce temps, le panneau **Principales sources de référence** montre les plateformes qui génèrent le plus de visites. Les indicateurs de tendance des mesures montrent l’évolution de ces valeurs au fil du temps par rapport à la période précédente.

<!--## Top Referral URLs {#top-referrals}

The Top Referral URLs list surfaces your site’s most visited pages from referrals.

![Top Referral URLs](/help/dashboards/assets/top-url.png)-->

## Détails sur les sources de référence et analyse des performances des URL {#traffic-details}

Les tableaux Détails des sources de référence et Analyse des performances des URL vous permettent d’évaluer à la fois le volume et la qualité du trafic. Cliquez sur chaque onglet ci-dessous pour plus de détails :

![Détails du trafic de référence](/help/dashboards/assets/traffic-details.png)

>[!BEGINTABS]

>[!TAB Détails des sources de référence]

La vue Détails des sources de référence répartit le trafic provenant de différentes plateformes telles qu’OpenAI, Microsoft, Google et Perplexity. Il affiche des mesures clés telles que les visites, le taux de rebond et le type de canal, ce qui vous aide à comprendre quelles sources d’IA et de recherche génèrent le trafic le plus engagé sur votre site.

**Source** - Source du trafic de référence.
**Visites** - Nombre total de visites pour chaque source.
**Taux de rebond** - Pourcentage de sessions provenant de la source de référence qui n’ont eu aucun événement d’engagement.
**Canal** - Le canal de la source, gagnée, payée ou les deux.

>[!TAB Analyse des performances des URL]

La vue Analyse des performances des URL classe les pages les plus performantes en fonction du volume de trafic de référence provenant de LLM et d’autres sources. Il met en évidence des mesures telles que le trafic, le taux de rebond, le taux de consentement et l’intention de page, ce qui vous permet d’identifier les pages qui attirent et conservent les visiteurs les plus engagés grâce aux recommandations pilotées par l’IA. Le tableau comporte un champ de recherche pour un accès rapide aux rubriques.

>[!ENDTABS]

Sur les deux tableaux, vous pouvez utiliser l’option **Exporter** pour télécharger le tableau .csv et partager les informations avec votre équipe ou inclure le tableau de trafic de référence dans les rapports d’exécution.
