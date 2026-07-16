---
title: Démarrage rapide
description: Découvrez comment intégrer votre nom de marque et votre domaine, activer votre version d’essai à partir d’Experience Hub ou d’Experience Cloud et terminer la configuration pour Adobe LLM Optimizer.
feature: Quickstart, Onboarding
autotag-review: '2026-07-15T18:07:16.514Z'
TQID: 'https://experienceleague.adobe.com/Hp5j1st4fkfiBVKTTL-eHQX6Ovmw61-2hX2g1T8Ui8Y'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a080bb92-ba2a-4e53-ba60-f5184d1a9e9a
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d00e9f03-e50b-4162-b143-0c0817c937c2
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1201
ht-degree: 87%

---


# Démarrage rapide

Pour commencer à utiliser LLM Optimizer, suivez le processus d’intégration. Ensuite, personnalisez les catégories, les rubriques et les prompts, configurez le transfert du journal CDN et ouvrez les [tableaux de bord](/help/dashboards/dashboards-overview.md) pour obtenir des informations plus complètes.

<!--Where steps differ by layout, use **Customer Configuration (classic experience)** or **Brands Management** / **Prompts Management**, whichever matches your current interface.-->

## Expérience axée sur la marque {#brand-centric-experience}

Par défaut, les clients commencent dans une interface ciblée et axée sur la marque, avec une configuration pilotée par l’intégration. Dans cette interface, chaque organisation commence par une marque active et d’autres marques suggérées parmi lesquelles choisir. <!--Existing LLM Optimizer customers will shift to this Brand Centric experience gradually.-->

## Vue d’ensemble de l’intégration

Le processus d’intégration commence par votre domaine et le nom de votre marque. Chaque partie du parcours d’intégration est détaillée ci-dessous, ainsi que des conseils utiles pour commencer à utiliser LLM Optimizer dès que possible.

### Autoriser Adobe LLM Optimizer à accéder aux pages publiques

Pour fournir un contenu précis et des recommandations techniques, Adobe LLM Optimizer doit pouvoir accéder à vos pages destinées au public. Pour ce faire, un robot d’exploration interne sécurisé (agent utilisateur Spacecat/1.0) est utilisé.

Configuration requise :

* Ajoutez l’agent utilisateur Spacecat/1.0 à la liste autorisée dans le fichier robots.txt de votre site ou dans les règles de gestion du trafic de robots.
* Assurez-vous que les pages ne sont pas bloquées au niveau du domaine ou du réseau CDN. Les pages bloquées ne peuvent pas être indexées, ce qui signifie que les tâches d’optimisation et les informations ne peuvent pas être générées pour elles.

Si la visibilité du contenu semble faible dans le tableau de bord, vérifiez que le robot d’exploration a accès à vos domaines. L’accès restreint est une cause courante d’indexation incomplète.

## Étape 1 : Intégrer votre nom de marque et votre domaine {#step-1-onboard-your-domain}

Pour commencer à utiliser LLM Optimizer, commencez par activer votre version d’essai (si éligible) et intégrez votre nom de marque et votre domaine.

### Activer votre version d’essai

Le flux d’activation diffère en fonction de votre produit Adobe.

#### Clients AEM Cloud

Pour activer votre version d’essai, en tant que membre de la clientèle AEM Cloud, vous pouvez effectuer l’une des opérations suivantes :

* Accédez à [Experience Hub](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) et utilisez la carte Annonce de produit pour activer LLM Optimizer. Sélectionnez **Essayer LLM Optimizer** pour accéder à [https://llmo.now](https://llmo.now). Connectez-vous via IMS, puis saisissez un domaine et un nom de marque pour démarrer le processus d’intégration.
* Ou accédez directement à [https://llmo.now](https://llmo.now) et connectez-vous.

![Version d’évaluation de LLM Optimizer](/help/overview/assets/llm-trial.png)

#### Adobe Analytics et Adobe Customer Journey Analytics

Pour les clients Adobe Analytics et Adobe Customer Journey Analytics, une bannière s’affiche sur la page d’accueil d’Experience Cloud.

![Page d’accueil d’Experience Cloud avec la bannière Démarrer la version d’essai Adobe LLM Optimizer &#x200B;](/help/overview/assets/experience-cloud-llmo-trial-banner.png)

Vous pouvez activer votre version d’essai de l’une des façons suivantes :

* Sélectionnez **Démarrer la version d’essai Adobe LLM Optimize** dans la bannière.
* Accédez directement à [https://llmo.now](https://llmo.now) et connectez-vous.

Une fois l’essai actif, continuez en intégrant votre nom de marque et votre domaine.

>[!NOTE]
>
> * **Version d’essai gratuite :** les clients AEM Cloud et Adobe Analytics/Customer Journey Analytics peuvent utiliser la version d’essai gratuite de LLM Optimizer.
> * **Les personnes qui activent l’essai le ou après le 1er avril 2026** peuvent utiliser jusqu’à 100 prompts et un domaine. Elles peuvent également déployer des optimisations sur jusqu’à 10 URL pour un seul type d’opportunité.
> * **Les clients qui ont activé l’essai avant le 1er avril 2026** continuent d’avoir accès à jusqu’à 200 prompts en vertu de leurs conditions actuelles.
>
>L’utilisation au-delà des limites incluses nécessite un contrat de licence distinct. L’accès est fourni en l’état et selon la disponibilité. Il peut être modifié, limité ou supprimé à tout moment. Contactez votre représentant commercial ou représentante commerciale pour plus d’informations.

#### Intégrer votre nom de marque et votre domaine

Saisissez votre nom de marque et votre nom de domaine pour commencer à utiliser LLM Optimizer.

1. Saisissez le nom de votre marque et le domaine associé.

   * Il s’agit du domaine principal dans lequel vous souhaitez analyser et optimiser le contenu.

1. Terminez l’intégration.

   * LLM Optimizer commence ensuite à analyser votre domaine et à générer des informations.

![Domaine LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Les nouveaux prompts n’apparaîtront pas dans le [tableau de bord Présence de la marque](/help/dashboards/brand-presence.md) tant que le traitement ne sera pas terminé.

>[!NOTE]
>Le domaine fourni sera utilisé par toutes les personnes membres de votre organisation et ne peut pas être modifié.

Un petit ensemble de catégories, de rubriques et de prompts sera généré pendant la phase d’intégration. L’analyse de présence de la marque sur ces prompts sera disponible peu de temps après l’intégration de votre site.

La possibilité de déployer des optimisations en périphérie est également disponible. Pour en savoir plus, consultez [Optimize at Edge — Questions fréquentes](https://experienceleague.adobe.com/fr/docs/llm-optimizer/using/resources/optimize-at-edge/overview#frequently-asked-questions).

Configurez ensuite le [transfert du journal CDN](#step-4) pour l’analyse du trafic. LLM Optimizer a besoin des données et des informations de présence de la marque issues du trafic généré par l’IA agentique et du trafic de recommandation pour identifier les opportunités et fournir des conseils afin de renforcer la visibilité de l’IA.

### Clientèle non AEM Cloud

Une fois que votre organisation aura finalisé l’accord commercial, l’intégration à LLM Optimizer est effective, avec le domaine sélectionné par votre organisation. Une fois l’intégration terminée, connectez-vous à[https://llmo.now](https://llmo.now).

## Étape 2 : personnalisation des catégories, des rubriques et des prompts {#step-2-customize-categories-topics-and-prompts}

Une fois votre site intégré, vous pouvez afficher l’analyse de présence de la marque en fonction du petit ensemble de propts qui ont été générés automatiquement pendant la phase d’intégration. À l’avenir, vous pourrez personnaliser les catégories, les rubriques et les prompts de votre marque.

### Catégories, rubriques et suggestions d’expérience axée sur la marque

Vous pouvez ajouter des catégories, des rubriques et des invites comme suit :

* **Catégories** — Accédez à **Gestion des marques** et cliquez sur **Catégories**. Les catégories sont définies au niveau global et s’appliquent à toutes les marques gérées par Gestion des marques.

  ![Gestion des marques avec catégories dans la navigation](/help/assets/brand-centric-experience/llmo-app-shell.png)

* **Sujets et prompts** — Accédez à **Gestion des prompts** pour créer des rubriques et des prompts, y compris des prompts d’une marque spécifique.

  ![Gestion des prompts](/help/assets/brand-centric-experience/prompts-management.png)

>[!NOTE]
>Les prompts exacts que vous demandez aux LLM ne sont pas disponibles publiquement car ils ne sont pas divulgués par les LLM.

>[!NOTE]
>
> Pour plus d’informations sur la configuration des catégories, rubriques et prompts, reportez-vous à la page [Bonnes pratiques pour la configuration des catégories, rubriques, prompts](/help/overview/best-practices-topics-prompts.md).

## Étape 3 : informations sur la présence de la marque

Une fois votre domaine intégré, des informations initiales s’affichent dans la vue Présence de la marque en fonction des prompts qui ont été générés automatiquement lors de l’intégration. Une fois que vous avez personnalisé vos propres catégories, rubriques et prompts, LLM Optimizer déclenche automatiquement l’analyse de présence de la marque sur les prompts que vous avez fournis et les résultats seront disponibles sous 24 heures.

Accédez à **Présence des marques** et sélectionnez une marque pour laquelle vous souhaitez afficher la Présence des marques à l’aide de la liste déroulante Marque . Vous pouvez également consulter la visibilité de la marque au niveau de **Toutes les marques** avec cette expérience.

## Étape 4 : fournir des informations pour le transfert du journal CDN {#step-4}

Pour accéder aux informations sur le trafic généré par l’IA agentique et le trafic de recommandation, enregistrez le transfert des journaux CDN afin que LLM Optimizer puisse lire vos journaux d’accès.

### Transfert de journaux CDN

Vous pouvez ajouter des informations de transfert de journal CDN depuis **Brands Management** comme suit : ouvrez **Brands Management** et cliquez sur le libellé **CDN**.

![Gestion des marques – Transfert des journaux CDN](/help/assets/brand-centric-experience/brands-management-cdn.png)

>[!NOTE]
>Pour plus de détails concernant le transfert des journaux lors de l’utilisation d’un CDN géré par la clientèle (BYOCDN), consultez [Vue d’ensemble du transfert de journaux BYOCDN](/help/overview/log-forwarding/log-forwarding-overview.md).


## Étape 5 : explorer les tableaux de bord et prendre des mesures

Après avoir fourni des informations pour le transfert du journal de réseau CDN, vous pouvez accéder au tableau de bord de votre choix à partir de la section de navigation à gauche.

* afficher le tableau de bord de la [présence de la marque](/help/dashboards/brand-presence.md), visualiser votre score de visibilité et suivre vos performances par rapport aux autres marques ;
* explorer les tableaux de bord du trafic généré par l’IA [agentique](/help/dashboards/agentic-traffic.md) et du [trafic de recommandation](/help/dashboards/referral-traffic.md), si le transfert des journaux CDN a été configuré ;
* Utiliser les [opportunités](/help/dashboards/opportunities-overview.md) pour identifier les améliorations de contenu et techniques ;
* exporter des données et collaborer avec votre équipe ou inviter vos collègues à utiliser le produit.

Enfin, pour comprendre pleinement les fonctionnalités de LLM Optimizer, vous devez explorer tous les [tableaux de bord](/help/dashboards/dashboards-overview.md) disponibles.
