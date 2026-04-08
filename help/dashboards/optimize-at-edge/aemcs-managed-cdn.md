---
title: Optimiser sur Edge - Réseau CDN géré par AEM Cloud Service (Fastly)
description: Découvrez comment configurer le réseau CDN géré par AEM Cloud Service (rapidement) pour une optimisation sur Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 0c7ccadbb40c8c119cb2a57cf8118708c33c4236
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 12%

---


# Réseau CDN géré par AEM Cloud Service (Fastly)

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Pour commencer à acheminer le trafic d’agent vers Edge Optimizer :

1. Dans LLM Optimizer, ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau de diffusion de contenu**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Recherchez la section **Déployer des optimisations sur des agents d’IA**. Cochez la case **Activer le moteur d’optimisation**.

   ![Déploiement des optimisations sur les agents d’IA - en attente](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Dans la boîte de dialogue de confirmation, sélectionnez **Activer**. L’équipe d’Adobe s’occupera de la configuration du routage en votre nom.

   ![Boîte de dialogue de confirmation Activer le moteur d’optimisation](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

   Une fois le routage configuré et actif, son statut passe à **Terminé** avec une coche verte confirmant qu&#39;il est activé. Aucune autre action n’est requise de votre part.

   ![Déploiement des optimisations sur les agents d’IA - terminé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

**Routage en libre-service via le pipeline Cloud Manager**

Si vous préférez configurer le routage vous-même via le pipeline Cloud Manager, procédez comme suit. La configuration du routage est effectuée à l’aide d’une règle [originSelector CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#origin-selectors). Les conditions préalables sont les suivantes :

* Choisissez le domaine à acheminer.
* Choisissez les chemins à acheminer.
* Décidez des agents utilisateur à acheminer (regex recommandée).

Pour déployer la règle, vous devez effectuer les opérations suivantes :

* Créez un [pipeline de configuration](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/config-pipeline).
* Validez le fichier de configuration `cdn.yaml` dans votre référentiel.
* Exécutez le pipeline de configuration.

```
kind: "CDN"
version: "1"
data:
  # Origin selectors to route to Edge Optimize backend
  originSelectors:
    rules:
      - name: route-to-edge-optimize-backend
        when:
          allOf:
            - reqHeader: x-edgeoptimize-request
              exists: false # avoid loops when requests comes from Edge Optimize
            - reqHeader: user-agent
              matches: "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)" # routed user agents
            - reqProperty: domain
              equals: "example.com" # routed domain
            - reqProperty: originalPath
              matches: '(/[^./]+|\.html|/)$' # routed extensions, with .html extension or without extension
            - anyOf:
              - { reqProperty: originalPath, in: [ "/page.html" ] } # routed pages, exact path matching
              - { reqProperty: originalPath, like: "/dir/*" } # routed pages, wildcard path matching
        action:
          type: selectOrigin
          originName: edge-optimize-backend
    origins:
      - name: edge-optimize-backend
        domain: "live.edgeoptimize.net"
```

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

**4. Vérifiez le statut du routage dans**

Vous pouvez également confirmer le routage dans l’interface utilisateur de LLM Optimizer. Ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**. Lorsque le routage est actif, la section **Déployer les optimisations sur les agents d’IA** indique **Terminé**.

![Déploiement des optimisations sur les agents d’IA - terminé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

{{return-to-overview}}
