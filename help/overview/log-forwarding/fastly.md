---
title: Transfert de journaux - Fastly
description: Découvrez comment transférer les journaux CDN de Fastly vers le compartiment S3 Adobe pour la collecte de données de trafic généré par l’IA agentique dans LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:51:11.580Z'
TQID: 'https://experienceleague.adobe.com/HPUxzfbvA4DtdNmjgTMvVVv-WqtjPcAUeZmg8JdvL-s'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 381
ht-degree: 100%

---


# Transfert de journaux : Fastly {#log-forwarding-fastly}

Cette page explique comment transférer les journaux CDN de Fastly vers le compartiment S3 d’Adobe pour la collecte de données de trafic généré par l’IA agentique. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour l’intégration à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes fournies sur cette page pour configurer le transfert des journaux dans la console web Fastly.

## Étape 1 : intégrer dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez à **Configuration**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du CDN**.

   ![Onglet Configuration du CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Prise en main**.
1. À côté de **Activer les informations sur le trafic généré par l’IA**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)
1. Sélectionnez **Fastly (BYOCDN)**.

   ![Sélectionnez Fastly.](/help/overview/assets/log-forwarding/fastly/fastly-select.png)
1. Cliquez sur **Intégration**.

## Étape 2 : Créer un point d’entrée S3 dans Fastly {#step-2}

Pour créer un point d’entrée S3, sur le **panneau de Contrôle Fastly** :

1. Dans le tableau de bord Fastly, accédez à **Services CDN** (et non aux Services de calcul).
1. Dans la zone **Amazon Web Services S3**, cliquez sur **Créer un point d’entrée**.
1. Renseignez les champs **Créer un point d’entrée Amazon S3** :

| Champ | Description |
| --- | --- |
| **Nom** | Nom lisible par l’utilisateur ou l’utilisatrice du point d’entrée. |
| **Placement** | Par défaut |
| **Format du journal** | Utilisez la chaîne de format du journal indiquée dans la section **Chaîne de format du journal** ci-dessous. |
| **Format de date et heure** | `%Y-%m-%dT%H:%M:%S.000` |
| **Nom du compartiment** | Copiez le **nom du compartiment** de la page de configuration de LLM Optimizer. ![Nom du compartiment](/help/overview/assets/log-forwarding/fastly/fastly-bucket-name.png) |
| **Domaine** | Copiez le **Nom de domaine** de la page de configuration de LLM Optimizer. ![Nom du domaine](/help/overview/assets/log-forwarding/fastly/fastly-domain-name.png) |
| **Méthode d’accès** | **Identifiants d’utilisation** |
| **Identifiants d’utilisation** | Copiez la **clé d’accès** et la **clé secrète** de la page de configuration de LLM Optimizer. ![Clés d’accès](/help/overview/assets/log-forwarding/common/access-keys.png) |
| **Période** | `300` |

**Chaîne de format des journaux :**

```json
{ "timestamp": "%{strftime(\{"%Y-%m-%dT%H:%M:%S%z"\}, time.start)}V", "host": "%{if(req.http.Fastly-Orig-Host, req.http.Fastly-Orig-Host, req.http.Host)}V", "url": "%{json.escape(req.url)}V", "request_method": "%{json.escape(req.method)}V", "request_referer": "%{json.escape(req.http.referer)}V", "request_user_agent": "%{json.escape(req.http.User-Agent)}V", "response_status": %{resp.status}V, "response_content_type": "%{json.escape(resp.http.Content-Type)}V", "client_country_code": "%{client.geo.country_name}V", "time_to_first_byte": "%{time.to_first_byte}V" }
```

>[!WARNING]
>
>Les gestionnaires de mots de passe peuvent remplir automatiquement le champ **Clé secrète** avec votre mot de passe Fastly. Si l’intégration AWS échoue, saisissez la clé secrète manuellement.

Une fois les étapes ci-dessus terminées, cliquez sur **Options avancées** et configurez les éléments suivants :

| Champ | Description |
| --- | --- |
| **Chemin** | Copiez le **chemin** depuis la page de configuration de LLM Optimizer. ![Chemin](/help/overview/assets/log-forwarding/fastly/fastly-path.png) |
| **Sélectionnez un format de ligne de journal.** | Vide |
| **Compression** | Gzip |
| **Niveau de redondance** | Standard |
| **ACL** | Aucun |
| **Chiffrement côté serveur** | Aucun |
| **Octets maximum** | 0 |

Après avoir configuré les options avancées :

1. Cliquez sur **Créer** pour créer le point d’entrée.
1. Dans le menu **Activer**, sélectionnez **Activer en production** pour effectuer le déploiement.

>[!NOTE]
>
>Fastly transmet les journaux en continu à S3 ; le site web et l’API de S3 ne rendent les fichiers disponibles qu’une fois le chargement terminé.

### Exemple d’entrée de journal {#example}

Vous trouverez ci-dessous un exemple de chaîne de format pour l’envoi de données vers Amazon S3 :

```json
{
  "timestamp": "2026-02-10T05:05:36+0000",
  "host": "example.com",
  "url": "/my/path",
  "request_method": "GET",
  "request_referer": "https://example.com/my/other/path",
  "request_user_agent": "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
  "response_status": 200,
  "response_content_type": "text/css; charset=utf-8",
  "client_country_code": "argentina",
  "time_to_first_byte": "0.138"
}
```
