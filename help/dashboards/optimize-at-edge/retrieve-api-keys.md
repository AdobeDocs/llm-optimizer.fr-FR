---
title: Récupérez vos clés API
description: Comment récupérer vos clés API Edge Optimize de production et de préproduction depuis LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T18:05:12.505Z'
TQID: 'https://experienceleague.adobe.com/X3vIzxrlaqJ5Mx3K8rOpX2QqgGyxT6p8qfdLzTWC1gQ'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 337
ht-degree: 100%

---


# Récupérez vos clés API

Avant de configurer votre CDN, récupérez vos clés API Edge Optimize depuis l’interface d’utilisation de LLM Optimizer. Vous avez besoin d’une clé API de **production** pour le trafic en direct. Vous pouvez également récupérer une clé API de **préproduction** pour tester d’abord le routage sur un nom d’hôte de préproduction.

## Clé API de production

1. Dans LLM Optimizer, ouvrez **Configuration cliente** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à Configuration cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Repérez la section **Déployer les optimisations vers les agents IA**. Cochez la case **Activer le moteur d’optimisation**.

   ![Déployer des optimisations vers les agents IA — en attente](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Sélectionner **Activer** dans la boîte de dialogue de confirmation.

   ![Activez la boîte de dialogue de confirmation du moteur d’optimisation.](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Sélectionnez **Afficher les détails**. Dans la boîte de dialogue **Détails des optimisations de déploiement**, copiez la **clé API de production** (utilisez **Copier** à côté du champ).

   ![Clé API de production dans les détails des optimisations de déploiement](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >La boîte de dialogue peut indiquer que l’installation n’est pas terminée. Ceci est normal tant que le routage n’a pas été vérifié ; vous pouvez toujours copier la clé API afin que votre équipe informatique ou CDN puisse terminer la configuration.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de équipe Adobe en charge des comptes ou `llmo-at-edge@adobe.com`.

## Clé API d’évaluation (facultative)

Pour valider le routage dans un environnement inférieur avant d’activer le routage en production, vous pouvez configurer un nom d’hôte de préproduction.

**Conditions requises**

* Le nom d’hôte de préproduction doit être sur le **même domaine enregistrable** que la production (par exemple, `https://staging.example.com` lorsque la production est `https://www.example.com`).
* **Un seul** domaine de préproduction par site. Une fois enregistré, vous devez contacter Adobe pour toute modification.

**Étapes**

1. Dans LLM Optimizer, ouvrez **Configuration cliente** et sélectionnez l’onglet **Configuration du réseau CDN**.
2. Sous **Déployer les optimisations sur les agents d’IA**, sélectionnez **Ajouter un domaine de préproduction** (ou **Domaine de préproduction** si un domaine de préproduction est déjà configuré).
3. Saisissez l’URL complète de l’environnement de test, y compris `https://` et sélectionnez **Définir le domaine**.
4. Copiez la clé API de **préproduction** depuis la boîte de dialogue de confirmation.

   ![Clé API du domaine de préproduction](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Déployez les mêmes règles de routage sur votre environnement de préproduction à l’aide de la clé API de préproduction.

Si vous avez besoin d’aide, contactez `llmo-at-edge@adobe.com`.

## Étapes suivantes

Après avoir récupéré vos clés API, revenez à votre [guide de configuration du réseau CDN](/help/dashboards/optimize-at-edge/overview.md#cdn-configuration-guides) pour configurer le routage.
