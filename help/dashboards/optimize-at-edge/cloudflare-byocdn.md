---
title: Optimize at Edge - Cloudflare (BYOCDN)
description: Découvrez comment configurer Cloudflare BYOCDN pour Optimize at Edge dans LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T17:46:02.378Z'
TQID: 'https://experienceleague.adobe.com/ZgOX0yC8qyb13Y7YNCg3Y1A6Q3TSk9-mUQ8gthzQvLM'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadcid: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1919
ht-degree: 96%

---


# Cloudflare (BYOCDN)

Cette configuration achemine le trafic généré par l’IA agentique (demandes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois celle-ci terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles de routage de CloudFlare Worker, vérifiez que vous disposez des éléments suivants :

* Compte Cloudflare avec Workers activé sur votre domaine.
* Accès aux paramètres DNS de votre domaine dans Cloudflare.
* Clé d’API Edge Optimize récupérée à partir de l’interface d’utilisation de LLM Optimizer. Pour connaître les étapes, voir [Récupération de vos clés API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facultatif) Pour tester le routage de préproduction, consultez [Clé API de préproduction](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Fonctionnement du routage**

Lorsque la configuration est correcte, une requête vers votre domaine (par exemple, `www.example.com/page.html`) provenant d’un agent utilisateur agentique est interceptée par le Cloudflare Worker et acheminée vers le serveur principal d’Edge Optimize. La requête du back-end inclut les en-têtes requis.

**Test de la requête du back-end**

Vous pouvez vérifier le routage en adressant une requête directe au back-end d’Edge Optimize.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**En-têtes obligatoires**

Les en-têtes suivants doivent être définis sur les requêtes du serveur principal d’Edge Optimize :

| En-tête | Description | Exemple |
|--------|-------------|---------|
| `x-forwarded-host` | Hôte d’origine de la requête. Obligatoire pour l’identification du domaine du site. | `www.example.com` |
| `x-edgeoptimize-url` | Le chemin d’URL d’origine et la chaîne de requête de la requête. | `/page.html` ou `/products?id=123` |
| `x-edgeoptimize-api-key` | La clé API fournie par Adobe pour votre domaine. | `your-api-key-here` |
| `x-edgeoptimize-config` | Chaîne de configuration pour la différenciation des clés de cache. | `LLMCLIENT=TRUE;` |

## Options de configuration

Il existe deux façons de configurer le Cloudflare Worker pour Edge Optimize :

* [**Option 1 : Déployer sur Cloudflare (recommandé)**](#option-1-deploy-to-cloudflare) — Crée automatiquement un nouveau worker et vous invite à saisir les variables d’environnement et les secrets requis. Utilisez cette option si vous ne disposez pas d’un Cloudflare Worker existant pour ce domaine.
* [**Option 2 : Configuration manuelle**](#option-2-manual-setup) — Instructions étape par étape pour créer et configurer vous-même le worker. Utilisez cette option si vous avez déjà un Cloudflare Worker configuré sur votre domaine — vous devrez fusionner le code Edge Optimize dans votre worker existant (voir [Étape 2 : Ajouter le code Worker](#option-2-manual-setup)), ou si vous préférez un contrôle total sur le déploiement.

Peu importe l’option que vous choisissez, vous devez lier manuellement le worker à votre domaine — voir [Étape : Ajouter un itinéraire à votre domaine](#add-a-route-to-your-domain).

## Option 1 : Déployer sur Cloudflare

Cette option utilise le bouton **Déployer sur Cloudflare** pour créer automatiquement le worker et configurer les variables d’environnement et les secrets requis dans votre compte Cloudflare. C’est la méthode la plus rapide pour démarrer si vous configurez un nouveau worker.

>[!IMPORTANT]
>
>Utilisez cette option uniquement si vous **n’avez pas** de Cloudflare Worker existant sur votre domaine. Si vous avez déjà un worker, utilisez [Option 2 : Configuration manuelle](#option-2-manual-setup) pour ajouter la logique de routage Edge Optimize à votre worker existant.

**Étape 1 : Déployer le worker**

Cliquez sur le bouton ci-dessous pour déployer le worker Edge Optimize sur votre compte Cloudflare :

[![Déployer sur Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/adobe/llmo-code-samples/tree/main/optimize-at-edge/cloudflare/automation)

**Étape 2 : Remplir le formulaire de déploiement**

Cliquez sur le bouton pour ouvrir la page de configuration des workers. Renseignez le formulaire comme suit :

![Page de configuration de Cloudflare Workers](/help/assets/optimize-at-edge/cloudflare-deploy-form.png)

1. **Compte Git** — Sélectionnez votre compte GitHub ou GitLab dans la liste déroulante. Cloudflare duplique le code du worker dans un référentiel de votre compte. Si aucun compte n’est répertorié, vous pouvez ajouter une nouvelle connexion directement à partir de la liste déroulante en sélectionnant **+ Nouvelle connexion GitHub** ou **+ Nouvelle connexion GitLab**. Pour plus d’informations, voir le [guide d’intégration Cloudflare Git](https://developers.cloudflare.com/workers/ci-cd/builds/git-integration/github-integration/).

   ![Menu déroulant Compte Git affichant les options Nouvelle connexion GitHub et Nouvelle connexion GitLab](/help/assets/optimize-at-edge/cloudflare-git-connection.png)
2. **Créer un dépôt Git privé** — Laissez cette case cochée (par défaut).
3. **Nom du projet** — Laissez tel quel `edge-optimize-router` ou entrez un nom de votre choix.
4. **EDGE_OPTIMIZE_API_KEY** — Collez votre clé API Edge Optimize fournie par Adobe. Cette valeur est stockée sous forme de secret chiffré.
5. **EDGE_OPTIMIZE_TARGET_HOST** — Entrez le domaine de votre site sans le protocole (par exemple, `www.example.com`).
6. **Commande de construction** — Laissez vide.
7. **Commande de déploiement** — Laissez tel quel`npm run deploy` (pré-rempli).
8. **Builds pour les branches hors production** — Laissez décoché. Il s’agit d’une fonctionnalité du flux de travail de développement. Elle n’est pas nécessaire pour ce déploiement.
9. Cliquez sur **Créer et déployer**.

Une fois le worker déployé, passez à l’étape [Ajouter un itinéraire à votre domaine](#add-a-route-to-your-domain) pour lier le worker à votre domaine. Le routage n’est pas configuré automatiquement et doit être effectué manuellement.

## Option 2 : Configuration manuelle

Suivez ces étapes pour créer et configurer manuellement le worker.

**Étape 1 : créer le Cloudflare Worker**

1. Connectez-vous à votre tableau de bord Cloudflare.
2. Accédez à **Workers et pages** dans la barre latérale.
3. Cliquez sur **Créer l’application**, puis sur **Créer un worker**.
4. Nommez votre worker (par exemple, `edge-optimize-router`).
5. Cliquez sur **Déployer** pour créer le worker avec le code par défaut.

![Tableau de bord de Cloudflare Workers](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Étape 2 : ajouter le code du worker**

Après avoir créé le programme de travail, cliquez sur **Modifier le code** et remplacez le code par défaut par le code de [worker.js](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudflare/automation/src/worker.js). Si vous disposez déjà d’un programme de travail de Cloudflare, fusionnez le code avec votre code de programme de travail existant au lieu de le remplacer entièrement.

Cliquez sur **Enregistrer et déployer** pour publier le worker.

**Étape 3 : Configurer les variables d’environnement et les secrets**

Les variables d’environnement stockent en toute sécurité une configuration sensible, telle que votre clé API.

1. Dans les paramètres de votre worker, accédez à **Paramètres** > **Variables**.
2. Sous **Variables d’environnement**, cliquez sur **Ajouter une variable**.
3. Ajoutez les variables suivantes :

   | Nom de variable | Description | Nécessaires |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | Votre clé API Edge Optimize fournie par Adobe. | Oui |
   | `EDGE_OPTIMIZE_TARGET_HOST` | L’hôte cible des requêtes Edge Optimize (envoyées en tant qu’en-tête `x-forwarded-host`) et le domaine d’origine pour le basculement. Doit être le domaine uniquement sans protocole (par exemple, `www.example.com`, pas `https://www.example.com`). | Oui |

4. Pour la clé API, cliquez sur **Chiffrer** pour la stocker en toute sécurité.
5. Cliquez sur **Enregistrer et déployer**.

![Variables d’environnement Cloudflare](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

## Ajouter un itinéraire à votre domaine {#add-a-route-to-your-domain}

Quelle que soit l’option de configuration utilisée, vous devez lier manuellement le worker à votre domaine. Cette étape active le worker sur votre trafic.

1. Accédez au **Paramètres** > **Triggers** de votre worker.
2. Sous **Itinéraires**, cliquez sur **Ajouter un itinéraire**.
3. Saisissez le modèle de votre domaine (par exemple, `www.example.com/*` ou `example.com/*`).
4. Sélectionnez votre zone dans la liste déroulante.
5. Cliquez sur **Enregistrer**.

Vous pouvez également configurer des itinéraires au niveau de la zone :

1. Accédez à votre domaine dans Cloudflare.
2. Accédez à **Itinéraires des workers**.
3. Cliquez sur **Ajouter un itinéraire** et spécifiez le modèle et le worker.

![Itinéraires de CloudFlare Worker](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Vérification du comportement de basculement**

Si Edge Optimize n’est pas disponible ou renvoie une erreur, le programme de travail bascule automatiquement sur votre origine. Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo` :

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

Vous pouvez surveiller les événements de basculement dans les journaux de Cloudflare Workers pour résoudre les problèmes.

**Comprendre la logique du worker**

Le Cloudflare Worker met en œuvre la logique suivante :

1. **Détection de l’agent utilisateur :** vérifie si l’agent utilisateur de la requête entrante correspond à l’un des robots agentic définis (non-respect de la casse).

2. **Ciblage des chemins d’accès :** filtre éventuellement les requêtes en fonction des chemins d’accès ciblés. Par défaut, toutes les pages d’HTML (URL se terminant par `/`, sans extension ou `.html`) sont acheminées. Vous pouvez spécifier des chemins d’accès spécifiques à l’aide du tableau `TARGETED_PATHS`.

3. **Protection contre les boucles :** l’en-tête `x-edgeoptimize-request` empêche les boucles infinies. Lorsqu’Edge Optimize renvoie les requêtes à votre origine, cet en-tête est défini sur `"1"` et le worker transmet la requête sans la renvoyer à Edge Optimize.

4. **Sécurité des en-têtes :** avant de définir les en-têtes Edge Optimize, le programme de travail supprime tous les en-têtes `x-edgeoptimize-*` existants de la requête entrante pour empêcher les attaques par injection d’en-tête.

5. **Mappage des en-têtes :** le worker définit les en-têtes requis pour Edge Optimize :
   * `x-forwarded-host` : identifie le domaine d’origine du site.
   * `x-edgeoptimize-url` : conserve le chemin d’accès de la requête d’origine et la chaîne de requête.
   * `x-edgeoptimize-api-key` : authentifie la requête avec Edge Optimize.
   * `x-edgeoptimize-config` : fournit la configuration de la clé de cache.

6. **Logique de basculement :** si Edge Optimize renvoie un code d’état d’erreur (erreurs client 4XX ou erreurs serveur 5XX) ou si la requête échoue en raison d’une erreur réseau, le worker bascule automatiquement sur votre origine à l’aide de `EDGE_OPTIMIZE_TARGET_HOST`. La réponse de basculement inclut l’en-tête `x-edgeoptimize-fo: 1` pour indiquer que le basculement s’est produit.

7. **Gestion des redirections :** l’option `redirect: "manual"` garantit que les réponses de redirection d’Edge Optimize sont transmises à la clientèle sans que le programme de travail ne les suive.

**Personnalisation de la configuration**

Vous pouvez personnaliser le comportement du worker en modifiant les constantes de configuration en haut du code :

**Liste de robots agentiques**

Modifiez le tableau `AGENTIC_BOTS` pour ajouter ou supprimer des agents utilisateur :

```javascript
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User',
  'ClaudeBot',
  'Claude-User',
  'Claude-SearchBot',
  // Add additional user agents as needed
];
```

**Chemins ciblés**

Par défaut, toutes les pages HTML sont acheminées vers Edge Optimize. Pour limiter le routage à des chemins spécifiques, modifiez le tableau `TARGETED_PATHS` :

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Comportements de configuration**

Par défaut, le programme de travail bascule sur toute erreur 4XX ou 5XX d’Edge Optimize. Personnalisez ce comportement :

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

* **Comportement de basculement :** le worker bascule automatiquement sur votre origine si Edge Optimize renvoie une erreur (codes d’état 4XX ou 5XX) ou si la requête échoue en raison d’une erreur réseau. Le basculement utilise `EDGE_OPTIMIZE_TARGET_HOST` comme domaine d’origine (similaire à `F_Default_Origin` pour Fastly ou à `Default_Origin` pour CloudFront). Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo: 1`, que vous pouvez utiliser pour la surveillance et le débogage.

* **Mise en cache :** Cloudflare met en cache les réponses en fonction de l’URL par défaut. Le trafic généré par l’IA agentique ne recevant pas le même contenu que le trafic humain, assurez-vous que la configuration du cache en tient compte. Envisagez d’utiliser l’API de cache ou les en-têtes de cache pour différencier le contenu mis en cache. L’en-tête `x-edgeoptimize-config` doit être inclus dans votre clé de cache.

* **Limitation de débit :** Surveillez l’utilisation d’Edge Optimizer et envisagez d’implémenter une limitation de débit pour le trafic généré par l’IA agentique, si nécessaire.

* **Tests :** testez toujours la configuration dans un environnement d’évaluation avant de la déployer en production. Vérifiez que le trafic agentique et humain se comporte comme prévu. Testez le comportement de basculement en simulant les erreurs Edge Optimize.

* **Journalisation :** activez la journalisation de Cloudflare Workers pour surveiller les requêtes et résoudre les problèmes. Accédez à **Workers** > **votre worker** > **Journaux** pour afficher les journaux en temps réel. Le worker consigne les événements de basculement à des fins de débogage.

**Résolution des incidents**

| Problème | Cause possible | Solution |
|-------|----------------|----------|
| Aucun en-tête `x-edgeoptimize-request-id` dans la réponse | Itinéraire de worker non apparié ou agent utilisateur non présent dans la liste des robots agentique. | Vérifiez que votre modèle d’itinéraire correspond à l’URL de requête. Vérifiez que l’agent utilisateur se trouve dans le tableau `AGENTIC_BOTS`. |
| Erreurs 401 ou 403 d’Edge Optimize | Clé API non valide ou manquante. | Vérifiez que `EDGE_OPTIMIZE_API_KEY` est correctement défini dans les variables d’environnement et les secrets. Contactez Adobe pour confirmer que votre clé API est active. |
| Redirections infinies ou boucles | L’en-tête de protection contre les boucles n’est pas défini ou vérifié correctement. | Assurez-vous que la vérification de l’en-tête `x-edgeoptimize-request` est en place. |
| Trafic humain affecté | La logique de routage des collaborateurs est trop large. | Vérifiez que la logique de correspondance de l’agent utilisateur est correcte et ne respecte pas la casse. Vérifiez que `TARGETED_PATHS` est correctement configuré. |
| Temps de réponse lents | Latence réseau vers le back end d’Edge Optimize. | Cela est prévu pour la première requête ; les requêtes suivantes sont mises en cache dans Edge Optimize. |
| En-tête `x-edgeoptimize-fo: 1` en réponse | Edge Optimize a renvoyé une erreur et le basculement vers l’origine s’est produit. | Vérifiez les journaux de Cloudflare Workers pour connaître le code d’erreur spécifique. Vérifiez l’état du service Edge Optimize avec Adobe. |
| Le basculement ne fonctionne pas | Indicateurs de basculement désactivés ou erreur dans la logique de basculement. | Vérifiez que `FAILOVER_ON_4XX` et `FAILOVER_ON_5XX` sont définis sur `true`. Vérifiez les messages d’erreur éventuels dans les journaux du worker. |
| Certains chemins ne sont pas optimisés | Chemin ne correspondant pas aux chemins ciblés ou au modèle de page HTML. | Vérifiez que le chemin d’accès est dans `TARGETED_PATHS` (s’il est spécifié) et correspond au modèle RegEx de page HTML. |
| Échec des requêtes avec un hôte non valide | `EDGE_OPTIMIZE_TARGET_HOST` inclut le protocole (par exemple, `https://`). | Utilisez uniquement le nom de domaine sans protocole (par exemple, `example.com`, et non `https://example.com`). |
| Erreur 530 lors du basculement | Cloudflare ne peut pas se connecter à l’origine ou la demande de basculement comporte des en-têtes non valides. | Assurez-vous que la fonction de basculement supprime les en-têtes Edge Optimize. Vérifiez que votre origine est accessible et que le DNS est correctement configuré. |

**Autoriser Optimize at Edge via des règles de pare-feu (facultatif)**

{{waf-allowlist-setup}}

**Vérifier la configuration**

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
| `x-edgeoptimize-fo` | Présent uniquement en cas de basculement (valeur : `1`) | Absent |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
