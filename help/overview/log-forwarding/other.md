---
title: 'Transfert de journal : autre (chargement manuel)'
description: Découvrez comment charger manuellement les journaux CDN dans le compartiment S3 Adobe pour la collecte de données de trafic généré par l’IA agentique dans LLM Optimizer lors de l’utilisation d’un fournisseur de CDN non pris en charge.
feature: Agentic Traffic
autotag-review: '2026-07-15T18:08:55.588Z'
TQID: 'https://experienceleague.adobe.com/tuB95AJnFbB4O0o2BYHiRP-W0RTxzMeMLNg-5OjF-8s'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadcid: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: dd952468-5202-43af-a365-6e0d2e67a703id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 670
ht-degree: 100%

---


# Transfert de journal : autre (chargement manuel) {#log-forwarding-other}

La méthode d’approvisionnement **Autre BYOCDN** est une option générique pour les clientes et clients qui souhaitent transmettre des journaux CDN à LLM Optimizer dans les cas suivants :

- Les **chargements manuels** sont recommandés : par exemple, les équipes opérationnelles exportent les journaux et les chargent régulièrement.
- Les **processus automatisés ad hoc** sont utilisés : scripts ponctuels, exportations planifiées, tâches sans serveur.
- Le client ou la cliente utilise un **réseau CDN qui n’est pas pris en charge nativement** par les intégrations de transfert de journaux.

Cette méthode imite le modèle de « transfert continu » : les journaux sont générés et chargés à l’emplacement S3 prévu et sont ensuite traités automatiquement par les pipelines d’ingestion.

## Étape 1 : intégrer dans LLM Optimizer {#step-1}

Dans [LLM Optimizer](https://llmo.now/) :

1. Accédez à **Configuration**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du CDN**.

   ![Onglet Configuration du CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Prise en main**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. À côté de **Activer les informations sur le trafic généré par l’IA**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)

1. Sélectionnez **Autre**.

   ![Sélectionner Autre](/help/overview/assets/log-forwarding/other/other-select.png)

1. Cliquez sur **Intégration**.

<!--   ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Étape 2 : préparation et chargement des journaux {#step-2}

### Format de journal obligatoire (lignes JSON) {#log-format}

Les journaux doivent être chargés au format JSON délimité par des retours à la ligne (**un objet JSON par ligne**). Chaque ligne de journal doit inclure les champs suivants, **écrits avec la même orthographe que celle ci-dessous**.

#### Schéma champ par champ {#schema}

| Champ | Type | Description | Exemple |
|---|---|---|---|
| **timestamp** | Chaîne | La date et l’heure de la demande sont au format **ISO 8601**. | `"2025-02-01T23:00:05Z"` |
| **host** | Chaîne | Domaine web demandé par le client. | `"www.example.com"` |
| **url** | Chaîne | Le **chemin** et les **paramètres de requête** sont requis, mais le domaine ne doit **pas** être inclus. | `"/home?utm_source=google"` |
| **request_method** | Chaîne | Méthode de requête HTTP, parfois appelée verbes HTTP. | `"GET"` |
| **request_user_agent** | Chaîne | En-tête de requête de l’agent utilisateur HTTP. | `"Mozilla/5.0 (compatible; GPTBot/1.0"` |
| **request_referer** | Chaîne | En-tête de requête du référent HTTP (peut être vide). | `"https://chatgpt.com"` |
| **response_status** | Entier | Code de réponse HTTP. | `200` |
| **response_content_type** | Chaîne | En-tête de réponse de type de contenu HTTP. | `"text/html; charset=utf-8"` |
| **time_to_first_byte** | Entier | Temps écoulé entre la création d’une connexion au serveur et le téléchargement du contenu d’une page web, en **millisecondes**. Définissez-le sur zéro si vous ne le connaissez pas ou s’il est n’est pas disponible. | `42` |

#### Exemple de lignes de journal {#example}

L’exemple suivant illustre trois lignes de journal :

```json
{"timestamp":"2025-02-01T23:06:14Z","host":"www.example.com","url":"/products/llm-optimizer?utm_source=google","request_method":"GET","request_user_agent":"Mozilla/5.0 (compatible; GPTBot/1.0; +https://openai.com/gptbot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":198}
{"timestamp":"2025-02-01T23:19:32Z","host":"www.example.com","url":"/services/ai-consulting/overview","request_method":"GET","request_user_agent":"PerplexityBot/1.0 (+https://www.perplexity.ai/perplexitybot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":255}
{"timestamp":"2025-02-01T23:44:05Z","host":"www.example.com","url":"/products/pricing/enterprise?utm_medium=social","request_method":"GET","request_user_agent":"ClaudeBot/1.0 (+https://www.anthropic.com)","response_status":200,"request_referer":"","response_content_type":"application/pdf","time_to_first_byte":312}
```

### Avertissement important (orthographe et types) {#disclaimer}

Les pipelines d’ingestion et d’agrégation sont stricts concernant **les noms de champ et les types de données**.

- Les noms des champs doivent correspondre **exactement** (casse et orthographe).
- Les types de données doivent être corrects comme suit :
   - **timestamp** doit être une chaîne au format **ISO 8601**. Les formats de date UNIX peuvent ne pas fonctionner.
   - **response_status** doit être un nombre entier.
   - **time_to_first_byte** doit être un nombre entier exprimé en millisecondes.
   - Les chaînes doivent être des chaînes JSON valides.
- Si le JSON est mal structuré ou que des champs sont incorrects ou manquants, des journaux peuvent être ignorés et leur analyse peut échouer, auquel cas il manquera des données dans les rapports.

### Emplacement de chargement et cadence de traitement {#upload-location}

#### Règle de chemin {#path-rule}

Chargez les journaux dans le chemin d’accès au dossier approprié en utilisant le format **`yyyy/mm/dd/`** (avec des barres obliques).

Exemple de journal du 1er février 2025 UTC : `ABC123AdobeOrg/raw/byocdn-other/2025/02/01/`

#### Règle de traitement {#processing-rule}

- Les journaux chargés au cours d’un **jour UTC** sont traités par les pipelines **vers la fin de ce jour UTC** (exécution quotidienne).
- Les journaux chargés dans les **dossiers des jours précédents** (renvoi) sont **détectés et traités** dans les 24 heures.

## Scénarios {#scenarios}

### Scénario 1 : journaux dans Splunk/Elasticsearch, exportation et chargement vers S3 {#scenario-splunk}

**Objectif** : récupérer les journaux des plateformes d’observabilité existantes et les transférer vers l’emplacement S3.

- Extrayez les champs requis des événements de recherche Splunk/Elastic.
- Transformez chaque événement en un objet JSON en suivant le schéma ci-dessus (lignes JSON).
- Chargez le(s) fichier(s) obtenu(s) dans le compartiment S3 désigné et le chemin du **jour UTC actuel** : `…/byocdn-other/yyyy/mm/dd/`
- Les journaux seront traités automatiquement à la fin de la journée UTC.

### Scénario 2 : fonction Lambda/Azure, format et chargement vers S3 {#scenario-serverless}

**Objectif** : utilisez le calcul sans serveur pour récupérer/recevoir les journaux CDN, les normaliser et les transférer vers l’emplacement S3.

- La fonction récupère les journaux à partir de la source du client (banque de journaux, file d’attente, stockage d’objets blob, etc.).
- La fonction mappe les champs dans le schéma attendu et émet des **lignes JSON**.
- La fonction charge la sortie vers `…/byocdn-other/yyyy/mm/dd/`.
- Les journaux seront traités automatiquement à la fin de la journée UTC.

## Liste de contrôle rapide {#checklist}

- **Un objet JSON par ligne** (lignes JSON)
- **Orthographe exacte des champs** telle que spécifiée
- Types de données corrects
- **time_to_first_byte** en millisecondes (nombre entier)
- Chargez le fichier dans le dossier UTC approprié : **aaaa/mm/jj/** sous **byocdn-other**.
