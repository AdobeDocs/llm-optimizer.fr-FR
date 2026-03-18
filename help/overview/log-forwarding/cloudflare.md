---
title: Transfert de journal - Cloudflare
description: Découvrez comment transférer les journaux CDN de Cloudflare vers le compartiment S3 Adobe pour la collecte de données de trafic agentic dans LLM Optimizer.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# Transfert de journal : Cloudflare {#log-forwarding-cloudflare}

Cette page explique comment transférer les journaux CDN de Cloudflare vers le compartiment S3 d’Adobe pour la collecte de données de trafic agentic. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour vous intégrer à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes fournies sur cette page pour configurer le transfert des journaux dans la console du tableau de bord Cloudflare.

## Étape 1 : intégration dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez au **Tableau de bord de configuration du client**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du réseau CDN**.

   ![Onglet Configuration du réseau CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Commencer**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png) -->

1. En regard de **Activer AI Traffic Insights**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)

1. Sélectionnez **Cloudflare (BYOCDN)**.

   ![Sélectionnez Cloudflare](/help/overview/assets/log-forwarding/cloudflare/cloudflare-select.png)

1. Cliquez sur **Intégration**.

   <!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Étape 2 : créer une tâche Logpush dans Cloudflare {#step-2}

Sur le tableau de bord [Cloudflare](https://dash.cloudflare.com/login), procédez comme suit :

1. Accédez à la page **Logpush** au niveau **Domaine (zone)**.
1. Sélectionnez **Créer une tâche Logpush**.
1. Dans **Sélectionner une destination**, choisissez **Amazon S3**.
1. Saisissez les informations de destination suivantes :

   - **Compartiment** : nom du compartiment S3. Copiez la valeur de la page Configuration du réseau CDN LLM Optimizer .

     ![Nom du compartiment](/help/overview/assets/log-forwarding/common/bucket-name.png)

   - **Chemin** : emplacement du compartiment dans le conteneur de stockage. Copiez la valeur de la page Configuration du réseau CDN LLM Optimizer .

     ![Chemin d’accès Cloudflare](/help/overview/assets/log-forwarding/cloudflare/cloudflare-path.png)

   - **Organiser les journaux dans des sous-dossiers quotidiens** (recommandé).

     ![Sous-dossiers quotidiens](/help/overview/assets/log-forwarding/cloudflare/cloudflare-daily-subfolders.png)

   - **Région du compartiment** — Copiez la valeur de la page Configuration du réseau CDN LLM Optimizer .

     <!-- ![Region](/help/overview/assets/log-forwarding/cloudflare/cloudflare-region.png)-->

   - Si le chiffrement côté serveur n’est pas nécessaire, ne cochez pas cette case.

   Une fois les étapes ci-dessus terminées, sélectionnez **Continuer**.

1. Pour prouver la propriété, Cloudflare enverra un fichier à la destination désignée. Pour trouver le jeton, cliquez sur le bouton **Ouvrir** dans l’onglet **Aperçu** du fichier de vérification de la propriété. Copiez le jeton de propriété de la page de configuration du réseau CDN de LLM Optimizer, puis collez-le dans le tableau de bord Cloudflare pour vérifier votre accès au compartiment . Saisissez le jeton de propriété et sélectionnez **Continuer**.

   <!--![Ownership token](/help/overview/assets/log-forwarding/cloudflare/cloudflare-ownership-token.png)-->

1. Sélectionnez le jeu de données **Requêtes HTTP** à envoyer au service de stockage .

1. Configurez votre tâche Logpush :

   - Saisissez le **nom de la tâche**.

   - Dans **Envoyer les champs suivants**, consultez les valeurs de la page de configuration de LLM Optimizer.

     ![Champs Logpush](/help/overview/assets/log-forwarding/cloudflare/cloudflare-logpush-fields.png)

   - **Format du journal** : JSON.

     <!--![JSON format](/help/overview/assets/log-forwarding/cloudflare/cloudflare-json-format.png)-->

1. Dans **Options avancées** :

   - Sélectionnez le format des champs d’horodatage dans vos journaux : `RFC3339`.

     ![Format de l’horodatage](/help/overview/assets/log-forwarding/cloudflare/cloudflare-timestamp-format.png)

   - Pour les taux d’échantillonnage, sélectionnez **Tous les journaux**.

     ![Taux d’échantillonnage](/help/overview/assets/log-forwarding/cloudflare/cloudflare-sampling-rate.png)

1. Sélectionnez **Envoyer** une fois la configuration de la tâche Logpush terminée.
