---
title: Transfert de journal - Imperva
description: Découvrez comment transférer les journaux CDN d’Imperva vers le compartiment Adobe S3 pour la collecte de données de trafic agentic dans LLM Optimizer.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 5%

---


# Transfert de journal : Imperva {#log-forwarding-imperva}

Ce guide explique comment transférer les journaux CDN d’Imperva vers le compartiment S3 Adobe pour la collecte de données de trafic agentic. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour vous intégrer à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes fournies sur cette page pour configurer le transfert des journaux à partir de la console web Imperva.

## Étape 1 : intégration dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez à **Configuration**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du réseau CDN**.

   ![Onglet Configuration du réseau CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)
1. Cliquez sur **Commencer**.
1. En regard de **Activer AI Traffic Insights**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)
1. Sélectionnez **Imperva (BYOCDN)**.

   ![Sélectionnez Imperva](/help/overview/assets/log-forwarding/imperva/imperva-select.png)
1. Cliquez sur **Intégration**.

## Étape 2 : Configurer le transfert du journal dans Imperva {#step-2}

Sur la console [Imperva](https://my.imperva.com) :

>[!NOTE]
>
>Les journaux doivent être envoyés quotidiennement.

1. Connectez-vous à votre compte Imperva sur [https://my.imperva.com](https://my.imperva.com).

2. Dans la barre latérale, accédez à **Journaux** > **Configuration du journal** (ou **Intégration du journal**).

3. Sélectionnez **Amazon S3 ARN** comme type de connexion (destination du journal).

4. Entrez la commande suivante :

   | Champ | Description | Remarque |
   |---|---|---|
   | **Nom de la connexion** | Nom explicite de la connexion (par exemple, journaux S3 de production). Vous pouvez renommer la valeur par défaut. | |
   | **Chemin** | Emplacement du dossier dans lequel les fichiers journaux seront stockés. Utilisez le format `<Amazon S3 bucket name>/<log folder>`. Par exemple : `MyBucket/MyImpervaLogFolder`. | `Amazon S3 bucket name` est le **nom du compartiment** de la page de configuration de LLM Optimizer. ![Nom du compartiment &#x200B;](/help/overview/assets/log-forwarding/imperva/imperva-bucket-name.png) le dossier du journal est **Chemin** à partir de la page de configuration de LLM Optimizer. ![Chemin &#x200B;](/help/overview/assets/log-forwarding/imperva/imperva-path.png) |

5. Cliquez sur **Tester la connexion**. Imperva exécute un test complet dans lequel un fichier de test (aucune donnée réelle) est envoyé au dossier désigné, puis supprimé une fois le transfert terminé.

   - **Disponible** — les informations de stockage sont valides ; vous pouvez configurer les journaux pour utiliser cette connexion.
   - **Non défini** — Les détails requis sont manquants ou le test a échoué.

6. Cliquez sur **Enregistrer** pour stocker la configuration.

7. Configurez les options du journal (types de journal, niveau de journal, format, compression) et **Niveaux de journal**. Vous pouvez obtenir les valeurs à partir de la page de configuration de LLM Optimizer.

   | Champ | Remarque |
   |---|---|
   | Mode d’intégration du journal | ![Mode d’intégration du journal](/help/overview/assets/log-forwarding/imperva/imperva-log-integration-mode.png) |
   | Méthode d’envoi | ![Méthode de diffusion](/help/overview/assets/log-forwarding/imperva/imperva-delivery-method.png) |
   | Types de logs | ![Types de journaux](/help/overview/assets/log-forwarding/imperva/imperva-log-types.png) |
   | Niveau de journal | ![Niveau de log](/help/overview/assets/log-forwarding/imperva/imperva-log-level.png) |
   | Format | ![Format](/help/overview/assets/log-forwarding/imperva/imperva-format.png) |
   | Compresser les journaux | ![Compresser les journaux](/help/overview/assets/log-forwarding/imperva/imperva-compress-logs.png) |
