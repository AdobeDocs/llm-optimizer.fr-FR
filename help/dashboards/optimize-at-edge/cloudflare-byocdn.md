---
title: Optimiser sur Edge - Cloudflare (BYOCDN)
description: Découvrez comment configurer le BYOCDN de Cloudflare pour l’optimisation sur Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 1%

---


# Cloudflare (BYOCDN)

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles de routage de CloudFlare Worker, vérifiez que vous disposez des éléments suivants :

* Un compte Cloudflare avec Workers activé sur votre domaine.
* Accès aux paramètres DNS de votre domaine dans Cloudflare.
* Fin du processus d’intégration de LLM Optimizer.
* Transfert du journal CDN vers LLM Optimizer terminé.
* Clé d’API Edge Optimize récupérée à partir de l’interface utilisateur de LLM Optimizer.

{{retrieve-byocdn-api-key}}

**Fonctionnement du routage**

Lorsque la configuration est correcte, une requête vers votre domaine (par exemple, `www.example.com/page.html`) provenant d’un agent utilisateur agentic est interceptée par le programme de travail Cloudflare et acheminée vers le serveur principal d’Edge Optimize. La requête du serveur principal inclut les en-têtes requis.

**Test de la requête du serveur principal**

Vous pouvez vérifier le routage en adressant une requête directe au serveur principal d’Edge Optimize.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**En-têtes obligatoires**

Les en-têtes suivants doivent être définis sur les requêtes du serveur principal d’Edge Optimize :

| En-tête | Description | Exemple |
|--------|-------------|---------|
| `x-forwarded-host` | Hôte d’origine de la requête. Obligatoire pour l’identification du domaine du site. | `www.example.com` |
| `x-edgeoptimize-url` | Le chemin d’URL d’origine et la chaîne de requête de la requête. | `/page.html` ou `/products?id=123` |
| `x-edgeoptimize-api-key` | Clé API fournie par Adobe pour votre domaine. | `your-api-key-here` |
| `x-edgeoptimize-config` | Chaîne de configuration pour la différenciation des clés de cache. | `LLMCLIENT=TRUE;` |

**Étape 1 : créer le programme de travail Cloudflare**

1. Connectez-vous à votre tableau de bord Cloudflare.
2. Accédez à **Programmes de travail et pages** dans la barre latérale.
3. Cliquez sur **Créer une application** puis sur **Créer un programme de travail**.
4. Nommez votre programme de travail (par exemple, `edge-optimize-router`).
5. Cliquez sur **Déployer** pour créer le programme de travail avec le code par défaut.

![Tableau de bord Cloudflare Workers](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Étape 2 : ajouter le code de programme de travail**

Après avoir créé le programme de travail, cliquez sur **Modifier le code** et remplacez le code par défaut par le suivant :

```javascript
/**
 * Edge Optimize BYOCDN - Cloudflare Worker
 *
 * This worker routes requests from agentic bots (AI/LLM user agents) to the
 * Edge Optimize backend service for optimized content delivery.
 *
 * Features:
 * - Routes agentic bot traffic to Edge Optimize backend
 * - Failover to origin on Edge Optimize errors (any 4XX or 5XX errors)
 * - Loop protection to prevent infinite redirects
 * - Human visitors and SEO bots are served from the origin as usual
 */

// List of agentic bot user agents to route to Edge Optimize
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User'
];

// Targeted paths for Edge Optimize routing
// Set to null to route all HTML pages, or specify an array of paths
const TARGETED_PATHS = null; // e.g., ['/', '/page.html', '/products']

// Failover configuration
// Failover on any 4XX client error or 5XX server error from Edge Optimize
const FAILOVER_ON_4XX = true; // Failover on any 4XX error (400-499)
const FAILOVER_ON_5XX = true; // Failover on any 5XX error (500-599)

export default {
  async fetch(request, env, ctx) {
    return await handleRequest(request, env, ctx);
  },
};

async function handleRequest(request, env, ctx) {
  const url = new URL(request.url);
  const userAgent = request.headers.get("user-agent")?.toLowerCase() || "";

  // Check if request is already processed (loop protection)
  const isEdgeOptimizeRequest = !!request.headers.get("x-edgeoptimize-request");

  // Construct the original path and query string
  const pathAndQuery = `${url.pathname}${url.search}`;

  // Check if the path matches HTML pages (no extension or .html extension)
  const isHtmlPage = /(?:\/[^./]+|\.html|\/)$/.test(url.pathname);

  // Check if path is in targeted paths (if specified)
  const isTargetedPath = TARGETED_PATHS === null
    ? isHtmlPage
    : (isHtmlPage && TARGETED_PATHS.includes(url.pathname));

  // Check if user agent is an agentic bot
  const isAgenticBot = AGENTIC_BOTS.some((ua) => userAgent.includes(ua.toLowerCase()));

  // Route to Edge Optimize if:
  // 1. Request is NOT already from Edge Optimize (prevents infinite loops)
  // 2. User agent matches one of the agentic bots
  // 3. Path is targeted for optimization
  if (!isEdgeOptimizeRequest && isAgenticBot && isTargetedPath) {

    // Build the Edge Optimize request URL
    const edgeOptimizeURL = `https://live.edgeoptimize.net${pathAndQuery}`;

    // Clone and modify headers for the Edge Optimize request
    const edgeOptimizeHeaders = new Headers(request.headers);

    // Remove any existing Edge Optimize headers for security
    edgeOptimizeHeaders.delete("x-edgeoptimize-api-key");
    edgeOptimizeHeaders.delete("x-edgeoptimize-url");
    edgeOptimizeHeaders.delete("x-edgeoptimize-config");

    // x-forwarded-host: The original site domain
    // Use environment variable if set, otherwise use the request host
    edgeOptimizeHeaders.set("x-forwarded-host", env.EDGE_OPTIMIZE_TARGET_HOST ?? url.host);

    // x-edgeoptimize-api-key: Your Adobe-provided API key
    edgeOptimizeHeaders.set("x-edgeoptimize-api-key", env.EDGE_OPTIMIZE_API_KEY);

    // x-edgeoptimize-url: The original request URL path and query
    edgeOptimizeHeaders.set("x-edgeoptimize-url", pathAndQuery);

    // x-edgeoptimize-config: Configuration for cache key differentiation
    edgeOptimizeHeaders.set("x-edgeoptimize-config", "LLMCLIENT=TRUE;");

    try {
      // Send request to Edge Optimize backend
      const edgeOptimizeResponse = await fetch(new Request(edgeOptimizeURL, {
        headers: edgeOptimizeHeaders,
        redirect: "manual", // Preserve redirect responses from Edge Optimize
      }), {
        cf: {
          cacheEverything: true, // Enable caching based on origin's cache-control headers
        },
      });

      // Check if we need to failover to origin
      const status = edgeOptimizeResponse.status;
      const is4xxError = FAILOVER_ON_4XX && status >= 400 && status < 500;
      const is5xxError = FAILOVER_ON_5XX && status >= 500 && status < 600;

      if (is4xxError || is5xxError) {
        console.log(`Edge Optimize returned ${status}, failing over to origin`);
        return await failoverToOrigin(request, env, url);
      }

      // Return the Edge Optimize response
      return edgeOptimizeResponse;

    } catch (error) {
      // Network error or timeout - failover to origin
      console.log(`Edge Optimize request failed: ${error.message}, failing over to origin`);
      return await failoverToOrigin(request, env, url);
    }
  }

  // For all other requests (human users, SEO bots), pass through unchanged
  return fetch(request);
}

/**
 * Failover to origin server when Edge Optimize returns an error
 * @param {Request} request - The original request
 * @param {Object} env - Environment variables
 * @param {URL} url - Parsed URL object
 */
async function failoverToOrigin(request, env, url) {
  // Build origin URL
  const originURL = `${url.protocol}//${env.EDGE_OPTIMIZE_TARGET_HOST}${url.pathname}${url.search}`;

  // Prepare headers - clean Edge Optimize headers and add loop protection
  const originHeaders = new Headers(request.headers);
  originHeaders.set("Host", env.EDGE_OPTIMIZE_TARGET_HOST);
  originHeaders.delete("x-edgeoptimize-api-key");
  originHeaders.delete("x-edgeoptimize-url");
  originHeaders.delete("x-edgeoptimize-config");
  originHeaders.delete("x-forwarded-host");
  originHeaders.set("x-edgeoptimize-request", "fo");

  // Create and send origin request
  const originRequest = new Request(originURL, {
    method: request.method,
    headers: originHeaders,
    body: request.body,
    redirect: "manual",
  });

  const originResponse = await fetch(originRequest);

  // Add failover marker header to response
  const modifiedResponse = new Response(originResponse.body, {
    status: originResponse.status,
    statusText: originResponse.statusText,
    headers: originResponse.headers,
  });
  modifiedResponse.headers.set("x-edgeoptimize-fo", "1");
  return modifiedResponse;
}
```

Cliquez sur **Enregistrer et déployer** pour publier le programme de travail.

![Éditeur de code de Cloudflare Worker](/help/assets/optimize-at-edge/cloudflare-worker-editor.png)

**Étape 3 : Configurer les variables d’environnement**

Les variables d’environnement stockent en toute sécurité une configuration sensible telle que votre clé API.

1. Dans les paramètres de votre programme de travail, accédez à **Paramètres** > **Variables**.
2. Sous **Variables d’environnement**, cliquez sur **Ajouter une variable**.
3. Ajoutez les variables suivantes :

   | Nom de variable | Description | Nécessaires |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | Votre clé API Edge Optimize fournie par Adobe. | Oui |
   | `EDGE_OPTIMIZE_TARGET_HOST` | L’hôte cible des requêtes Edge Optimize (envoyées en tant qu’en-tête `x-forwarded-host`) et le domaine d’origine pour le basculement. Doit être le domaine uniquement sans protocole (par exemple, `www.example.com`, pas `https://www.example.com`). | Oui |

4. Pour la clé API, cliquez sur **Chiffrer** pour la stocker en toute sécurité.
5. Cliquez sur **Enregistrer et déployer**.

![Variables d’environnement Cloudflare](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

**Étape 4 : ajouter un itinéraire à votre domaine**

Pour activer le programme de travail sur votre domaine :

1. Accédez au **Paramètres** > **Triggers** de votre programme de travail.
2. Sous **Itinéraires**, cliquez sur **Ajouter un itinéraire**.
3. Saisissez le modèle de votre domaine (par exemple, `www.example.com/*` ou `example.com/*`).
4. Sélectionnez la zone dans la liste déroulante.
5. Cliquez sur **Enregistrer**.

Vous pouvez également configurer des itinéraires au niveau de la zone :

1. Accédez à votre domaine dans Cloudflare.
2. Accédez à **Itinéraires de travail**.
3. Cliquez sur **Ajouter un itinéraire** et spécifiez le modèle et le programme de travail.

![Itinéraires du programme de travail de Cloudflare](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Vérification du comportement de basculement**

Si Edge Optimize n’est pas disponible ou renvoie une erreur, le programme de travail bascule automatiquement sur votre origine. Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo` :

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

Vous pouvez surveiller les événements de basculement dans les journaux de Cloudflare Workers pour résoudre les problèmes.

**Comprendre la logique du programme de travail**

Le programme de travail de Cloudflare met en œuvre la logique suivante :

1. **Détection de l’agent utilisateur :** vérifie si l’agent utilisateur de la requête entrante correspond à l’un des robots agentic définis (non-respect de la casse).

2. **Ciblage des chemins d’accès :** filtre éventuellement les requêtes en fonction des chemins d’accès ciblés. Par défaut, toutes les pages d’HTML (URL se terminant par `/`, sans extension ou `.html`) sont acheminées. Vous pouvez spécifier des chemins d’accès spécifiques à l’aide du tableau `TARGETED_PATHS` .

3. **Protection contre les boucles :** l’en-tête `x-edgeoptimize-request` empêche les boucles infinies. Lorsqu’Edge Optimize renvoie les requêtes à votre origine, cet en-tête est défini sur `"1"` et le programme de travail transmet la requête sans la renvoyer à Edge Optimize.

4. **Sécurité des en-têtes :** avant de définir les en-têtes Edge Optimize, le programme de travail supprime tous les en-têtes `x-edgeoptimize-*` existants de la requête entrante pour empêcher les attaques par injection d’en-tête.

5. **Mappage des en-têtes :** le programme de travail définit les en-têtes requis pour Edge Optimize :
   * `x-forwarded-host` : identifie le domaine d’origine du site.
   * `x-edgeoptimize-url` - Conserve le chemin d’accès de la requête d’origine et la chaîne de requête.
   * `x-edgeoptimize-api-key` - Authentifie la requête avec Edge Optimize.
   * `x-edgeoptimize-config` - Fournit la configuration de la clé de cache.

6. **Logique de basculement :** si Edge Optimize renvoie un code d’état d’erreur (erreurs client 4XX ou erreurs serveur 5XX) ou si la requête échoue en raison d’une erreur réseau, le programme de travail bascule automatiquement sur votre origine à l’aide de `EDGE_OPTIMIZE_TARGET_HOST`. La réponse de basculement inclut l’en-tête `x-edgeoptimize-fo: 1` pour indiquer que le basculement s’est produit.

7. **Gestion des redirections :** l’option `redirect: "manual"` garantit que les réponses de redirection d’Edge Optimize sont transmises au client sans que le programme de travail ne les suive.

**Personnalisation de la configuration**

Vous pouvez personnaliser le comportement du programme de travail en modifiant les constantes de configuration en haut du code :

**Liste de robots agentiques**

Modifiez le tableau `AGENTIC_BOTS` pour ajouter ou supprimer des agents utilisateur :

```javascript
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User',
  // Add additional user agents as needed
  'ClaudeBot',
  'Anthropic-AI'
];
```

**Chemins ciblés**

Par défaut, toutes les pages HTML sont acheminées vers Edge Optimize. Pour limiter le routage à des chemins spécifiques, modifiez le tableau `TARGETED_PATHS` :

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Configuration de basculement**

Par défaut, le programme de travail bascule sur toute erreur 4XX ou 5XX d’Edge Optimize. Personnalisez ce comportement :

```javascript
// Default: failover on any 4XX or 5XX error
const FAILOVER_ON_4XX = true;
const FAILOVER_ON_5XX = true;

// Failover only on 5XX server errors (not 4XX client errors)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = true;

// Disable automatic failover (not recommended)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = false;
```

**Points importants à prendre en compte**

* **Comportement de basculement :** le programme de travail bascule automatiquement sur votre origine si Edge Optimize renvoie une erreur (codes d’état 4XX ou 5XX) ou si la requête échoue en raison d’une erreur réseau. Le basculement utilise `EDGE_OPTIMIZE_TARGET_HOST` comme domaine d’origine (similaire au `F_Default_Origin` de Fastly ou au `Default_Origin` de CloudFront). Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo: 1`, que vous pouvez utiliser pour la surveillance et le débogage.

* **Mise en cache :** Cloudflare met en cache les réponses en fonction de l’URL par défaut. Le trafic des agents ne recevant pas le même contenu que le trafic humain, assurez-vous que la configuration du cache en tient compte. Envisagez d’utiliser l’API de cache ou les en-têtes de cache pour différencier le contenu mis en cache. L’en-tête `x-edgeoptimize-config` doit être inclus dans votre clé de cache.

* **Limitation de débit :** Surveillez l’utilisation d’Edge Optimizer et envisagez d’implémenter une limitation de débit pour le trafic agentic, si nécessaire.

* **Tests :** testez toujours la configuration dans un environnement d’évaluation avant de la déployer en production. Vérifiez que le trafic d&#39;agents et de personnes se comporte comme prévu. Testez le comportement de basculement en simulant les erreurs Edge Optimize.

* **Journalisation :** activez la journalisation de Cloudflare Workers pour surveiller les requêtes et résoudre les problèmes. Accédez à **Collaborateurs** > **votre collaborateur** > **Journaux** pour afficher les journaux en temps réel. Le programme de travail consigne les événements de basculement à des fins de débogage.

**Résolution des incidents**

| Problème | Cause possible | Solution |
|-------|----------------|----------|
| Aucun en-tête de `x-edgeoptimize-request-id` dans la réponse | Itinéraire de collaborateur non apparié ou agent utilisateur non présent dans la liste des robots d&#39;agent. | Vérifiez que votre modèle d’itinéraire correspond à l’URL de requête. Vérifiez que l’agent utilisateur se trouve dans le tableau `AGENTIC_BOTS`. |
| Erreurs 401 ou 403 d’Edge Optimize | Clé API non valide ou manquante. | Vérifiez que `EDGE_OPTIMIZE_API_KEY` est correctement défini dans les variables d’environnement. Contactez Adobe pour confirmer que votre clé API est active. |
| Redirections infinies ou boucles | L’en-tête de protection contre les boucles n’est pas défini ou vérifié correctement. | Assurez-vous que la vérification de l’en-tête `x-edgeoptimize-request` est en place. |
| Trafic humain affecté | La logique de routage des collaborateurs est trop large. | Vérifiez que la logique de correspondance de l’agent utilisateur est correcte et ne respecte pas la casse. Vérifiez que `TARGETED_PATHS` est correctement configuré. |
| Temps de réponse lents | Latence réseau vers le serveur principal d’Edge Optimize. | Cela est prévu pour la première requête ; les requêtes suivantes sont mises en cache dans Edge Optimize. |
| En-tête `x-edgeoptimize-fo: 1` en réponse | Edge Optimize a renvoyé une erreur et le basculement vers l’origine s’est produit. | Vérifiez les journaux de Cloudflare Workers pour connaître le code d’erreur spécifique. Vérifiez l’état du service Edge Optimize avec Adobe. |
| Le basculement ne fonctionne pas | Indicateurs de basculement désactivés ou erreur dans la logique de basculement. | Vérifiez que `FAILOVER_ON_4XX` et `FAILOVER_ON_5XX` sont définis sur `true`. Recherchez des messages d&#39;erreur dans les journaux des collaborateurs. |
| Certains chemins ne sont pas optimisés. | Chemin ne correspondant pas aux chemins ciblés ou au modèle de page HTML. | Vérifiez que le chemin d’accès est en `TARGETED_PATHS` (s’il est spécifié) et correspond au modèle RegEx de page HTML. |
| Échec des requêtes avec un hôte non valide | `EDGE_OPTIMIZE_TARGET_HOST` inclut le protocole (par exemple, `https://`). | Utilisez uniquement le nom de domaine sans protocole (par exemple, `example.com`, et non `https://example.com`). |
| Erreur 530 lors du basculement | Cloudflare ne peut pas se connecter à l’origine ou la demande de basculement comporte des en-têtes non valides. | Assurez-vous que la fonction de basculement supprime les en-têtes Edge Optimize. Vérifiez que votre origine est accessible et que le DNS est correctement configuré. |

**Vérifier la configuration**

Une fois la configuration terminée, vérifiez que le trafic des robots est acheminé vers Edge Optimize et que le trafic humain n’est pas affecté.

**1. Tester le trafic de robots (doit être optimisé)**

Simulez une requête de robot d’IA à l’aide d’une chaîne agent-utilisateur :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Une réponse réussie inclut l’en-tête `x-edgeoptimize-request-id`, confirmant que la requête a été acheminée via Edge Optimize :

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Tester le trafic humain (ne devrait PAS être affecté)**

Simulez une requête régulière de navigateur humain :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La réponse ne doit **pas** contenir l’en-tête `x-edgeoptimize-request-id`. Le contenu de la page et le temps de réponse doivent rester identiques à avant l’activation de l’option Optimiser dans Edge.

**3. Comment différencier les deux scénarios**

| En-tête | Trafic de robots (optimisé) | Trafic humain (non affecté) |
|---|---|---|
| `x-edgeoptimize-request-id` | Présent : contient un ID de requête unique | Absent |
| `x-edgeoptimize-fo` | Présent uniquement en cas de basculement (valeur : `1`) | Absent |

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Statut du routage du trafic AI avec routage activé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

{{return-to-overview}}
