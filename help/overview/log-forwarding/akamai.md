---
title: Transfert de journal - Akamai
description: Découvrez comment transférer les journaux CDN d’Akamai vers le compartiment S3 Adobe pour la collecte de données de trafic agentic dans LLM Optimizer.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Transfert de journal : Akamai {#log-forwarding-akamai}

Cette page explique comment transférer les journaux CDN d’Akamai vers le compartiment S3 d’Adobe pour la collecte de données de trafic agentic. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour vous intégrer à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes présentées sur cette page pour configurer le transfert des journaux dans le Panneau de Contrôle Akamai.

## Étape 1 : intégration dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez au **Tableau de bord de configuration du client**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du réseau CDN**.

   ![Onglet Configuration du réseau CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Commencer**.

   <!--![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. En regard de **Activer AI Traffic Insights**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)

1. Sélectionnez **Akamai (BYOCDN)**.

   ![Sélectionner Akamai](/help/overview/assets/log-forwarding/akamai/akamai-select.png)

1. Cliquez sur **Intégration**.

   <!--![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Étape 2 : créer un flux dans Akamai {#step-2}

Sur le panneau de contrôle Akamai [https://control.akamai.com/](https://control.akamai.com/) suivez les étapes de la documentation officielle d’Akamai pour [créer un flux](https://techdocs.akamai.com/datastream2/docs/create-stream).

## Etape 3 : sélection des paramètres de données {#step-3}

Après avoir créé le flux, dans le panneau de contrôle Akamai, cliquez sur Suivant pour passer à l’onglet **Jeux de données**. Suivez les étapes de la documentation officielle d’Akamai pour choisir les [paramètres de données](https://techdocs.akamai.com/datastream2/docs/choose-data-parameters). Les champs suivants de la configuration LLM Optimizer seront nécessaires :

![champs de configuration LLMO](/help/overview/assets/log-forwarding/akamai/akamai-llmo-config-fields.png)

Le mapping doit être le suivant :

* **Informations sur le journal**
reqTimeSec -> Heure de la demande
* **Données géographiques**
pays -> Pays/zone géographique
* **Données d’échange de messages**
reqHost -> Hôte de requête
reqPath -> Chemin d’accès à la requête
queryStr -> Chaîne de requête
reqMethod -> Méthode de requête
ua -> User-Agent
statusCode -> Code d’état HTTP
rspContentType -> Type de contenu de réponse
* **Données d’en-tête de requête**
Référent -> Référent
* **Données de performances réseau**
timeToFirstByte -> Délai du premier octet

Les champs du jeu de données Akamai (y compris les identifiants) sont les suivants :

1100, # reqTimeSec -> Heure de la requête
2012, # pays -> Pays/Région
1011, # reqHost -> Hôte de requête
1013, # reqPath -> Chemin de la requête
2009, # queryStr -> Chaîne de requête
1012, # reqMethod -> Méthode de requête
1017, # ua -> User-Agent
1008, # statusCode -> Code d’état HTTP
1032, # référent -> Référent
1016, # rspContentType -> Type de contenu de réponse
2025 # timeToFirstByte -> Délai du premier octet

## Étape 4 : configurer la destination {#step-4}

Après avoir créé les flux de données et choisi les paramètres, vous devez configurer la destination. Pour configurer la destination, procédez comme suit :

1. Dans **Destination**, sélectionnez **S3**.
2. Dans **Nom**, saisissez une description lisible par l’utilisateur de la destination.
3. Dans **Compartiment**, copiez le **Nom du compartiment** à partir de la page de configuration de LLM Optimizer.

   ![Nom du compartiment](/help/overview/assets/log-forwarding/common/bucket-name.png)

4. Dans **Chemin du dossier**, copiez le **Chemin** de la page de configuration de LLM Optimizer.

   ![Configuration du chemin](/help/overview/assets/log-forwarding/akamai/akamai-path-config.png)

5. Dans **Region**, copiez le **Region** à partir de la page de configuration LLM Optimizer.

   <!--![Region](/help/overview/assets/log-forwarding/common/region.png)-->

6. Dans **ID de clé d’accès** et **Clé d’accès secrète**, copiez les deux valeurs à partir de la page de configuration de LLM Optimizer.

   ![Clés d’accès](/help/overview/assets/log-forwarding/common/access-keys.png)

7. Cliquez sur **Valider et enregistrer** pour valider la connexion à la destination et enregistrer les détails que vous avez fournis. Dans le cadre de ce processus de validation, le système utilise l’identifiant de clé d’accès et la clé d’accès secrète fournis pour créer un fichier de vérification dans votre dossier S3, avec un horodatage au format `Akamai_access_verification_[TimeStamp].txt` dans le nom du fichier. Ce fichier n’est visible que si le processus de validation a réussi et que vous avez accès au compartiment et au dossier Amazon S3 vers lesquels vous tentez d’envoyer des journaux.

8. Dans le menu **Options de diffusion** modifiez le champ **Nom de fichier** comme suit :

   a. Modifiez le **préfixe**. Copiez la valeur de la page de configuration de LLM Optimizer sous **Préfixe du fichier journal** :

   ```
   {%Y}-{%m}-{%d}T{%H}:{%M}:{%S}.000
   ```

   b. Modifiez le **suffixe**. Copiez la valeur de la page de configuration de LLM Optimizer sous **Suffixe du fichier journal**.

9. Modifiez la **Fréquence des notifications push**. Copiez la valeur de la page de configuration de LLM Optimizer sous **Intervalle de journal**.

   ![Intervalle de journal](/help/overview/assets/log-forwarding/akamai/akamai-log-interval.png)

10. Cliquez sur **Suivant** pour terminer le processus.

Avant la validation finale, la configuration doit ressembler à cet exemple :

![ Validation de la configuration ](/help/overview/assets/log-forwarding/akamai/akamai-validation.png)
