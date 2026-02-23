---
title: Optimisation d’Edge - CloudFront (BYOCDN)
description: Découvrez comment configurer CloudFront BYOCDN pour Optimiser sur Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 1253d0f0a58f6523699c52fbfab23028dc469c82
workflow-type: tm+mt
source-wordcount: '2228'
ht-degree: 1%

---


# CloudFront (BYOCDN)

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer CloudFront, vérifiez que vous disposez des éléments suivants :

* Une distribution CloudFront existante desservant votre site web.
* Les autorisations IAM d’AWS pour créer des fonctions Lambda, des rôles IAM, des distributions CloudFront et des politiques de cache.
* Fin du processus d’intégration de LLM Optimizer.
* Transfert du journal CDN vers LLM Optimizer terminé.
* Clé d’API Edge Optimize récupérée à partir de l’interface utilisateur de LLM Optimizer.

{{retrieve-byocdn-api-key}}

**Étape 1 : Créer une origine Edge Optimize**

**Navigation :** Console AWS > CloudFront > Distributions > [Votre distribution] > Onglet Origines

1. Cliquez sur **Créer l’origine**.

2. Configurez l’origine :
   * **Domaine d’origine :** `live.edgeoptimize.net`
   * **Nom :** `EdgeOptimize_Origin`

3. Laissez tous les autres champs avec leurs valeurs par défaut.

4. Ajouter des en-têtes personnalisés :

   | En-tête | Valeur |
   |--------|-------|
   | `x-edgeoptimize-api-key` | Votre clé API |
   | `x-forwarded-host` | `www.example.com` |

   Remplacez `www.example.com` par le domaine et la `Your API key` de votre site web réel à l’aide de la clé API Edge Optimize fournie par votre représentant Adobe.

5. Cliquez sur **Créer l’origine**.

![Création d’origine Cloudfront](/help/assets/optimize-at-edge/cloudfront-origin-creation.png)

**Étape 2 : créer une fonction de requête de visionneuse**

**Navigation :** Console AWS > CloudFront > Fonctions

1. Cliquez sur **Créer une fonction**.

2. Configurez les éléments suivants :
   * **Nom :** `edgeoptimize-routing`
   * **Runtime:** `cloudfront-js-2.0`

3. Remplacez le code par défaut par le code de [viewer-request.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/cloudfront-function/viewer-request.js).

   Avant de publier, personnalisez les valeurs suivantes dans le code :

   * `YOUR_DEFAULT_ORIGIN` — Remplacez par le nom de votre origine par défaut existante (disponible dans CloudFront > Distributions > [Votre distribution] > Onglet Origines).
   * `TARGETED_PATHS` : définissez cette option sur `null` pour cibler toutes les pages HTML ou sur un tableau de chemins spécifiques, par exemple `['/', '/products', '/about']`.

4. Cliquez sur **Enregistrer les modifications** > **Fonction de publication**.

![Création de la fonction Cloudfront](/help/assets/optimize-at-edge/cloudfront-function-creation.png)


**Étape 3 : Configurer la politique de cache**

**Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

Vérifiez la politique de cache actuellement associée à votre comportement. Cliquez sur **Modifier** sur votre comportement et consultez la section **Clé de cache et demandes d’origine** pour identifier votre scénario :

* **Scénario A (hérité) :** un bouton radio intitulé **Paramètres de cache hérités** sélectionné s’affiche. Il n’existe pas de liste déroulante de nom de politique ; à la place, vous voyez les paramètres TTL et d’en-tête intégrés.
* **Scénario B (Politique personnalisée) :** vous voyez **Politique de mise en cache** sélectionnée avec un nom de politique que vous ou votre équipe avez créé (et non une politique fournie par AWS).
* **Scénario C (Politique gérée) :** vous voyez **Politique de mise en cache** sélectionnée avec un nom fourni par AWS, tel que `CachingOptimized`, `CachingDisabled` ou `CachingOptimizedForUncompressedObjects` ; elle ne peut pas être modifiée.

**Scénario A : paramètres de cache hérités**

Si votre comportement utilise les paramètres de cache hérités :

1. Sous **Clé de cache et demandes d’origine**, vous verrez **Paramètres de cache hérités** sélectionnés.

2. Ajoutez des `x-edgeoptimize-config` et des `x-edgeoptimize-url` à la liste autorisée **En-têtes** :

   * Sélectionnez **Inclure les en-têtes suivants** dans la liste déroulante.
   * Ajoutez des `x-edgeoptimize-config` et des `x-edgeoptimize-url`.
     ![Hérité du cache Cloudfront](/help/assets/optimize-at-edge/cloudfront-cache-policy-legacy.png)

   Si vous avez déjà sélectionné **Tous** dans la liste déroulante En-têtes , ignorez cette étape : tous les en-têtes sont automatiquement transférés vers l’origine.

3. Vérifiez le paramètre **Caching d’objets** :

   * Si la valeur est **Personnaliser** — il est recommandé de définir **Durée de vie minimale** sur `0`. Cependant, si votre TTL minimale actuelle est déjà très courte, vous n’aurez peut-être pas besoin de la modifier.
   * Si le paramètre est défini sur **Utiliser les en-têtes de cache d’origine** — aucune modification n’est nécessaire.

4. Cliquez sur **Enregistrer les modifications**.

**Scénario B : non hérité avec une politique de cache personnalisée**

Si votre comportement utilise déjà une politique de cache personnalisée (une politique que vous avez créée, et non une politique gérée par AWS) :

**Navigation :** Console AWS > CloudFront > Politiques > Cache

1. Cliquez sur votre politique existante.

2. Cliquez sur **Modifier**.

3. Il est recommandé de définir **durée de vie minimale** sur `0`. Cependant, si votre TTL minimale actuelle est déjà très courte, vous n’aurez peut-être pas besoin de la modifier.
   ![Paramètres TTL de la stratégie de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

4. Sous **Paramètres de clé de cache** > **En-têtes**, ajoutez les `x-edgeoptimize-config` et les `x-edgeoptimize-url` à vos inclusions existantes.
   ![Mettre en cache les en-têtes de politique](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

5. Cliquez sur **Enregistrer les modifications**.

**Scénario C : non hérité avec une politique de cache gérée (AWS)**

Si votre comportement utilise une politique de cache géré par AWS (par exemple, `CachingOptimized`), vous ne pouvez pas la modifier. Vous devez créer une nouvelle politique de cache personnalisée qui réplique les paramètres de la politique gérée existante et ajoute les en-têtes Edge Optimize par-dessus.

**Partie 1 : Notez les paramètres actuels de votre stratégie de cache géré**

**Navigation :** Console AWS > CloudFront > Politiques > Cache

1. Recherchez et cliquez sur la politique de cache géré actuellement associée à votre comportement (par exemple, `CachingOptimized`).

2. Notez tous les paramètres existants :
   * TTL minimale, TTL maximale, TTL par défaut
   * En-têtes inclus dans la clé de cache
   * Cookies inclus dans la clé de cache
   * Chaînes de requête incluses dans la clé de cache
   * Support de compression (Gzip, Brotli)

**Partie 2 : création d’une politique de cache personnalisée avec les mêmes paramètres + configuration Edge Optimize**

**Navigation :** Console AWS > CloudFront > Politiques > Cache

1. Cliquez sur **Créer une stratégie de cache**.

2. **Nom :** `edgeoptimize-cache`

   ![Nom de la politique de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-name.png)

3. Reproduire tous les paramètres indiqués dans la partie 1, avec les modifications suivantes :

   * Il est recommandé de définir **durée de vie minimale** sur `0`. Cependant, si votre TTL minimale actuelle est déjà très courte, vous n’aurez peut-être pas besoin de la modifier.

   ![Paramètres TTL de la stratégie de cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

   * Sous **Paramètres de clé de cache** > **En-têtes**, incluez tout ce dont disposait la politique gérée, ainsi que les `x-edgeoptimize-config` et les `x-edgeoptimize-url` supplémentaires.

   ![Mettre en cache les en-têtes de politique](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

4. Cliquez sur **Créer**.

5. Revenez à votre comportement et associez la nouvelle politique :

   **Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

   1. Modifiez votre comportement.
   2. Sous **Clé de cache et demandes d’origine**, sélectionnez **Politique de cache**.
   3. Sélectionnez `edgeoptimize-cache` dans la liste déroulante.
   4. Cliquez sur **Enregistrer les modifications**.

**Étape 4 : créer la fonction Lambda@Edge (requête et réponse d’origine)**

>[!IMPORTANT]
>Les fonctions Lambda@Edge **doivent être créées dans la région de `us-east-1` (Virginie du Nord)**. Ceci est une exigence d’AWS. Même si la fonction est créée dans `us-east-1`, AWS la reproduit automatiquement vers tous les emplacements de périphérie CloudFront dans le monde entier, afin qu’elle s’exécute à l’emplacement de périphérie le plus proche de la visionneuse. Assurez-vous d’être dans la région `us-east-1` de la console AWS avant de continuer.

**Créez la fonction Lambda**

**Navigation :** Console AWS > Lambda

1. Cliquez sur **Créer une fonction**.

2. Sélectionnez **Auteur à partir de zéro**.

3. Configurez les éléments suivants :
   * **Nom de la fonction :** `edgeoptimize-origin`
   * Laissez tous les autres champs avec leurs valeurs par défaut.

4. Cliquez sur **Créer une fonction**.

5. Dans l’éditeur de code, remplacez le code par défaut par le code du fichier [origin-request-response.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/origin-request-response.js).

6. Cliquez sur **Déployer** pour enregistrer le code.

7. Notez le **nom du rôle d’exécution** affiché sous **Configuration** > **Autorisations** (par exemple, `edgeoptimize-origin-role-xxxxx`). Vous en aurez besoin dans les étapes suivantes.

**Mettre à jour la politique d’approbation du rôle d’exécution**

Le rôle créé automatiquement n’approuve que `lambda.amazonaws.com`. Pour Lambda@Edge, vous devez également ajouter `edgelambda.amazonaws.com`.

**Navigation :** Console AWS > IAM > Rôles > [votre rôle de l’étape précédente] > Onglet Relations de confiance

1. Cliquez sur **Modifier la politique d’approbation**.

2. Remplacez la politique par le contenu de [trust-policy.json](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/trust-policy.json).

3. Cliquez sur **Mettre à jour la politique**.

>[!WARNING]
>Le principal de service `edgelambda.amazonaws.com` est **obligatoire** pour Lambda@Edge. Sans cela, CloudFront ne peut pas appeler votre fonction aux emplacements Edge.

**Correction de la politique d’autorisation des journaux CloudWatch**

Le rôle créé automatiquement est fourni avec une politique `AWSLambdaBasicExecutionRole` configurée pour Lambda standard, qui a la mauvaise région et le nom de groupe de journaux pour Lambda@Edge. Vous devez le mettre à jour.

**Navigation :** Console AWS > IAM > Rôles > [votre rôle] > Onglet Autorisations > cliquez sur le nom de la politique jointe (par exemple, `AWSLambdaBasicExecutionRole-xxxx`)

1. Cliquez sur **Modifier**.

2. Remplacez la politique par le contenu de [cloudwatch-policy.json](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/cloudwatch-policy.json).

   Dans le fichier JSON, remplacez `ACCOUNT_ID` par votre identifiant de compte AWS (situé dans le coin supérieur droit de la console AWS) et `FUNCTION_NAME` par le nom de votre fonction Lambda (par exemple, `edgeoptimize-origin`).

3. Cliquez sur **Enregistrer les modifications**.

>[!WARNING]
>La région du ARN doit être `*` : Lambda@Edge s’exécute à l’emplacement Edge le plus proche de la visionneuse, de sorte que les journaux sont écrits vers CloudWatch dans la région de l’emplacement Edge (par exemple, `ap-south-1`, `eu-west-1`), pas nécessairement `us-east-1`. Le groupe de journaux utilise un nom comportant un préfixe de région : `/aws/lambda/us-east-1.FUNCTION_NAME`, où `us-east-1` correspond toujours à la région d’origine de la fonction.

**Publier une version**

1. Sur la page de la fonction, cliquez sur **Actions** (en haut à droite) > **Publier la nouvelle version**.

2. Ajoutez une description.

3. Cliquez sur **Publier**.
   ![Publication Lambda](/help/assets/optimize-at-edge/cloudfront-lambda-publish.png)

4. Copiez ou notez le **Fonction ARN** — vous en avez besoin à l&#39;étape suivante.
   ![Lambda ARN](/help/assets/optimize-at-edge/cloudfront-lambda-arn.png)

**Étape 5 : associer les fonctions et la politique de cache au comportement**

**Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

1. Modifiez votre comportement.

2. Si vous avez créé une stratégie de cache à l’étape 3 (scénario C), définissez **stratégie de cache** sur `edgeoptimize-cache`.
   ![Politique de cache](/help/assets/optimize-at-edge/cloudfront-behaviour-cache.png)

3. Sous **Associations de fonctions**, configurez :

   * **Requête de la visionneuse :** `edgeoptimize-routing`
   * **Demande d’origine :** fonction avec version ARN à l’étape 4 (dans **Publication d’une version**).
   * **Réponse d’origine :** fonction versionnée ARN à l’étape 4 (dans **Publication d’une version**).

   ![Configuration des associations de fonctions](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Cliquez sur **Enregistrer les modifications**.

**Étape 6 : tester la configuration**

**1. Tester le trafic de robots (doit être optimisé)**

Envoyez une requête avec un agent utilisateur de robot agent. Lors de la **première requête**, Edge Optimize peut renvoyer une réponse proxy (non optimisée) pendant qu’il traite et met en cache la page. Vous pouvez l’identifier par l’en-tête `x-edgeoptimize-proxy: 1` dans la réponse.

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

**4. Vérifiez que les journaux circulent correctement**

Après avoir exécuté les requêtes de test ci-dessus, vérifiez que les journaux sont écrits pour les fonctions CloudFront et Lambda@Edge.

*Journaux des fonctions CloudFront (`edgeoptimize-routing`)*

**Navigation :** Console AWS > CloudWatch > Groupes de journaux (dans le `us-east-1` ou la région où votre distribution CloudFront est configurée)

1. Recherchez un groupe de journaux nommé `/aws/cloudfront/function/edgeoptimize-routing`.
2. Ouvrez le dernier flux de journal.
3. Pour les demandes d’agence, vous devriez voir des entrées telles que :
   * `Adding origin group for userAgent: chatgpt-user`
   * `Routing to Edge Optimize origin for userAgent: chatgpt-user`
4. Pour les requêtes non-agences, vous devriez voir :
   * `Routing to Default origin for userAgent: ...`

Vous pouvez également vérifier l’onglet **Mesures** sous **Console AWS > CloudFront > Fonctions > edgeoptimizer-routing** pour afficher les nombres d’appels et les taux d’erreur.

*Journaux Lambda@Edge (`edgeoptimize-origin`)*

>[!IMPORTANT]
>Les journaux Lambda@Edge sont écrits vers CloudWatch dans la **région de l’emplacement Edge** qui a répondu à la requête, et non `us-east-1`. Cochez l’option CloudWatch dans la région AWS la plus proche de l’endroit où vous avez exécuté la commande curl.

**Navigation :** Console AWS > CloudWatch > Groupes de journaux (vérifiez que vous vous trouvez dans la bonne région)

1. Recherchez un groupe de journaux nommé `/aws/lambda/us-east-1.edgeoptimize-origin`.
2. Ouvrez le dernier flux de journal.
3. Pour les demandes d’agence, vous devriez voir des entrées telles que :
   * `Calling Edge Optimize Origin for agentic requests` — chemin principal
   * `Calling Default Origin in case of failover for agentic requests` — chemin de basculement
   * `Failover Triggered for agentic requests` — détection de basculement origine-réponse

Si le groupe de journaux n’est pas présent, vérifiez que les autorisations IAM ont été correctement mises à jour à l’étape 4. Vérifiez également d’autres régions AWS à proximité : l’emplacement Edge qui a répondu à votre demande peut différer de ce à quoi vous vous attendez.

**Résolution des incidents**

| Problème | Cause possible | Solution |
|-------|----------------|----------|
| Pas de `x-edgeoptimize-request-id` en réponse aux demandes de l’agent | Le groupe d’origine n’est pas acheminé vers Edge Optimize. | Vérifiez que `YOUR_DEFAULT_ORIGIN` a été correctement remplacé dans le code de fonction CloudFront (étape 2). |
| Erreurs 403 sur les requêtes agentiques | Clé API non valide ou manquante | Vérifiez la valeur de l’en-tête `x-edgeoptimize-api-key` dans les en-têtes personnalisés d’origine Edge Optimize (étape 1). |
| Impossible de trouver les journaux CloudWatch pour Lambda@Edge | Autorisations IAM incorrectes | Vérifiez que la politique d’autorisation des journaux CloudWatch a été mise à jour (étape 4). Remarque : les journaux Lambda@Edge apparaissent dans la région Edge qui a fourni la requête, pas nécessairement `us-east-1`. |
| Le cache ne respecte pas les `cache-control: no-store` | La durée de vie minimale peut être trop élevée. | Définissez la durée de vie minimale sur `0` dans votre stratégie de cache (étape 3). Si votre durée de vie minimale est déjà très courte, cela peut ne pas poser problème. |
| Trafic régulier (non agentique) rompu après la configuration | Mauvaise configuration de la politique de cache | Si vous avez créé une nouvelle politique de cache (scénario C), assurez-vous d’avoir répliqué tous les paramètres de la politique gérée d’origine. |

**Désactivation et réactivation de l’optimisation dans Edge**

La fonction Lambda@Edge (`edgeoptimize-origin`) est associée aux événements de requête d’origine et de réponse d’origine de votre comportement CloudFront. Comme il s’exécute en ligne sur chaque requête passant par ce comportement (à la fois humaine et agentique), une panne de Lambda@Edge aura un impact sur tout le trafic en direct, et pas seulement sur les requêtes agentiques. Si vous détectez une panne de Lambda@Edge, supprimez immédiatement les associations de fonctions pour restaurer le flux de trafic normal à votre origine par défaut.

**Comment détecter une panne de Lambda@Edge**

* **Tableau de bord d’intégrité du service AWS** — Vérifiez le [Tableau de bord d’intégrité du service AWS](https://health.aws.amazon.com/health/status) pour tout incident actif affectant **Amazon CloudFront** ou **AWS Lambda**. Une panne globale ou régionale signalée ici est le moyen le plus rapide de confirmer le problème du côté de l’infrastructure AWS plutôt que dans votre configuration.
* **Lambda@Edge erreurs** — Accédez à **AWS Console > CloudFront > Surveillance > [Votre distribution]**. Ouvrez l’onglet **Lambda@Edge errors** et recherchez les erreurs d’exécution dans le graphique **Erreurs d’exécution**. S’ils sont élevés, Lambda@Edge est peut-être en panne.

**Désolidarisation de la fonction Lambda@Edge**

**Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

1. Cliquez sur **Modifier** pour connaître votre comportement.

2. Faites défiler l’écran jusqu’à la section **Associations de fonctions**.

3. Définissez les associations suivantes sur **Aucune association** :

   | Événement | Passer à |
   |---|---|
   | Requête de la visionneuse | Aucune association |
   | Demande d’origine | Aucune association |
   | Réponse d’origine | Aucune association |

   ![Configuration des associations de fonctions](/help/assets/optimize-at-edge/cloudfront-no-function-association.png)

4. Cliquez sur **Enregistrer les modifications**.

5. Attendez que le déploiement de la distribution CloudFront soit terminé. Le statut passe de **Déploiement** à la date de dernière modification, généralement en quelques minutes.

Une fois déployé, tous les itinéraires de trafic rejoignent directement votre origine par défaut. Aucune configuration n’est supprimée ; la fonction Lambda et ses associations peuvent être restaurées à tout moment.

**Rattachement de la fonction Lambda@Edge**

**Navigation :** Console AWS > CloudFront > Distributions > [Votre Distribution] > Comportements

1. Cliquez sur **Modifier** pour connaître votre comportement.

2. Faites défiler l’écran jusqu’à la section **Associations de fonctions**.

3. Restaurez les associations :

   | Événement | Définir sur |
   |---|---|
   | Requête de la visionneuse | `edgeoptimize-routing` (fonction CloudFront) |
   | Demande d’origine | ARN lambda avec version à partir de l’étape 4 |
   | Réponse d’origine | ARN lambda avec version à partir de l’étape 4 |

   Utilisez la **fonction ARN** versionnée, comme indiqué à l’étape 4 (dans **Publication d’une version**).

   ![Configuration des associations de fonctions](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Cliquez sur **Enregistrer les modifications**.

5. Attendez que le déploiement de la distribution soit terminé, puis vérifiez que les requêtes agentiques renvoient l’en-tête `x-edgeoptimize-request-id` comme décrit à l’étape 6.

{{return-to-overview}}
