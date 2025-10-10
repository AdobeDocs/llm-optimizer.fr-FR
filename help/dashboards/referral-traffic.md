---
title: Trafic de référence
description: Voici la présentation de l’article.
source-git-commit: c83b4929a82331534654fcfdccd41d91eefe6d92
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# Trafic de référence

Le trafic de référence montre comment les visiteurs et visiteuses accèdent à votre site à partir de plateformes externes, de citations d’IA et de liens de référence. Il suit et analyse les sources de trafic, les modèles de référence et les mesures de conversion des sites web et plateformes externes. Cela vous aidera à comprendre quelles sources, régions et pages génèrent le trafic le plus engagé. Les données proviennent des journaux CDN ou des **de télémétrie opérationnelle AEM (ajout d’un lien)**. Ces deux sources protègent la confidentialité et ne capturent pas de données personnelles des utilisateurs.

Il existe également des filtres personnalisables pour vous aider à affiner les données affichées.

Cette page présente les éléments suivants :

* [Configuration](#setup)
* [Filtres](#filters)
* [Performance globale de référence](#overall-performance)
* [Principales URL de référence](#top-referrals)
* [Détails du trafic de référence](#traffic-details)

## Configuration {#setup}

Lors de la première connexion, le tableau de bord Trafic de référence peut apparaître vide. Pour afficher vos données, vous devez configurer un fournisseur de trafic de référence.

![Configuration du parrainage](/help/dashboards/assets/referral-setup.png)

1. Sélectionnez votre Source (journaux CDN ou télémétrie opérationnelle AEM).
2. Saisissez l’adresse e-mail principale du contact.
3. Cliquez sur **Demander l’activation** pour activer l’ingestion des données.

Une fois activé, le tableau de bord s’affichera avec les mesures de trafic de parrainage.

## Filtres {#filters}

En haut de la page, vous pouvez appliquer des filtres pour affiner votre vue. Les filtres que vous choisissez auront un impact sur **toutes** les sections présentes sur le tableau de bord. Vous pouvez personnaliser les éléments suivants :

**Période** - Sélectionnez la période pour les données affichées. Par exemple, les 4 dernières semaines. Vous avez également la possibilité de personnaliser la période en sélectionnant l’option **Semaines personnalisées**.
**Platform** - Sélectionnez une source de trafic spécifique telle que Google, OpenAI ou les médias sociaux.
**Canal** - Filtrez les canaux tels que les canaux gagnés ou payés. Si vous préférez un mélange entre les deux, sélectionnez l’option **Tous les canaux**.
**Channel Source** - Filtrez par source du canal. les options incluent : affichage, recherche, référence, vidéo et réseaux sociaux. Vous pouvez également utiliser la **Toutes les plateformes** pour afficher toutes les sources de canal.
**Type d’appareil** - Analysez le trafic par type d’appareil du visiteur, que ce soit un ordinateur, un appareil mobile ou tous les appareils.
**Région** - Affichez les schémas de recommandation dans différentes zones géographiques.

Après avoir sélectionné le filtre souhaité, cliquez sur **Appliquer les filtres** pour appliquer la sélection au tableau de bord.

## Performance globale de référence {#overall-performance}

Le tableau de bord met en évidence les performances globales des références en affichant les mesures clés suivantes :

* **Trafic de référence total** - Trafic de référence total provenant de toutes les sources.
* **Taux de consentement** - Pourcentage de visiteurs et visiteuses qui acceptent une invite de consentement.
* **Taux de rebond** - Pourcentage de sessions provenant de sources de référence qui n’ont eu aucun événement d’engagement.

![Page de référence](/help/dashboards/assets/referral-traffic.png)

Outre les mesures de performances globales présentées ci-dessus, le panneau **Principales régions** répartit le trafic par zone géographique. Pendant ce temps, le panneau **Principales sources de référence** montre les plateformes qui génèrent le plus de visites.

## Principales URL de référence {#top-referrals}

La liste des principales URL de référence affiche les pages de votre site les plus visitées à partir de références.

![Principales URL de référence](/help/dashboards/assets/top-url.png)

## Détails du trafic de référence {#traffic-details}

Le tableau des détails du trafic de référence vous permet d’évaluer à la fois le volume et la qualité du trafic. Il fournit une répartition détaillée par source, y compris le nombre de visites, les taux de rebond et le type de canal.

![Détails du trafic de référence](/help/dashboards/assets/traffic-details.png)

Le tableau contient les catégories suivantes :

**Source** - Source du trafic de référence.
**Visites** - Nombre total de visites pour chaque source.
**Taux de rebond** - Pourcentage de sessions provenant de la source de référence qui n’ont eu aucun événement d’engagement.
**Canal** - Le canal de la source, gagnée, payée ou les deux.

Vous pouvez utiliser l’option **Exporter** pour télécharger le tableau .csv et partager les informations avec votre équipe ou inclure le tableau de trafic de référence dans les rapports d’exécution.
