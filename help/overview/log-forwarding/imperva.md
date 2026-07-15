---
title: 'Transfert de journaux : Imperva'
description: Découvrez comment transférer les journaux CDN d’Imperva vers le compartiment S3 d’Adobe pour la collecte de données de trafic généré par l’IA agentique dans LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:57:30.264Z'
TQID: 'https://experienceleague.adobe.com/l-DYz7pXzFDqZn1rnZWUOG9PpRqosq00LmGrlsOMqNk'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3aid: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: dd952468-5202-43af-a365-6e0d2e67a703id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 352
ht-degree: 100%

---


# Transfert de journaux : Imperva {#log-forwarding-imperva}

Ce guide explique comment transférer les journaux CDN d’Imperva vers le compartiment S3 d’Adobe pour la collecte de données de trafic généré par l’IA agentique. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour l’intégration à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes indiquées sur cette page pour configurer le transfert des journaux à partir de la console web d’Imperva.

## Étape 1 : intégrer dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez à **Configuration**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du CDN**.

   ![Onglet Configuration du CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)
1. Cliquez sur **Prise en main**.
1. À côté de **Activer les informations sur le trafic généré par l’IA**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)
1. Sélectionnez **Imperva (BYOCDN)**.

   ![Sélectionner Imperva](/help/overview/assets/log-forwarding/imperva/imperva-select.png)
1. Cliquez sur **Intégration**.

## Étape 2 : configurer le transfert des journaux dans Imperva {#step-2}

Dans la [console Imperva](https://my.imperva.com) :

>[!NOTE]
>
>Les journaux doivent être envoyés quotidiennement.

1. Connectez-vous à votre compte Imperva sur [https://my.imperva.com](https://my.imperva.com).

2. Dans la barre latérale, allez à&#x200B;**Journaux** > **Configuration des journaux** (ou **Intégration des journaux**).

3. Sélectionnez **ARN Amazon S3** comme type de connexion (destination du journal).

4. Entrez la commande suivante :

   | Champ | Description | Remarque |
   |---|---|---|
   | **Nom de la connexion** | Nom explicite pour la connexion (par exemple, Journaux S3 de production). Vous pouvez changer le nom par défaut. | |
   | **Chemin** | Emplacement du dossier où seront stockés les fichiers journaux. Utilisez le format `<Amazon S3 bucket name>/<log folder>`. Par exemple : `MyBucket/MyImpervaLogFolder`. | `Amazon S3 bucket name` est le **nom du compartiment** de la page de configuration de LLM Optimizer. ![Nom du compartiment](/help/overview/assets/log-forwarding/imperva/imperva-bucket-name.png) Le dossier de journaux correspond au **chemin** indiqué sur la page de configuration de LLM Optimizer. ![Chemin](/help/overview/assets/log-forwarding/imperva/imperva-path.png) |

5. Cliquez sur **Tester la connexion**. Imperva effectue un test complet au cours duquel un fichier de test (sans données réelles) est envoyé dans le dossier désigné, puis supprimé une fois le transfert terminé.

   - **Disponible** — Les informations de stockage sont valides ; vous pouvez configurer les journaux pour utiliser cette connexion.
   - **Non défini** — Soit les détails requis sont manquants, soit le test a échoué.

6. Cliquez sur **Enregistrer** pour enregistrer la configuration.

7. Configurez les options de journalisation (types de journalisation, niveau de journalisation, format, compression) et les **niveaux de journalisation**. Les valeurs sont disponibles sur la page de configuration de LLM Optimizer.

   | Champ | Remarque |
   |---|---|
   | Mode d’intégration des journaux | ![Mode d’intégration des journaux](/help/overview/assets/log-forwarding/imperva/imperva-log-integration-mode.png) |
   | Mode de diffusion | ![Mode de diffusion](/help/overview/assets/log-forwarding/imperva/imperva-delivery-method.png) |
   | Types de journaux | ![Types de journaux](/help/overview/assets/log-forwarding/imperva/imperva-log-types.png) |
   | Niveau de journal | ![Niveau de journalisation](/help/overview/assets/log-forwarding/imperva/imperva-log-level.png) |
   | Format | ![Format](/help/overview/assets/log-forwarding/imperva/imperva-format.png) |
   | Comprimer les journaux | ![Compresser les journaux](/help/overview/assets/log-forwarding/imperva/imperva-compress-logs.png) |
