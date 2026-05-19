---
title: Transfert de journaux - Akamai
description: Découvrez comment transférer des journaux de CDN d’Akamai vers le compartiment S3 d’Adobe pour la collecte de données du trafic généré par l’IA agentique dans LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:35:22.816Z'
TQID: 'https://experienceleague.adobe.com/cO-qqOveWFee1-QnVSlzmO-n383sptHl59Ni2qQcvAU'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 595
ht-degree: 100%

---


# Transfert de journaux : Akamai {#log-forwarding-akamai}

Cette page explique comment transférer des journaux de CDN d’Akamai vers le compartiment S3 d’Adobe pour la collecte de données du trafic généré par l’IA agentique. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour l’intégration à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes détaillées sur cette page pour configurer le transfert des journaux dans le panneau de configuration d’Akamai.

## Étape 1 : intégrer dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez au **tableau de bord de la configuration cliente**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du CDN**.

   ![Onglet Configuration du CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Prise en main**.

   <!--![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. À côté de **Activer les informations sur le trafic généré par l’IA**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)

1. Sélectionnez **Akamai (BYOCDN)**.

   ![Sélectionnez Akamai](/help/overview/assets/log-forwarding/akamai/akamai-select.png)

1. Cliquez sur **Intégration**.

   <!--![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Étape 2 : créer un flux dans Akamai {#step-2}

Dans le panneau de configuration d’Akamai [https://control.akamai.com/](https://control.akamai.com/), suivez les étapes de la documentation officielle d’Akamai pour [créer un flux](https://techdocs.akamai.com/datastream2/docs/create-stream).

## Étape 3 : sélectionner les paramètres des données {#step-3}

Après avoir créé le flux, dans le panneau de configuration d’Akamai, cliquez sur Suivant pour poursuivre vers l’onglet **Jeux de données**. Suivez les étapes de la documentation officielle d’Akamai pour sélectionner les [paramètres des données](https://techdocs.akamai.com/datastream2/docs/choose-data-parameters). Les champs suivants issus de la configuration de LLM Optimizer seront nécessaires :

![Champs de configuration de LLMO](/help/overview/assets/log-forwarding/akamai/akamai-llmo-config-fields.png)

Le mapping doit être effectué comme suit :

* **Informations de journalisation**
reqTimeSec -> Heure de la requête
* **Données géographiques**
country -> Pays/Région géographique
* **Données d’échange des messages**
reqHost -> Hôte de la requête
reqPath -> Chemin de la requête
queryStr -> Chaîne de requête
reqMethod -> Méthode de requête
ua -> Agent utilisateur
statusCode -> Code d’état HTTP
rspContentType -> Type de contenu de la réponse
* **Données d’en-tête de requête**
referer -> Référent
* **Données de performances du réseau**
timeToFirstByte -> Time To First Byte

Les champs de jeux de données Akamai (y compris les identifiants) sont les suivants :

1100, # reqTimeSec -> Heure de la demande
2012, # country -> Pays/Région géographique
1011, # reqHost -> Hôte de la requête
1013, # reqPath -> Chemin de la requête
2009, # queryStr -> Chaîne de requête
1012, # reqMethod -> Méthode de requête
1017, # ua -> Agent utilisateur
1008, # statusCode -> Code d’état HTTP
1032, # referer -> Référent
1016, # rspContentType -> Type de contenu de la réponse
2025  # timeToFirstByte -> Time To First Byte

## Étape 4 : configurer la destination {#step-4}

Après avoir créé les flux de données et choisi les paramètres, vous devez configurer la destination. Pour configurer la destination, procédez comme suit :

1. Dans **Destination**, sélectionnez **S3**.
2. Dans **Nom**, entrez une description lisible et compréhensible pour la destination.
3. Dans **Compartiment**, copiez le **Nom du compartiment** à partir de la page de configuration de LLM Optimizer.

   ![Nom du compartiment](/help/overview/assets/log-forwarding/common/bucket-name.png)

4. Dans **Chemin du dossier**, copiez le **Chemin** à partir de la page de configuration de LLM Optimizer.

   ![Configuration du chemin](/help/overview/assets/log-forwarding/akamai/akamai-path-config.png)

5. Dans **Région**, copiez la **Région** à partir de la page de configuration de LLM Optimizer.

   <!--![Region](/help/overview/assets/log-forwarding/common/region.png)-->

6. Dans **Identifiant de clé d’accès** et **Clé d’accès secrète**, copiez les deux valeurs à partir de la page de configuration de LLM Optimizer.

   ![Clés d’accès](/help/overview/assets/log-forwarding/common/access-keys.png)

7. Cliquez sur **Valider et enregistrer** pour valider la connexion à la destination et enregistrer les détails que vous avez renseignés. Dans le cadre de ce processus de validation, le système utilise l’identifiant de clé d’accès et la clé d’accès secrète fournis pour créer un fichier de vérification dans votre dossier S3, avec un horodatage au format `Akamai_access_verification_[TimeStamp].txt` inclus dans le nom du fichier. Ce fichier n’est visible que si le processus de validation a réussi et que vous avez accès au compartiment et au dossier Amazon S3 vers lesquels vous tentez d’envoyer des fichiers journaux.

8. Dans le menu **Options de diffusion**, modifiez le champ **Nom de fichier** comme suit :

   a. Modifiez le **préfixe**. Copiez la valeur à partir de la page de configuration de LLM Optimizer, dans **Préfixe du fichier journal** :

   ```
   {%Y}-{%m}-{%d}T{%H}:{%M}:{%S}.000
   ```

   b. Modifiez le **suffixe**. Copiez la valeur à partir de la page de configuration de LLM Optimizer, dans **Suffixe du fichier journal**.

9. Modifiez la **Fréquence d’envoi**. Copiez la valeur à partir de la page de configuration de LLM Optimizer, dans **Intervalle de journalisation**.

   ![Intervalle de journalisation](/help/overview/assets/log-forwarding/akamai/akamai-log-interval.png)

10. Cliquez sur **Suivant** pour terminer le processus.

Avant la validation finale, la configuration doit ressembler à cet exemple :

![Validation de la configuration](/help/overview/assets/log-forwarding/akamai/akamai-validation.png)
