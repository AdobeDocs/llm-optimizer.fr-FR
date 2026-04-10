---
title: Transfert de journal - CloudFront (interface de ligne de commande AWS)
description: Transférer les journaux CDN CloudFront vers le compartiment S3 d’Adobe à l’aide de l’interface de ligne de commande AWS pour la configuration et les opérations de diffusion.
feature: Agentic Traffic
source-git-commit: 3277e7f7f2e0c5e4693e40473d595b12d9e5f2e8
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Transfert de journal : CloudFront (interface de ligne de commande AWS) {#log-forwarding-cloudfront-cli}

Cette page explique comment transférer les journaux CDN de CloudFront vers le compartiment S3 d’Adobe pour la collecte de données de trafic agentic. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour vous intégrer à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes fournies sur cette page pour configurer le transfert des journaux à l’aide de l’interface de ligne de commande [&#128279;](https://aws.amazon.com/cli/) à l’[étape 2](#step-2-cli).

>[!NOTE]
>
> Ce guide explique comment configurer le transfert de journal à l’aide de l’[interface de ligne de commande &#x200B;](https://aws.amazon.com/cli/). Si vous souhaitez configurer le transfert de journal à l’aide de l’interface utilisateur **CloudFront**, voir [Transfert de journal : CloudFront](/help/overview/log-forwarding/cloudfront.md).

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

1. Saisissez votre **ID de compte**.

<!--  ![AWS Account ID](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)-->

1. Sélectionnez **CloudFront (BYOCDN)**.

   ![Sélectionner CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Cliquez sur **Intégration**.

<!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Étape 2 : configurer le transfert du journal de réseau CDN avec l’interface de ligne de commande AWS {#step-2-cli}

Configurez le transfert des journaux CDN avec l’interface de ligne de commande AWS comme suit :

### Configuration des informations d’identification de l’interface de ligne de commande AWS

Configurez le MAC des informations d’identification de l’interface de ligne de commande AWS. Ouvrez ~/.aws/credentials et saisissez les valeurs des variables ci-dessous :

```text
[LLMO]
aws_access_key_id=<VALUE_OF_ACCESS_KEY_ID>
aws_secret_access_key=<VALUE_OF_SECRET_KEY>
aws_session_token=<ONLY_IF_USING_SECURITY_TOKEN_SERVICE> ## Optional
```

### Tester la connexion

Exécutez la commande ci-dessous pour tester la connexion :

```bash
aws sts get-caller-identity --profile LLMO
```

Exemple de sortie réussie :

```bash
aws sts get-caller-identity --profile LLMO
{
    "UserId": "AxxxxxxxxxxxP:user",
    "Account": "012345678912",
    "Arn": "arn:aws:sts::012345678912:assumed-role/klam-master-role-BatlY3dnPVinQLC/user"
}
```

### Initialiser les variables

Remplacez `REPLACEME123@AdobeOrg` par l’ID d’organisation Adobe IMS de votre organisation et exécutez la commande ci-dessous. L’identifiant de sortie de cette commande est appelé `TRANSFORM_IMS_ID`.

```bash
echo "REPLACEME123@AdobeOrg" | sed 's/@AdobeOrg$//' | tr '[:upper:]' '[:lower:]'
```

Saisissez les valeurs de `CUSTOMER`, `CDN_ID`, `ACCT1` et `TRANSFORM_IMS_ID` en suivant les instructions ci-dessous, puis exécutez les commandes à partir de votre terminal.

```bash
export PROFILE1=LLMO
export REGION1=us-east-1
export CUSTOMER=<CUSTOMER_NAME> ## No Space, user letters,numbers and dash
export CDN_ID=<YOUR_CLOUDFRONT_DISTRIBUTION_ID>
export ACCT1=<YOUR_AWS_ACCOUNT_NUMBER>
export DELIVERY_DEST_ARN=arn:aws:logs:us-east-1:640168421876:delivery-destination:cdn-logs-<TRANSFORM_IMS_ID>-ams  ## Replace TRANSFORM_IMS_ID with the output of the command above 
```

<!--Use the **Delivery destination ARN** and org values from the LLM Optimizer CDN configuration page if they differ from the pattern above.-->

### Création de la source de diffusion

À partir du même terminal où l’étape 3 a été exécutée, exécutez la commande ci-dessous :

```bash
aws logs put-delivery-source --name llmo-cf-${CUSTOMER}-${CDN_ID} \
  --profile $PROFILE1 --region $REGION1 \
  --resource-arn arn:aws:cloudfront::${ACCT1}:distribution/${CDN_ID} \
  --log-type ACCESS_LOGS
```

>[!IMPORTANT]
>
>Si vous obtenez l’erreur suivante, recherchez la source de diffusion existante : *Une erreur s’est produite (ConflictException) lors de l’appel de l’opération PutDeliverySource : Cet ResourceId a déjà été utilisé dans un autre Source de diffusion de ce compte.*
>
>Pour rechercher la source de diffusion existante, exécutez la commande suivante :
>
>```bash
>aws logs describe-delivery-sources --region us-east-1 \
>--query "deliverySources[?contains(resourceArns[0], '<CDN DistributionID>')]"
>```
>
>Dans la commande suivante, utilisez le nom de la source de diffusion à partir des résultats de la commande ci-dessus.

### Création de la configuration de diffusion

```bash
aws logs create-delivery \
  --profile "$PROFILE1" --region "$REGION1" \
  --delivery-source-name "llmo-cf-${CUSTOMER}-${CDN_ID}" \
  --delivery-destination-arn $DELIVERY_DEST_ARN \
  --s3-delivery-configuration '{"suffixPath":"/{yyyy}/{MM}/{dd}/{HH}"}' \
  --record-fields 'date' 'time' 'x-edge-location' 'cs-method' 'cs(Host)' 'cs-uri-stem' 'sc-status' 'cs(Referer)' 'cs(User-Agent)' 'time-to-first-byte' 'sc-content-type' 'x-host-header'
```

&lt;!—Alignez `--record-fields` et `--s3-delivery-configuration` sur la liste de champs et le suffixe de chemin affichés sur votre page de configuration du réseau CDN LLM Optimizer si la documentation ou les valeurs du produit changent.—>
