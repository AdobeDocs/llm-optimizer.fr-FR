---
title: Transfert de journal - CloudFront
description: Découvrez comment transférer les journaux CDN de CloudFront vers le compartiment S3 Adobe pour la collecte de données de trafic agentic dans LLM Optimizer.
feature: Agentic Traffic
source-git-commit: d1f98770b39f550c36d93ece9b89933c0e90f189
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---


# Transfert de journal : CloudFront {#log-forwarding-cloudfront}

Cette page explique comment transférer les journaux CDN de CloudFront vers le compartiment S3 d’Adobe pour la collecte de données de trafic agentic. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour vous intégrer à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes fournies sur cette page pour configurer le transfert des journaux dans la console du tableau de bord CloudFront.

## Étape 1 : intégration dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez au **Tableau de bord de configuration du client**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du réseau CDN**.

   ![Onglet Configuration du réseau CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Commencer**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. En regard de **Activer AI Traffic Insights**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)

1. Saisissez votre **ID de compte AWS**.

   ![Identifiant de compte AWS](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)

1. Sélectionnez **CloudFront (BYOCDN)**.

   ![Sélectionner CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Cliquez sur **Intégration**.

   ![Bouton Intégration](/help/overview/assets/log-forwarding/common/onboard-button.png)

## Étape 2 : activer la journalisation standard (console CloudFront) {#step-2}

Pour activer la journalisation standard, à partir de la console de gestion [AWS](https://aws.amazon.com/console/) :

1. Accédez à la [console CloudFront](https://console.aws.amazon.com/cloudfront/v4/home) et [mettez à jour une distribution existante](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowToUpdateDistribution.html#HowToUpdateDistributionProcedure).

1. Ouvrez l’onglet **Journalisation**.

1. Choisissez **Ajouter**, puis sélectionnez le service qui recevra les logs, ici **Amazon S3**.

1. Pour **Destination**, sélectionnez ou créez la ressource. Saisissez le **nom du compartiment**, vous pouvez copier la valeur de la page de configuration du réseau CDN LLM Optimizer.

   ![Nom du compartiment CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-bucket-name.png)

1. Configurez **paramètres supplémentaires** :

   - **Sélection du champ** — choisissez les champs du fichier journal. Voir les champs obligatoires sur la page Configuration du réseau CDN LLM Optimizer .

     ![Sélection de champ CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-field-selection.png)

   - **Partitionnement** — copiez le **suffixe de chemin** de la page de configuration de LLM Optimizer.

     ![Partitionnement CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-partitioning.png)

   - **Format de sortie** — le format doit être JSON.

     ![Format de sortie CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-output-format.png)

1. Suivez les étapes de mise à jour ou de création de la distribution.

1. Sur la page **Journaux**, confirmez que **Activé** s’affiche en regard de la distribution.

## Activer la journalisation standard pour la diffusion entre comptes {#cross-account}

Le **compte source** (avec la distribution CloudFront) envoie les journaux d’accès au **compte de destination** (le compartiment S3 affiché dans la page de configuration du réseau CDN de LLM Optimizer). Les deux comptes doivent disposer des autorisations appropriées.

Par exemple : le compte source envoie `111111111111` les journaux à un compartiment S3 dans le compte de destination `222222222222`. Vous pouvez utiliser l’interface de ligne de commande [AWS](https://aws.amazon.com/cli/).

>[!NOTE]
>
>Dans les commandes ci-dessous, remplacez la valeur de l’ARN de destination de la diffusion (`arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination`) par la valeur de l’**ARN de destination de la diffusion** à partir de la page de configuration de LLM Optimizer.

![ARN de destination de la diffusion](/help/overview/assets/log-forwarding/cloudfront/cloudfront-delivery-destination-arn.png)

### Configuration du compte source {#source-account}

Vous devez ensuite configurer le compte source :

1. **Créer une source de diffusion** - remplacez le nom et la distribution ARN :

   ```bash
   aws logs put-delivery-source --name s3-cf-delivery \
     --resource-arn arn:aws:cloudfront::111111111111:distribution/E1TR1RHV123ABC \
     --log-type ACCESS_LOGS
   ```

1. **Créer la diffusion** - lier la source à la destination ; utiliser l’ARN de destination à partir de l’étape « Configurer le compte de destination » :

   ```bash
   aws logs create-delivery --delivery-source-name s3-cf-delivery \
     --delivery-destination-arn arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination
   ```

1. **Vérifier :**

   - Dans le compte **source** : console CloudFront > onglet distribution > **Journalisation** . Sous **Type** vous devriez voir la diffusion du journal entre comptes S3.
   - Dans le compte **destination** : Console S3 > compartiment . Vous devriez voir le préfixe (par exemple, `MyLogPrefix`) et les journaux dans ce dossier.
