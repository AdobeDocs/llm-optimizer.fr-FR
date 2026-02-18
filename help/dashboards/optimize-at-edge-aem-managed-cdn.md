---
title: Optimiser sur Edge - Réseau CDN géré par AEM Cloud Service (Fastly)
description: Découvrez comment configurer le réseau CDN géré par AEM Cloud Service (rapidement) pour une optimisation sur Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 8cdd15413555057165f69ea4d5a15b243ab9098d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 16%

---


# Réseau CDN géré par AEM Cloud Service (Fastly)

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Pour commencer à acheminer le trafic d’agent vers Edge Optimizer :

1. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Sous **Routage du trafic AI pour déployer des optimisations**, cochez la case **Déployer des optimisations sur des agents AI**. L’équipe d’Adobe s’occupera de la configuration du routage en votre nom.

   ![Cochez la case Déployer les optimisations sur les agents AI](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Après avoir activé la case à cocher, le statut indique que la configuration est en cours. L’équipe d’Adobe terminera la configuration du routage pour vous.

   ![Configuration du routage du trafic AI en cours](/help/assets/optimize-at-edge/prereq-traffic-routing-progress.png)

   Une fois le routage configuré et actif, son état est mis à jour pour afficher une coche verte indiquant qu’il a bien été activé. Aucune autre action n’est requise de votre part.

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

{{verify-setup-adobe-aem-cs-cdn}}

{{return-to-overview}}
