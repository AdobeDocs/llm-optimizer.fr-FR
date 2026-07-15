---
title: Transfert de journaux – CloudFront
description: Découvrez comment transférer les journaux CDN de CloudFront vers le compartiment S3 d’Adobe pour la collecte de données du trafic généré par l’IA agentique dans LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:47:22.372Z'
TQID: 'https://experienceleague.adobe.com/0aPeInYmcNRZLHUdABG2cEpT-dXb6GhEMoNUqMLMusY'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e69d5a42-0217-4ca5-9396-a9a826a170daid: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 466
ht-degree: 100%

---


# Transfert de journaux : CloudFront {#log-forwarding-cloudfront}

Cette page explique comment transférer les journaux CDN de CloudFront vers le compartiment S3 d’Adobe pour la collecte de données du trafic généré par l’IA agentique. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour l’intégration à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes indiquées sur cette page pour configurer le transfert des journaux dans la console du tableau de bord CloudFront.

## Étape 1 : intégrer dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez au **tableau de bord de la configuration cliente**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du CDN**.

   ![Onglet Configuration du CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Prise en main**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. À côté de **Activer les informations sur le trafic généré par l’IA**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)

1. Saisissez votre identifiant de **compte AWS**.

   ![Identifiant de compte AWS](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)

1. Sélectionnez **CloudFront (BYOCDN)**.

   ![Sélectionner CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Cliquez sur **Intégration**.

   ![Bouton Intégration](/help/overview/assets/log-forwarding/common/onboard-button.png)

## Étape 2 : activer la journalisation standard (console CloudFront) {#step-2}

Pour activer la journalisation standard, à partir de la [console de gestion AWS](https://aws.amazon.com/console/) :

1. Accédez à la [console CloudFront](https://console.aws.amazon.com/cloudfront/v4/home) et [mettez à jour une distribution existante](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowToUpdateDistribution.html#HowToUpdateDistributionProcedure).

1. Ouvrez l’onglet **Journalisation**.

1. Choisissez **Ajouter**, puis sélectionnez le service qui recevra les journaux, ici **Amazon S3**.

1. Pour **Destination**, sélectionnez ou créez la ressource. Saisissez le **nom du compartiment**, vous pouvez copier la valeur de la page de configuration du réseau CDN de LLM Optimizer.

   ![Nom du compartiment CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-bucket-name.png)

1. Configurez les **paramètres supplémentaires** :

   - **Sélection du champ** : choisissez les champs du fichier journal. Consultez les champs obligatoires sur la page Configuration du réseau CDN de LLM Optimizer.

     ![Sélection de champs CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-field-selection.png)

   - **Partitionnement** : copiez le **suffixe de chemin** depuis la page de configuration de LLM Optimizer.

     ![Partitionnement CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-partitioning.png)

   - **Format de sortie** : le format doit être JSON.

     ![Format de sortie CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-output-format.png)

1. Suivez les étapes pour mettre à jour ou créer la distribution.

1. Sur la page **Journaux**, confirmez que **Activé** s’affiche en regard de la distribution.

## Activer la journalisation standard pour la diffusion entre comptes {#cross-account}

Le **compte source** (avec la distribution CloudFront) envoie les journaux d’accès au **compte de destination** (le compartiment S3 affiché dans la page de configuration du réseau CDN de LLM Optimizer). Les deux comptes doivent disposer des autorisations appropriées.

Par exemple : le compte source `111111111111` envoie  les journaux à un compartiment S3 dans le compte de destination `222222222222`. Vous pouvez utiliser l’[interface de ligne de commande AWS](https://aws.amazon.com/cli/).

>[!NOTE]
>
>Dans les commandes ci-dessous, remplacez la valeur de l’ARN de destination de la diffusion (`arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination`) par la valeur de l’**ARN de destination de la diffusion** à partir de la page de configuration de LLM Optimizer.

![ARN de destination de la diffusion](/help/overview/assets/log-forwarding/cloudfront/cloudfront-delivery-destination-arn.png)

### Configurer le compte source {#source-account}

Vous devez ensuite configurer le compte source :

1. **Créer une source de diffusion** : remplacez le nom et l’ARN de distribution :

   ```bash
   aws logs put-delivery-source --name s3-cf-delivery \
     --resource-arn arn:aws:cloudfront::111111111111:distribution/E1TR1RHV123ABC \
     --log-type ACCESS_LOGS
   ```

1. **Créer la diffusion** : liez la source à la destination. Utilisez l’ARN de destination à partir de l’étape « Configurer le compte de destination » :

   ```bash
   aws logs create-delivery --delivery-source-name s3-cf-delivery \
     --delivery-destination-arn arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination
   ```

1. **Vérifier :**

   - Dans le compte **source** : console CloudFront > votre distribution > onglet **Journalisation**. Sous **Type**, vous devez voir la diffusion de journaux entre comptes S3.
   - Dans le compte **destination** : console S3 > compartiment. Vous devez voir le préfixe (par exemple, `MyLogPrefix`) et les journaux dans ce dossier.
