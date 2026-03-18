---
title: Transfert de journal - Autre (chargement manuel)
description: Découvrez comment charger manuellement les journaux CDN dans le compartiment S3 Adobe pour la collecte de données de trafic agentic dans LLM Optimizer lors de l’utilisation d’un fournisseur de réseau CDN non pris en charge.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---


# Transfert de journal : autre (chargement manuel) {#log-forwarding-other}

La méthode d’approvisionnement **Autre BYOCDN** est une option fourre-tout pour les clients qui souhaitent fournir des journaux CDN à LLM Optimizer lorsque :

- Les **chargements manuels** sont recommandés ; par exemple, les équipes opérationnelles exportent les journaux et les chargent régulièrement.
- Les **processus automatisés ad hoc** sont utilisés : scripts uniques, exportations planifiées, tâches sans serveur.
- Le client utilise un **réseau CDN qui n’est pas pris en charge nativement** par les intégrations de transfert de journal intégrées.

Cette méthode imite le modèle de « transfert continu » : les journaux sont générés et chargés à l’emplacement S3 prévu et sont finalement traités automatiquement par les pipelines d’ingestion.

## Étape 1 : intégration dans LLM Optimizer {#step-1}

Sous [LLM Optimizer](https://llmo.now/) :

1. Accédez à **Configuration**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du réseau CDN**.

   ![Onglet Configuration du réseau CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Commencer**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. En regard de **Activer AI Traffic Insights**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)

1. Sélectionnez **Autre**.

   ![Sélectionner autre](/help/overview/assets/log-forwarding/other/other-select.png)

1. Cliquez sur **Intégration**.

<!--   ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Étape 2 : préparation et chargement des journaux {#step-2}

### Format de journal obligatoire (lignes JSON) {#log-format}

Les journaux doivent être chargés au format JSON délimité par une nouvelle ligne (**un objet JSON par ligne**). Chaque ligne de journal doit inclure les champs suivants **exactement comme orthographié ci-dessous**.

#### Schéma champ par champ {#schema}

| Champ | Type | Description | Exemple |
|---|---|---|---|
| **timestamp** | Chaîne | Date et heure de la requête au format **ISO 8601**. | `"2025-02-01T23:00:05Z"` |
| **host** | Chaîne | Domaine web demandé par le client. | `"www.example.com"` |
| **url** | Chaîne | Le **chemin** et les **paramètres de requête** sont requis, tandis que le domaine ne doit **pas** être inclus. | `"/home?utm_source=google"` |
| **request_method** | Chaîne | Méthode de requête HTTP, parfois appelée verbes HTTP. | `"GET"` |
| **request_user_agent** | Chaîne | En-tête de requête Agent-utilisateur HTTP. | `"Mozilla/5.0 (compatible; GPTBot/1.0"` |
| **request_referer** | Chaîne | L’en-tête de requête du référent HTTP (peut être vide). | `"https://chatgpt.com"` |
| **response_status** | Entier | Code de statut de la réponse HTTP. | `200` |
| **response_content_type** | Chaîne | En-tête de réponse de type contenu HTTP. | `"text/html; charset=utf-8"` |
| **time_to_first_byte** | Entier | Temps écoulé entre la création d’une connexion au serveur et le téléchargement du contenu d’une page web, en **millisecondes**. Définissez-le sur zéro s’il est inconnu ou indisponible. | `42` |

#### Exemples de lignes de journal {#example}

L’exemple suivant illustre trois lignes de journal :

```json
{"timestamp":"2025-02-01T23:06:14Z","host":"www.example.com","url":"/products/llm-optimizer?utm_source=google","request_method":"GET","request_user_agent":"Mozilla/5.0 (compatible; GPTBot/1.0; +https://openai.com/gptbot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":198}
{"timestamp":"2025-02-01T23:19:32Z","host":"www.example.com","url":"/services/ai-consulting/overview","request_method":"GET","request_user_agent":"PerplexityBot/1.0 (+https://www.perplexity.ai/perplexitybot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":255}
{"timestamp":"2025-02-01T23:44:05Z","host":"www.example.com","url":"/products/pricing/enterprise?utm_medium=social","request_method":"GET","request_user_agent":"ClaudeBot/1.0 (+https://www.anthropic.com)","response_status":200,"request_referer":"","response_content_type":"application/pdf","time_to_first_byte":312}
```

### Clause de non-responsabilité critique (orthographe et types) {#disclaimer}

Les pipelines d’ingestion et d’agrégation sont stricts en ce qui concerne **les noms de champ et les types de données**.

- Les noms des champs doivent correspondre **exactement** (casse et orthographe).
- Les types de données doivent être corrects, comme suit :
   - **timestamp** doit être une chaîne au format **ISO 8601**. Les horodatages de type UNIX peuvent ne pas fonctionner.
   - **response_status** doit être un entier.
   - **time_to_first_byte** doit être un entier et utiliser des millisecondes.
   - Les chaînes doivent être des chaînes JSON valides.
- Des champs JSON incorrects ou manquants/incorrects peuvent entraîner l’omission ou l’échec de l’analyse des journaux, ce qui entraîne l’absence de données dans les rapports.

### Emplacement de chargement et cadence de traitement {#upload-location}

#### Règle de chemin {#path-rule}

Chargez les journaux dans le chemin d’accès au dossier approprié au format : **`yyyy/mm/dd/`** (avec des barres obliques).

Exemple de journal depuis le 1er février 2025 UTC : `ABC123AdobeOrg/raw/byocdn-other/2025/02/01/`

#### Règle de traitement {#processing-rule}

- Les journaux chargés au cours d’un **jour UTC** donné sont traités par les pipelines **vers la fin de ce jour UTC** (exécution quotidienne).
- Les journaux chargés dans les **dossiers des jours précédents** (renvoi) sont **détectés et traités** dans les 24 heures.

## Scénarios {#scenarios}

### Scénario 1 : Journaux dans Splunk/Elasticsearch - exportation et chargement vers S3 {#scenario-splunk}

**Objectif** : récupérer les journaux des plateformes d’observabilité existantes et les diffuser à l’emplacement S3.

- Extrayez les champs requis des événements de recherche Splunk/Elastic.
- Transformez chaque événement en un objet JSON en suivant le schéma ci-dessus (lignes JSON).
- Chargez le(s) fichier(s) obtenu(s) dans le compartiment S3 désigné et le chemin **jour UTC actuel** : `…/byocdn-other/yyyy/mm/dd/`
- Les journaux seront traités automatiquement à la fin de la journée UTC.

### Scénario 2 : fonction Lambda/Azure — format et chargement vers S3 {#scenario-serverless}

**Objectif** : utilisez un calcul sans serveur pour récupérer/recevoir les journaux du réseau CDN, les normaliser et les diffuser à l’emplacement S3.

- La fonction récupère les journaux à partir de la source du client (banque de journaux, file d’attente, stockage d’objets blob, etc.).
- La fonction mappe les champs dans le schéma attendu et émet des **Lignes JSON**.
- La fonction charge la sortie vers : `…/byocdn-other/yyyy/mm/dd/`
- Les journaux seront traités automatiquement à la fin de la journée UTC.

## Liste de contrôle rapide {#checklist}

- **Un objet JSON par ligne** (lignes JSON)
- **Orthographe exacte du champ** tel que spécifié
- Types de données corrects
- **time_to_first_byte** en millisecondes (entier)
- Chargez le fichier dans le dossier UTC approprié : **aaaa/mm/jj/** sous **byocdn-autre**.
