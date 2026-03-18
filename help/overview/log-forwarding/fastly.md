---
title: Transfert de journal - Fastly
description: Découvrez comment transférer les journaux CDN de Fastly vers le compartiment S3 Adobe pour la collecte de données de trafic agentic dans LLM Optimizer.
feature: Agentic Traffic
source-git-commit: d1f98770b39f550c36d93ece9b89933c0e90f189
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 4%

---


# Transfert de journal : rapide {#log-forwarding-fastly}

Cette page explique comment transférer les journaux CDN de Fastly vers le compartiment S3 d’Adobe pour la collecte de données de trafic agentic. Vous utiliserez la page de configuration du réseau CDN de LLM Optimizer pour vous intégrer à LLM Optimizer. Une fois le processus d’intégration terminé, suivez les étapes fournies sur cette page pour configurer le transfert des journaux dans la console web Fastly.

## Étape 1 : intégration dans LLM Optimizer {#step-1}

Sur la page LLM Optimizer [https://llmo.now/](https://llmo.now/) :

1. Accédez à **Configuration**.

   ![Bouton Configuration](/help/overview/assets/log-forwarding/common/config-button.png)

1. Cliquez sur l’onglet **Configuration du réseau CDN**.

   ![Onglet Configuration du réseau CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Cliquez sur **Commencer**.
1. En regard de **Activer AI Traffic Insights**, cliquez sur **Configurer**.

   ![Configurer](/help/overview/assets/log-forwarding/common/configure.png)
1. Sélectionnez **Fastly (BYOCDN)**.

   ![Sélectionnez Rapidement](/help/overview/assets/log-forwarding/fastly/fastly-select.png)
1. Cliquez sur **Intégration**.

## Étape 2 : créer un point d’entrée S3 dans Fastly {#step-2}

Pour créer un point d’entrée S3, sur le **Panneau de Contrôle Fastly** :

1. Dans le tableau de bord Fastly, accédez à **Services CDN** (et non aux Services de calcul).
1. Dans la zone **Amazon Web Services S3**, cliquez sur **Créer un point d’entrée**.
1. Renseignez les champs **Création d’un point d’entrée Amazon S3** :

| Champ | Description |
| --- | --- |
| **Nom** | Nom lisible par l’utilisateur du point d’entrée. |
| **Emplacement** | Par défaut |
| **Format du journal** | Utilisez la chaîne de format du journal indiquée dans la section **Chaîne de format du journal** ci-dessous. |
| **Format de l’horodatage** | `%Y-%m-%dT%H:%M:%S.000` |
| **Nom du compartiment** | Copiez le **nom du compartiment** de la page de configuration de LLM Optimizer. ![Nom du compartiment &#x200B;](/help/overview/assets/log-forwarding/fastly/fastly-bucket-name.png) |
| **Domaine** | Copiez le **Nom de domaine** de la page de configuration de LLM Optimizer. ![Nom de domaine &#x200B;](/help/overview/assets/log-forwarding/fastly/fastly-domain-name.png) |
| **Méthode d’accès** | **Informations d’identification de l’utilisateur** |
| **Informations d’identification de l’utilisateur** | Copiez la **clé d’accès** et la **clé secrète** de la page de configuration de LLM Optimizer. ![Clés d’accès &#x200B;](/help/overview/assets/log-forwarding/common/access-keys.png) |
| **Période** | `300` |

**Chaîne de format du journal:**

```json
{ "timestamp": "%{strftime(\{"%Y-%m-%dT%H:%M:%S%z"\}, time.start)}V", "host": "%{if(req.http.Fastly-Orig-Host, req.http.Fastly-Orig-Host, req.http.Host)}V", "url": "%{json.escape(req.url)}V", "request_method": "%{json.escape(req.method)}V", "request_referer": "%{json.escape(req.http.referer)}V", "request_user_agent": "%{json.escape(req.http.User-Agent)}V", "response_status": %{resp.status}V, "response_content_type": "%{json.escape(resp.http.Content-Type)}V", "client_country_code": "%{client.geo.country_name}V", "time_to_first_byte": "%{time.to_first_byte}V" }
```

>[!WARNING]
>
>Les gestionnaires de mots de passe peuvent remplir automatiquement le champ **Clé secrète** avec votre mot de passe Fastly. Si l’intégration d’AWS échoue, saisissez manuellement la clé secrète .

Une fois les étapes ci-dessus effectuées, cliquez sur **Options avancées** et définissez les éléments suivants :

| Champ | Description |
| --- | --- |
| **Chemin** | Copiez **Chemin** à partir de la page de configuration de LLM Optimizer. ![Chemin &#x200B;](/help/overview/assets/log-forwarding/fastly/fastly-path.png) |
| **Sélectionner un format de ligne de journal** | Vide |
| **Compression** | Gzip |
| **Niveau de redondance** | Standard |
| **ACL** | Aucun |
| **Chiffrement côté serveur** | Aucun |
| **Nombre maximal d’octets** | 0 |

Après avoir défini les options avancées :

1. Cliquez sur **Créer** pour créer le point d’entrée.
1. Dans le menu **Activer**, sélectionnez **Activer en production** pour déployer.

>[!NOTE]
>
>Fastly diffuse les journaux en continu vers S3, le site web S3 et l’API ne rendent les fichiers disponibles qu’une fois le chargement terminé.

### Exemple d’entrée de journal {#example}

Vous trouverez ci-dessous un exemple de chaîne de format pour l’envoi de données à Amazon S3 :

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
