---
title: Optimize at Edge - CloudFront (BYOCDN)
description: Découvrez comment configurer CloudFront BYOCDN pour Optimize at Edge dans LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T17:46:25.674Z'
TQID: 'https://experienceleague.adobe.com/yIEUTzlnvOX-WBf276KQcAN8sGYDpZNVibJt024VMWU'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: e36ee407933e2d3d56cadf1c9517f23f24d41d91
workflow-type: tm+mt
source-wordcount: 2343
ht-degree: 85%

---


# CloudFront (BYOCDN)

Cette configuration achemine le trafic généré par l’IA agentique (demandes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois celle-ci terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer CloudFront, assurez-vous d’avoir les éléments suivants :

* Distribution CloudFront existante hébergeant votre site web.
* Autorisations AWS IAM pour créer des fonctions Lambda, des rôles IAM, des distributions CloudFront et des politiques de cache.
* Clé d’API Edge Optimize récupérée à partir de l’interface d’utilisation de LLM Optimizer. Pour connaître les étapes, voir [Récupération de vos clés API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facultatif) Pour tester le routage de préproduction, consultez [Clé API de préproduction](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Étape 1 : Création de l’origine d’optimisation d’Edge

**Navigation :** Console AWS > CloudFront > Distributions > [Votre distribution] > Onglet Origines.

1. Cliquez sur **Créer une origine**.

2. Configurer l’origine :
   * **Domaine d’origine :**`live.edgeoptimize.net`
   * **Nom :** `EdgeOptimize_Origin`

3. Conservez les valeurs par défaut des autres champs.

4. Ajouter des en-têtes personnalisés :

   | En-tête | Valeur |
   |--------|-------|
   | `x-edgeoptimize-api-key` | Votre clé API |
   | `x-forwarded-host` | `www.example.com` |
   | `x-edgeoptimize-fetcher-key` | Votre clé de récupération (requise uniquement en cas de WAF) |

   Remplacez `www.example.com` par le nom de domaine de votre site Web et `Your API key` par la clé API Edge Optimize fournie par votre représentant ou représentante Adobe.

5. Cliquez sur **Créer une origine**.

![Création d’origine Cloudfront](/help/assets/optimize-at-edge/cloudfront-origin-creation.png)

## Étape 2 : créer une fonction de requête de visionneuse

**Navigation :** Console AWS > CloudFront > Fonctions

1. Cliquez sur **Créer une fonction**.

2. Configurez les éléments suivants :
   * **Nom :** `edgeoptimize-routing`
   * **Runtime :** `cloudfront-js-2.0`

3. Remplacez le code par défaut par le code de [viewer-request.js](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/cloudfront-function/viewer-request.js).

   Avant publication, personnalisez les valeurs suivantes dans le code :

   * `YOUR_DEFAULT_ORIGIN` — Remplacez par le nom de votre origine par défaut existante (trouvée dans CloudFront > Distributions >[Votre distribution] > onglet Origines).
   * `TARGETED_PATHS` — Définissez cette option sur `null` pour cibler toutes les pages HTML ou sur un tableau de chemins spécifiques, par exemple `['/', '/products', '/about']`.

4. Cliquez sur **Enregistrer les modifications** > **Fonction de publication**.

![Création de la fonction Cloudfront](/help/assets/optimize-at-edge/cloudfront-function-creation.png)


## Étape 3 : configurer la politique de cache

**Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

Vérifiez la politique de cache actuellement associée à votre comportement. Cliquez sur **Modifier** sur votre comportement et consultez la section **Clé de cache et demandes d’origine** pour identifier votre scénario :

* **Scénario A (hérité) :** un bouton radio intitulé **Paramètres de cache hérités** sélectionné s’affiche. Il n’existe pas de liste déroulante de nom de politique ; à la place, vous voyez les paramètres TTL et d’en-tête intégrés.
* **Scénario B (politique personnalisée) :** l’option **Politique de cache** sélectionnée s’affiche avec un nom de politique que votre équipe ou vous avez créé (et non pas une politique fournie par AWS).
* **Scénario C (politique gérée) :** l’option **Politique de cache** sélectionnée s’affiche avec un nom fourni par AWS, tel que `CachingOptimized`, `CachingDisabled` ou `CachingOptimizedForUncompressedObjects`. Elles ne peuvent pas être modifiées.

### Scénario A : paramètres de cache hérités

Si votre comportement utilise les paramètres de cache hérités :

1. Sous **Clé de cache et demandes d’origine**, l’option **Paramètres de cache hérités** sélectionnée s’affiche.

2. Ajoutez `x-edgeoptimize-config` et `x-edgeoptimize-url` à la liste autorisée **En-têtes** :

   * Sélectionnez **Inclure les en-têtes suivants** dans la liste déroulante.
   * Ajoutez `x-edgeoptimize-config` et `x-edgeoptimize-url`.
     ![Cache Cloudfront (hérité)](/help/assets/optimize-at-edge/cloudfront-cache-policy-legacy.png)

   Si vous avez déjà sélectionné **Tous** dans la liste déroulante En-têtes, ignorez cette étape : tous les en-têtes sont automatiquement transférés vers l’origine.

3. Vérifiez le paramètre **Mise en cache d’objets** :

   * Si le paramètre est défini sur **Personnaliser**, il est recommandé de définir **Durée de vie minimale** sur `0`. Cependant, si la durée de vie minimale actuelle est déjà très courte, vous n’avez peut-être pas besoin de la modifier.
   * Si le paramètre est défini sur **Utiliser les en-têtes de cache d’origine**, aucune modification n’est nécessaire.

4. Cliquez sur **Enregistrer les modifications**.

### Scénario B : non hérité avec une politique de cache personnalisée

Si votre comportement utilise déjà une politique de cache personnalisée (une politique que vous avez créée, et non une politique gérée par AWS) :

**Navigation :** Console AWS > CloudFront > Politiques > Cache

1. Cliquez sur votre politique existante.

2. Cliquez sur **Modifier**.

3. Il est recommandé de définir **durée de vie minimale** sur `0`. Cependant, si votre TTL minimale actuelle est déjà très courte, vous n’aurez peut-être pas besoin de la modifier.
   ![Paramètres de durée de vie de la politique de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

4. Sous **Paramètres de la clé de cache** > **En-têtes**, ajoutez `x-edgeoptimize-config` et `x-edgeoptimize-url` à vos inclusions existantes.
   ![En-têtes de la politique de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

5. Cliquez sur **Enregistrer les modifications**.

### Scénario C : non hérité avec une politique de cache gérée (AWS)

Si votre comportement utilise une politique de cache gérée par AWS (par exemple, `CachingOptimized`), vous ne pouvez pas la modifier. Vous devez créer une nouvelle politique de cache personnalisée qui réplique les paramètres de la politique gérée et y ajoute les en-têtes Edge Optimize.

**Partie 1 : notez les paramètres de votre politique de cache gérée actuelle**

**Navigation :** Console AWS > CloudFront > Politiques > Cache

1. Recherchez et cliquez sur la politique de cache gérée actuellement associée à votre comportement (par exemple, `CachingOptimized`).

2. Notez tous les paramètres existants :
   * Durée de vie minimale, Durée de vie maximale, Durée de vie par défaut
   * En-têtes inclus dans la clé de cache
   * Cookies inclus dans la clé de cache
   * Chaînes de requête incluses dans la clé de cache
   * Support de compression (Gzip, Brotli)

**Partie 2 : création d’une politique de cache personnalisée avec les mêmes paramètres + configuration Edge Optimize**

**Navigation :** Console AWS > CloudFront > Politiques > Cache

1. Cliquez sur **Créer une politique de cache**.

2. **Nom :** `edgeoptimize-cache`

   ![Nom de la politique de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-name.png)

3. Reproduisez tous les paramètres notés dans la partie 1, avec les modifications suivantes :

   * Il est recommandé de définir **Durée de vie minimale** sur `0`. Cependant, si la durée de vie minimale actuelle est déjà très courte, vous n’avez peut-être pas besoin de la modifier.

   ![Paramètres de durée de vie de la politique de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

   * Sous **Paramètres de la clé de cache** > **En-têtes**, incluez tout ce dont disposait la politique gérée, puis ajoutez `x-edgeoptimize-config` et `x-edgeoptimize-url`.

   ![En-têtes de la politique de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

4. Cliquez sur **Créer**.

5. Revenez à votre comportement et associez la nouvelle politique :

   **Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

   1. Modifiez le comportement.
   2. Sous **Clé de cache et demandes d’origine**, sélectionnez **Politique de cache**.
   3. Sélectionnez `edgeoptimize-cache` dans la liste déroulante.
   4. Cliquez sur **Enregistrer les modifications**.

## Étape 4 : créer la fonction Lambda@Edge (requête et réponse d’origine)

>[!IMPORTANT]
>Les fonctions Lambda@Edge **doivent être créées dans la région `us-east-1` (Virginie du Nord)**. Il s’agit d’une exigence d’AWS. Même si la fonction est créée dans `us-east-1`, AWS la reproduit automatiquement vers tous les emplacements Edge CloudFront dans le monde entier, afin qu’elle s’exécute à l’emplacement Edge le plus proche de l’utilisateur ou l’utilisatrice. Dans la console AWS, vérifiez que vous vous trouvez dans la région `us-east-1` avant de continuer.

### Création de la fonction Lambda

**Navigation :** Console AWS > Lambda

1. Cliquez sur **Créer une fonction**.

2. Sélectionnez **Créer à partir de zéro**.

3. Configurez les éléments suivants :
   * **Nom de la fonction :** `edgeoptimize-origin`
   * Conservez les valeurs par défaut des autres champs.

4. Cliquez sur **Créer une fonction**.

5. Dans l’éditeur de code, remplacez le code par défaut par le code contenu dans [origin-request-response.js](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/origin-request-response.js).

6. Cliquez sur **Déployer** pour enregistrer le code.

7. Notez le **nom du rôle d’exécution** affiché sous **Configuration** > **Autorisations** (par exemple, `edgeoptimize-origin-role-xxxxx`). Vous en aurez besoin lors des étapes suivantes.

### Mettre à jour la politique d’approbation du rôle d’exécution

Le rôle créé automatiquement n’approuve que `lambda.amazonaws.com`. Pour Lambda@Edge, vous devez également ajouter `edgelambda.amazonaws.com`.

**Navigation :** Console AWS > IAM > Rôles > [votre rôle de l’étape précédente] > onglet Relations de confiance

1. Cliquez sur **Modifier la politique de confiance**.

2. Remplacez la politique par le contenu de [trust-policy.json](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/trust-policy.json).

3. Cliquez sur **Mettre à jour la politique**.

>[!WARNING]
>Le principal de service `edgelambda.amazonaws.com` est **obligatoire** pour Lambda@Edge. Sans cela, CloudFront ne peut pas appeler votre fonction aux emplacements Edge.

### Correction de la politique d’autorisation des journaux CloudWatch

Le rôle créé automatiquement est fourni avec une politique `AWSLambdaBasicExecutionRole` configurée pour Lambda standard, qui une région et un nom de groupe de journaux incorrects pour Lambda@Edge. Vous devez le mettre à jour.

**Navigation :** Console AWS > IAM > Rôles > [votre rôle] > onglet Autorisations > cliquez sur le nom de la politique jointe (par exemple, `AWSLambdaBasicExecutionRole-xxxx`)

1. Cliquez sur **Modifier**.

2. Remplacez la politique par le contenu de [cloudwatch-policy.json](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/cloudwatch-policy.json).

   Dans le fichier JSON, remplacez `ACCOUNT_ID` par votre ID de compte AWS (situé dans le coin supérieur droit de la console AWS) et `FUNCTION_NAME` par le nom de votre fonction Lambda (par exemple, `edgeoptimize-origin`).

3. Cliquez sur **Enregistrer les modifications**.

>[!WARNING]
>La région de l’ARN doit être `*` : Lambda@Edge s’exécute à l’emplacement Edge le plus proche de l’utilisateur ou l’utilisatrice, de sorte que les journaux sont écrits dans CloudWatch dans la région de cet emplacement Edge (par exemple, `ap-south-1`, `eu-west-1`), pas nécessairement `us-east-1`. Le groupe de journaux utilise un nom comportant un préfixe de zone géographique : `/aws/lambda/us-east-1.FUNCTION_NAME`, où `us-east-1` correspond toujours à la zone géographique d’origine de la fonction.

### Correction du lien des journaux CloudWatch

Par défaut, le raccourci **Afficher les journaux CloudWatch** de la console Lambda renvoie vers `/aws/lambda/FUNCTION_NAME` dans `us-east-1` — le mauvais groupe de journaux pour Lambda@Edge. Configurez un groupe de journaux personnalisé afin que le lien pointe vers le chemin d’accès correct.

**Navigation :** Console AWS > Lambda > [votre fonction] > Configuration > Outils de surveillance et d’opérations

1. Cliquez sur **Modifier**.

2. Sous **Groupe de journaux CloudWatch**, sélectionnez **Personnalisé**.

3. Définissez le nom du groupe de journaux personnalisé sur `/aws/lambda/us-east-1.edgeoptimize-origin`.

4. Sous **Autorisations**, laissez la case **Ajouter les autorisations requises** **non cochée**.

   ![Configuration de groupe de journaux personnalisé Lambda](/help/assets/optimize-at-edge/cloudfront-lambda-custom-log-group.png)

5. Cliquez sur **Enregistrer**.

>[!NOTE]
>Même après ce correctif, le lien **Afficher les journaux CloudWatch** ouvre le nom correct du groupe de journaux, mais peut n’afficher aucune donnée si vous vous trouvez dans la mauvaise région. Les journaux Lambda@Edge sont écrits dans la région Edge qui a traité la requête (par exemple, `eu-west-1`, `ap-south-1`), et non `us-east-1`. Vous devez toujours passer à la bonne région dans CloudWatch pour afficher les journaux.

### Publication d’une version

1. Sur la page de la fonction, cliquez sur **Actions** (en haut à droite) > **Publier une nouvelle version**.

2. Ajoutez une description.

3. Cliquez sur **Publier**.
   ![Publication Lambda](/help/assets/optimize-at-edge/cloudfront-lambda-publish.png)

4. Copiez ou notez l’**ARN de la fonction** : vous en aurez besoin à l’étape suivante.
   ![ARN lambda](/help/assets/optimize-at-edge/cloudfront-lambda-arn.png)

## Étape 5 : associer les fonctions et la politique de cache au comportement

**Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

1. Modifiez le comportement.

2. Si vous avez créé une politique de mise en cache lors de l’étape 3 (scénario C), définissez la **politique de mise en cache** sur `edgeoptimize-cache`.
   ![Politique de mise en cache](/help/assets/optimize-at-edge/cloudfront-behaviour-cache.png)

3. Dans **Associations de fonctions**, configurez les éléments suivants :

   * **Requête de l’affichage :** `edgeoptimize-routing`
   * **Requête de l’origine :** ARN de fonction avec numéro de version provenant de l’étape 4 (dans **Publier une version**).
   * **Réponse de l’origine :** ARN de fonction avec numéro de version provenant de l’étape 4 (dans **Publier une version**).

   ![Configuration des associations de fonctions](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Cliquez sur **Enregistrer les modifications**.

## Autoriser l’optimisation sur Edge via des règles de pare-feu (facultatif)

{{waf-allowlist-setup}}

## Étape 6 : tester la configuration

**1. Tester le trafic de robots (doit être optimisé)**

Envoyez une requête avec un robot agentique de type agent utilisateur. Lors de la **première requête**, il est possible qu’Edge Optimize renvoie une réponse proxy (non optimisée) pendant qu’il traite et met en cache la page. Vous pouvez identifier ce cas de figure grâce à l’en-tête `x-edgeoptimize-proxy: 1` dans la réponse.

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

**4. Vérifier que les journaux sont correctement transmis**

Après avoir exécuté les demandes de test ci-dessus, vérifiez que les journaux sont bien écrits pour la fonction CloudFront et la fonction Lambda@Edge.

*Journaux de fonction CloudFront (`edgeoptimize-routing`)*

**Navigation :** Console AWS > CloudWatch > Groupes de journaux (dans `us-east-1` ou la région où votre distribution CloudFront est configurée)

1. Recherchez un groupe de journaux nommé `/aws/cloudfront/function/edgeoptimize-routing`.
2. Ouvrez le flux de journal le plus récent.
3. Pour les demandes agentiques, les entrées suivantes devraient s’afficher :
   * `Adding origin group for userAgent: chatgpt-user`
   * `Routing to Edge Optimize origin for userAgent: chatgpt-user`
4. Pour les demandes non agentiques, ce qui suit devrait s’afficher :
   * `Routing to Default origin for userAgent: ...`

Vous pouvez également accéder à l’onglet **Métriques** dans **Console AWS > CloudFront > Fonctions > edgeoptimize-routing** pour consulter le nombre d’invocations et les taux d’erreur.

*Journaux Lambda@Edge (`edgeoptimize-origin`)*

>[!IMPORTANT]
>Les journaux Lambda@Edge sont écrits dans CloudWatch dans la **région de l’emplacement Edge** qui a servi la demande, et non pas dans `us-east-1`. Vérifiez CloudWatch dans la région AWS la plus proche de l’endroit où vous avez exécuté la commande curl.

**Navigation :** Console AWS > CloudWatch > Groupes de journaux (vérifiez que vous vous trouvez dans la bonne région)

1. Recherchez un groupe de journaux nommé `/aws/lambda/us-east-1.edgeoptimize-origin`.
2. Ouvrez le flux de journal le plus récent.
3. Pour les demandes agentiques, les entrées suivantes devraient s’afficher :
   * `Calling Edge Optimize Origin for agentic requests` — Chemin principal
   * `Calling Default Origin in case of failover for agentic requests` — Chemin de basculement
   * `Failover Triggered for agentic requests` — Détection de basculement origine-réponse

Si le groupe de journaux n’apparaît pas, vérifiez que les autorisations IAM ont été correctement mises à jour à l’étape 4. Vérifiez également les autres régions AWS à proximité : l’emplacement Edge qui a servi votre demande peut ne pas être celui que vous attendez.

## Dépannage

| Problème | Cause possible | Solution |
|-------|----------------|----------|
| Aucun `x-edgeoptimize-request-id` dans la réponse pour les demandes agentiques | Le groupe d’origine ne redirige pas vers Edge Optimize | Vérifiez que `YOUR_DEFAULT_ORIGIN` a été correctement remplacé dans le code de la fonction CloudFront (étape 2). |
| Erreurs 403 sur les demandes agentiques | Clé API non valide ou manquante | Vérifiez la valeur de l’en-tête `x-edgeoptimize-api-key` dans les en-têtes personnalisés de l’origine Edge Optimize (étape 1). |
| Impossible de trouver les journaux CloudWatch pour Lambda@Edge | Autorisations IAM incorrectes | Vérifiez que la politique d’autorisation CloudWatch Logs a été mise à jour (étape 4). Remarque : les journaux Lambda@Edge apparaissent dans la région Edge qui a servi la demande, pas nécessairement dans `us-east-1`. |
| Le cache ne respecte pas `cache-control: no-store` | La durée de vie minimale est peut être trop élevée. | Définissez la durée de vie minimale sur `0` dans votre politique de cache (étape 3). Si la durée de vie minimale est déjà très courte, le problème doit venir d’ailleurs. |
| Trafic régulier (non agentique) interrompu après la configuration | Mauvaise configuration de la politique de cache | Si vous avez créé une nouvelle politique de cache (scénario C), assurez-vous d’avoir répliqué tous les paramètres de la politique gérée d’origine. |

## Désactivation et réactivation d’Optimize dans Edge

La fonction Lambda@Edge (`edgeoptimize-origin`) est associée aux événements de demande et de réponse d’origine de votre comportement CloudFront. Comme elle s’exécute en ligne sur chaque demande (humaine et agentique) passant par ce comportement, une panne de Lambda@Edge aura un impact sur l’ensemble du trafic réel, et pas seulement sur les demandes agentiques. Si vous détectez une panne de Lambda@Edge, supprimez immédiatement les associations de fonctions pour rétablir le flux de trafic normal vers votre origine par défaut.

### Comment détecter une panne de Lambda@Edge

* **Tableau de bord d’intégrité du service AWS** — Dans le [Tableau de bord d’intégrité du service AWS](https://health.aws.amazon.com/health/status), vérifiez si un incident actif affecte **Amazon CloudFront** ou **AWS Lambda**. Si une panne globale ou régionale s’affiche ici, cela confirme que le problème vient de l’infrastructure AWS plutôt que de votre configuration.
* **Erreurs Lambda@Edge** — Accédez à **Console AWS > CloudFront > Surveillance > [Votre distribution]**. Ouvrez l’onglet **Erreurs Lambda@Edge** et consultez le graphique **Erreurs d’exécution**. Si le taux d’erreurs est élevé, Lambda@Edge est peut-être en panne.

### Désolidarisation de la fonction Lambda@Edge

**Navigation :** Console AWS > CloudFront > Distributions > [Votre distribution] > Comportements

1. Cliquez sur **Modifier** sur votre comportement.

2. Faites défiler l’écran jusqu’à la section **Associations de fonctions**.

3. Définissez les associations suivantes sur **Aucune association** :

   | Événement | Passer à |
   |---|---|
   | Demande de la visionneuse | Aucune association |
   | Demande d’origine | Aucune association |
   | Réponse d’origine | Aucune association |

   ![Configuration des associations de fonctions](/help/assets/optimize-at-edge/cloudfront-no-function-association.png)

4. Cliquez sur **Enregistrer les modifications**.

5. Attendez que le déploiement de la distribution CloudFront soit terminé. Le statut passe de **Déploiement** à la date de la dernière modification, généralement en quelques minutes.

Une fois déployé, l’ensemble du trafic est dirigé directement vers votre origine par défaut. Aucune configuration n’est supprimée ; la fonction Lambda et ses associations peuvent être restaurées à tout moment.

### Rattachement de la fonction Lambda@Edge

**Navigation :** Console AWS > CloudFront > Distributions > [Votre distribution] > Comportements

1. Cliquez sur **Modifier** sur votre comportement.

2. Faites défiler l’écran jusqu’à la section **Associations de fonctions**.

3. Restaurez les associations :

   | Événement | Définir sur |
   |---|---|
   | Demande de la visionneuse | `edgeoptimize-routing` (fonction CloudFront) |
   | Demande d’origine | ARN lambda avec version à partir de l’étape 4 |
   | Réponse d’origine | ARN lambda avec version à partir de l’étape 4 |

   Utilisez l’**ARN de fonction** avec version que vous avez noté à l’étape 4 (dans **Publication d’une version**).

   ![Configuration des associations de fonctions](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Cliquez sur **Enregistrer les modifications**.

5. Attendez que le déploiement de la distribution soit terminé, puis vérifiez que les demandes agentiques renvoient l’en-tête `x-edgeoptimize-request-id` comme décrit à l’étape 6.

{{return-to-overview}}
