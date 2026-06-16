---
title: Optimisation d’Edge - Azure Front Door (BYOCDN)
description: Découvrez comment configurer le réseau BYOCDN de porte d’entrée Azure pour l’optimisation sur Edge dans LLM Optimizer.
feature: Opportunities
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 1d07ce1820e2688a130e410ee88ab329d628356a
workflow-type: tm+mt
source-wordcount: 768
ht-degree: 24%

---


# Portail d’Azure (BYOCDN)

Cette configuration achemine le trafic généré par l’IA agentique (demandes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois celle-ci terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

Azure Front Door n’exécute pas de code personnalisé en périphérie. Le routage est configuré à l’aide d’un **jeu de règles** ainsi que d’un **groupe d’origine** dédié pour Edge Optimize. Le basculement est géré par les sondes d’intégrité du groupe d’origine en fonction des priorités d’Azure Front Door.

**Conditions préalables**

Avant de configurer les règles de routage d’Azure Front Door, vérifiez que vous disposez des éléments suivants :

* Accès à votre profil Azure Front Door.
* Clé d’API Edge Optimize récupérée à partir de l’interface d’utilisation de LLM Optimizer. Pour connaître les étapes, voir [Récupération de vos clés API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facultatif) Pour tester le routage de préproduction, consultez [Clé API de préproduction](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Étape 1 : création d’un groupe d’origine pour Edge Optimize

Votre profil Azure Front Door comporte déjà un groupe d’origine par défaut qui pointe vers votre origine. Créez un **nouveau** groupe d’origine pour Edge Optimize :

* **Nom :** `edge-optimize-origin-group`
* **Origines (basculement sur incident en fonction de la priorité) :**
   * **Priorité 1** — `live.edgeoptimize.net` (En-tête d’hôte d’origine : `live.edgeoptimize.net`)
   * **Priorité 2** : point d’entrée de votre domaine (par exemple, `www.example.com`). Ceci est destiné au basculement : si Edge Optimize n’est pas intègre, les requêtes sont acheminées vers votre domaine, qui rentre à Azure Front Door et est diffusé à partir de votre origine par défaut.
* **Sondes d’intégrité :** **Activé**
   * Chemin : `/health/<your-domain>` (par exemple, `/health/www.example.com`)
   * Protocole : HTTPS
   * Intervalle : 225 secondes
* **Affinité de session :** **Désactivé**
* **Validation du nom de l’objet du certificat :** **Activé**

![Edge Optimisez le groupe d’origine avec deux sondes d’origine et d’intégrité prioritaires](/help/assets/optimize-at-edge/azure-front-door-origin-group.png)

>[!NOTE]
>
>Le groupe d’origine `edge-optimize-origin-group` affiche un avertissement **« Non associé »** dans le portail. Cela est prévu : il est référencé par le biais d’un remplacement d’itinéraire de jeu de règles, et non directement par un itinéraire.

## Étape 2 : Configurer votre itinéraire

Un itinéraire par défaut est généralement créé avec votre profil Azure Front Door. Le jeu de règles (étape 3) remplace le groupe d’origine pour le trafic agentic, de sorte qu’aucun itinéraire distinct n’est nécessaire pour Edge Optimize.

## Étape 3 : créer l’ensemble de règles

Accédez à **Ensembles de règles** > **Ajoutez un ensemble de règles** et nommez-le `EORouting`. Ajoutez trois règles dans cet ordre.

![Ensemble de règles EORouting affichant les règles d’extraction d’en-tête et de routage de robots](/help/assets/optimize-at-edge/azure-front-door-ruleset-routing.png)

### Règle 1 : StripIncomingEOHeaders01

Élimine les en-têtes Edge Optimize entrants pour éviter les usurpations. Aucune condition : s’applique à toutes les requêtes. Arrêter l’évaluation : **Désactivé**.

**Actions** — Supprimez l&#39;en-tête de la demande pour chacun des éléments suivants :

* `x-edgeoptimize-url`
* `x-edgeoptimize-config`
* `x-edgeoptimize-api-key`
* `x-edgeoptimize-fetcher-key`

### Règle 2 : EOGPTBotRootGET03

Achemine les requêtes de robots sur les chemins de page d’HTML vers Edge Optimize. Arrêter l&#39;évaluation : **Activé**.

**Conditions** (toutes doivent correspondre) :

* Méthode de requête : **Equal** `GET`
* Chemin de la requête : **RegEx** `(^$|^.*/$|(^|.*/)[^./]+$|^.*\.html$)` (correspond à la racine du site, aux chemins se terminant par `/`, aux chemins de page sans extension et aux chemins de `.html`)
* User-Agent : **contient l’un des** suivants `claude-searchbot` `chatgpt-user`, `gptbot`, `oai-searchbot`, `adobeedgeoptimize-ai`, `perplexitybot`, `perplexity-user`, `claudebot`, `claude-user`,. Définissez la transformation de chaîne sur **En minuscules**.
* `x-edgeoptimize-monitor` : **ne contient pas** `1`
* `x-edgeoptimize-request` : **ne contient aucun** `failover`, `1`

**Actions** :

* `x-edgeoptimize-url` de remplacement de l’en-tête de la requête = `/{url_path}?{query_string}`
* `x-edgeoptimize-config` de remplacement de l’en-tête de la requête = `LLMCLIENT=TRUE;`
* `x-edgeoptimize-api-key` de remplacement de l’en-tête de la requête = `YOUR_API_KEY`
* `x-edgeoptimize-monitor` de remplacement de l’en-tête de la requête = `1`
* Remplacement de configuration d’itinéraire : groupe d’origine → `edge-optimize-origin-group`, protocole de transfert → correspondre à la requête entrante, mise en cache → **désactivé**

### Règle 3 : HealthProbeRewrite03

Réécrit les requêtes de vérification d’intégrité Azure Front Door afin qu’elles atteignent votre origine en tant que `/` au lieu de `/health/<domain>`. Cela permet à Azure Front Door de surveiller la disponibilité d’Edge Optimizer sans avoir besoin d’un point d’entrée d’intégrité dédié sur votre origine. Arrêter l&#39;évaluation : **Activé**.

![Règle de réécriture de la sonde d’intégrité](/help/assets/optimize-at-edge/azure-front-door-ruleset-healthprobe.png)

**Conditions** (toutes doivent correspondre) :

* Chemin d’accès à l’URL de la requête : **Commence par** `/health/`
* `x-fd-healthprobe` : **Contient** `1`

**Actions** :

* Réécriture d&#39;URL — Modèle Source : `/health/`, Destination : `/`
* Remplacement de l&#39;en-tête de réponse `custom-origin-health` = `routed` (diagnostic — peut être supprimé après vérification)
* En-tête de la demande ajouter `user-agent` = ` AdobeEdgeOptimize/1.0` (ajoutez un espace de début — Azure Front Door ajoute la valeur en l’état)
* Remplacement de configuration d’itinéraire : groupe d’origine → `default-origin-group`, protocole de transfert → correspondre à la requête entrante, mise en cache → **désactivé**

## Étape 4 : associer le jeu de règles à l&#39;itinéraire

Ouvrez votre itinéraire, faites défiler l’écran jusqu’à la section **Règles** en bas, puis sélectionnez l’ensemble de règles `EORouting` dans la liste déroulante. Si vous disposez d’ensembles de règles existants, utilisez **Déplacer en haut** pour positionner le `EORouting` à **#1**. Les règles Optimiser sur Edge interceptent uniquement le trafic d’agent et les requêtes de boucle d’Edge Optimize. Tous les autres types de trafic sont transmis sans être affectés à vos autres règles. Enregistrez et attendez la propagation (environ 20 minutes).

## Autoriser l’optimisation sur Edge via des règles de pare-feu (facultatif)

{{waf-allowlist-setup}}

## Vérifier la configuration

Une fois la configuration terminée, vérifiez que le trafic des robots est acheminé vers Edge Optimize et que le trafic humain n’est pas affecté.

**1. Tester le trafic de robots (doit être optimisé)**

Simulez une requête de robot d’IA à l’aide d’une chaîne utilisateur-agent :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Une réponse réussie inclut l’en-tête `x-edgeoptimize-request-id`, confirmant que la requête a été acheminée via Edge Optimize :

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Tester le trafic humain (ne devrait PAS être affecté)**

Simulez une requête régulière de navigateur humain :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La réponse ne doit **pas** contenir l’en-tête `x-edgeoptimize-request-id`. Le contenu de la page et le temps de réponse doivent rester identiques à avant l’activation de l’option Optimize at Edge.

**3. Comment différencier les deux scénarios**

| En-tête | Trafic de robots (optimisé) | Trafic humain (non affecté) |
|---|---|---|
| `x-edgeoptimize-request-id` | Présent : contient un ID de requête unique | Absent |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
