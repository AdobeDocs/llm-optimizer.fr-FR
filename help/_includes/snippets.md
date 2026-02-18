---
source-git-commit: beae935e7a34f5bccbe21578fa9a928912958710
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 2%

---
# Fragments de code

## Vérifier la configuration - Réseau CDN géré par Adobe {#verify-setup-adobe-aem-cs-cdn}

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

![Statut du routage du trafic AI avec routage activé](/help/assets/optimize-at-edge/adobe-CDN-traffic-routed-tick.png)

## Vérifier la configuration - BYOCDN {#verify-setup-byocdn}

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

## Étapes de récupération des clés API {#retrieve-byocdn-api-key}

**Procédure de récupération de votre clé API :**

1. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Sous **Routage du trafic AI pour déployer des optimisations**, cochez la case **Déployer des optimisations sur des agents AI**.

   ![Cochez la case Déployer les optimisations sur les agents AI](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copiez la clé API et suivez les étapes de configuration du routage ci-dessous.

   ![Copier la clé API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >À ce stade, le statut peut afficher une croix rouge indiquant que la configuration n’est pas encore terminée. Cela est attendu : une fois que vous avez terminé la configuration de routage ci-dessous et que le trafic des robots d’IA commence à circuler, le statut se met à jour vers une coche verte confirmant que le routage est activé avec succès.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

## Revenir à l’aperçu {#return-to-overview}

Pour en savoir plus sur l’optimisation sur Edge, y compris sur les opportunités disponibles, les workflows d’optimisation automatique et les questions fréquentes, revenez à la [&#x200B; Présentation de l’optimisation sur Edge &#x200B;](/help/dashboards/optimize-at-edge.md).
