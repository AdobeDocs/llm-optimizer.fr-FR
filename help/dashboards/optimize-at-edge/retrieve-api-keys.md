---
title: Récupération des clés API
description: Comment récupérer vos clés API Edge Optimize de production et d’évaluation à partir de LLM Optimizer.
feature: Opportunities
autotag-review: '2026-05-15T17:58:10.897Z'
TQID: 'https://experienceleague.adobe.com/4R-cx6wv75Oowj9ZvEPGCzQbQBSoppgDuI5Ut1IbObA'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 337
ht-degree: 1%

---


# Récupération des clés API

Avant de configurer votre réseau CDN, récupérez vos clés d’API Edge Optimize à partir de l’interface utilisateur de LLM Optimizer. Vous avez besoin d’une clé API **production** pour le trafic en direct. Vous pouvez également récupérer une clé API **staging** pour tester d’abord le routage sur un nom d’hôte d’évaluation.

## Clé API de production

1. Dans LLM Optimizer, ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau de diffusion de contenu**.

   ![Accédez à Configuration cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Recherchez la section **Déployer des optimisations sur des agents d’IA**. Cochez la case **Activer le moteur d’optimisation**.

   ![Déploiement des optimisations sur les agents d’IA - en attente](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Dans la boîte de dialogue de confirmation, sélectionnez **Activer**.

   ![Boîte de dialogue de confirmation Activer le moteur d’optimisation](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Sélectionnez **Afficher les détails**. Dans la boîte de dialogue **Déployer les détails des optimisations**, copiez la **Clé API de production** (utilisez **Copier** en regard du champ).

   ![Clé de l’API de production dans les détails des optimisations du déploiement](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >La boîte de dialogue peut indiquer que la configuration n’est pas terminée. Cela est attendu jusqu’à ce que le routage soit vérifié. Vous pouvez toujours copier la clé API afin que votre équipe informatique ou réseau CDN puisse terminer la configuration.

Si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

## Clé API d’évaluation (facultatif)

Pour valider le routage dans un environnement inférieur avant d’activer le routage de production, vous pouvez configurer un nom d’hôte intermédiaire.

**Conditions requises**

* Le nom d’hôte d’évaluation doit se trouver sur le **même domaine enregistrable** que la production (par exemple, `https://staging.example.com` lorsque la production est `https://www.example.com`).
* Un seul domaine **’évaluation** par site. Une fois enregistré, il ne peut pas être modifié sans contacter Adobe.

**Étapes**

1. Dans LLM Optimizer, ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau de diffusion de contenu**.
2. Sous **Déployer les optimisations sur les agents d’IA**, sélectionnez **Ajouter un domaine intermédiaire** (ou **Domaine d’évaluation** si un domaine d’évaluation est déjà configuré).
3. Saisissez l’URL d’évaluation complète, y compris `https://`, puis sélectionnez **Définir le domaine**.
4. Copiez la clé API **staging** à partir de la boîte de dialogue de confirmation.

   ![Clé API du domaine d’évaluation](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Déployez les mêmes règles de routage sur votre environnement d’évaluation à l’aide de la clé API d’évaluation.

Si vous avez besoin d&#39;aide, contactez `llmo-at-edge@adobe.com`.

## Étapes suivantes

Après avoir récupéré vos clés API, revenez à votre [guide de configuration du réseau CDN](/help/dashboards/optimize-at-edge/overview.md#cdn-configuration-guides) pour configurer le routage.
