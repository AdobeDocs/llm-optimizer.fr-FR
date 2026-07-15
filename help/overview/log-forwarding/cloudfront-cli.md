---
title: Transfert de journaux - CloudFront (interface de ligne de commande AWS)
description: Transférez les journaux du CDN CloudFront vers le compartiment S3 d’Adobe en utilisant l’interface de ligne de commande AWS pour la configuration et les opérations de diffusion.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:46:48.888Z'
TQID: 'https://experienceleague.adobe.com/g3et1xycA6wCBl6hZ8CPVG9i0IppDN-SashlekY6pNM'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e69d5a42-0217-4ca5-9396-a9a826a170daid: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 379
ht-degree: 100%

---


# Transfert de journaux : CloudFront (interface de ligne de commande AWS) {#log-forwarding-cloudfront-cli}

Cette page explique comment transférer les journaux CDN de CloudFront vers le compartiment S3 d’Adobe pour la collecte de données du trafic généré par l’IA agentique. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour l’intégration à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes fournies sur cette page pour configurer le transfert des journaux à l’aide de l’[interface de ligne de commande AWS](https://aws.amazon.com/cli/) à l’[étape 2](#step-2-cli).

>[!NOTE]
>
> Ce guide explique comment configurer le transfert de journaux à l’aide de l’[interface de ligne de commande AWS](https://aws.amazon.com/cli/). Si vous souhaitez configurer le transfert de journaux à l’aide de l’**interface d’utilisation de CloudFront**, consultez [Transfert de journaux : CloudFront](/help/overview/log-forwarding/cloudfront.md).

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

<!--  ![AWS Account ID](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)-->

1. Sélectionnez **CloudFront (BYOCDN)**.

   ![Sélectionner CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Cliquez sur **Intégration**.

<!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Étape 2 : configurer le transfert de journaux du CDN avec l’interface de ligne de commande AWS {#step-2-cli}

Configurez le transfert de journaux du CDN avec l’interface de ligne de commande AWS comme suit :

### Configurer les informations d’identification de l’interface de ligne de commande AWS

Configurez le MAC de l’interface de ligne de commande AWS. Ouvrez ~/.aws/credentials et saisissez les valeurs des variables ci-dessous :

```text
[LLMO]
aws_access_key_id=<VALUE_OF_ACCESS_KEY_ID>
aws_secret_access_key=<VALUE_OF_SECRET_KEY>
aws_session_token=<ONLY_IF_USING_SECURITY_TOKEN_SERVICE> ## Optional
```

### Tester la connexion

Exécutez la commande ci-dessous pour tester la connexion :

```bash
aws sts get-caller-identity --profile LLMO
```

Exemple de sortie correcte :

```bash
aws sts get-caller-identity --profile LLMO
{
    "UserId": "AxxxxxxxxxxxP:user",
    "Account": "012345678912",
    "Arn": "arn:aws:sts::012345678912:assumed-role/klam-master-role-BatlY3dnPVinQLC/user"
}
```

### Initialiser les variables

Remplacez `REPLACEME123@AdobeOrg` par votre identifiant d’organisation Adobe IMS et exécutez la commande ci-dessous. L’identifiant de sortie de cette commande est appelé `TRANSFORM_IMS_ID`.

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
export DELIVERY_DEST_ARN=arn:aws:logs:us-east-1:640168421876:delivery-destination:cdn-logs-<TRANSFORM_IMS_ID>  ## Replace TRANSFORM_IMS_ID with the output of the command above
```

<!--Use the **Delivery destination ARN** and org values from the LLM Optimizer CDN configuration page if they differ from the pattern above.-->

### Créer la source de diffusion

À partir du même terminal que celui utilisé pour l’étape 3, exécutez la commande ci-dessous :

```bash
aws logs put-delivery-source --name llmo-cf-${CUSTOMER}-${CDN_ID} \
  --profile $PROFILE1 --region $REGION1 \
  --resource-arn arn:aws:cloudfront::${ACCT1}:distribution/${CDN_ID} \
  --log-type ACCESS_LOGS
```

>[!IMPORTANT]
>
>Si vous obtenez l’erreur suivante, recherchez la source de diffusion existante : *Une erreur s’est produite (ConflictException) lors de l’appel de l’opération PutDeliverySource : ce ResourceId a déjà été utilisé dans une autre source de diffusion de ce compte.*
>
>Pour rechercher la source de diffusion existante, exécutez la commande suivante :
>
>```bash
>aws logs describe-delivery-sources --region us-east-1 \
>--query "deliverySources[?contains(resourceArns[0], '<CDN DistributionID>')]"
>```
>
>Dans la commande suivante, utilisez le nom de la source de diffusion à partir des résultats de la commande ci-dessus.

### Créer la configuration de diffusion

```bash
aws logs create-delivery \
  --profile "$PROFILE1" --region "$REGION1" \
  --delivery-source-name "llmo-cf-${CUSTOMER}-${CDN_ID}" \
  --delivery-destination-arn $DELIVERY_DEST_ARN \
  --s3-delivery-configuration '{"suffixPath":"/{yyyy}/{MM}/{dd}/{HH}"}' \
  --record-fields 'date' 'time' 'x-edge-location' 'cs-method' 'cs(Host)' 'cs-uri-stem' 'sc-status' 'cs(Referer)' 'cs(User-Agent)' 'time-to-first-byte' 'sc-content-type' 'x-host-header'
```

&lt;!--Alignez `--record-fields` et `--s3-delivery-configuration` sur la liste des champs et le suffixe de chemin affichés sur votre page de configuration de CDN LLM Optimizer si la documentation ou les valeurs du produit changent.-->
