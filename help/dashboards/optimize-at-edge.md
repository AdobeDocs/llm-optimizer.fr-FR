---
title: Optimiser dans Edge
description: Découvrez comment diffuser des optimisations dans LLM Optimizer à la périphérie du réseau CDN sans apporter de modifications de création requises.
feature: Opportunities
source-git-commit: 3c6f287b3c3787cee95f99b7031412f26692a88b
workflow-type: tm+mt
source-wordcount: '2291'
ht-degree: 1%

---


# Optimiser dans Edge

Cette section ...

## Qu’est-ce que l’optimisation chez Edge ?

Optimiser sur Edge est une fonctionnalité de déploiement Edge de LLM Optimizer qui peut apporter des modifications compatibles avec l’IA aux agents utilisateurs de LLM. Comme il fournit des optimisations à la périphérie du réseau CDN, aucune modification de création dans le système de gestion de contenu (CMS) n’est nécessaire. Il cible également uniquement le trafic d’agents et n’a aucune incidence sur les utilisateurs humains ou les robots SEO.

Lorsque LLM Optimizer détecte des opportunités d’optimisation d’une page, les utilisateurs peuvent déployer des correctifs directement en périphérie, sans qu’aucune modification de plateforme ne soit nécessaire.

Cette fonctionnalité est actuellement en accès anticipé.

## Pourquoi un client devrait-il être intéressé ?

Optimize chez Edge est une alternative plus rapide et plus épurée aux correctifs traditionnels qui nécessitent des efforts d’ingénierie complexes. Une fois la configuration unique terminée, aucune modification de plateforme ni aucun long cycle de développement ne sont nécessaires pour appliquer les modifications aux pages web. L’utilisateur peut publier les améliorations en quelques minutes et non pas en plusieurs semaines, sans nécessiter l’engagement des développeurs. Il s’agit d’un moyen simple et sans code d’optimiser votre site web pour les agents d’IA.

### Principaux avantages et proposition de valeur

* Diffusion **IA uniquement)** Diffuse des HTML optimisées aux agents d’IA uniquement, sans impact sur les visiteurs humains ou les robots d’optimisation du moteur de recherche (SEO).
* **Cycles plus rapides :** publiez les modifications en quelques minutes et non en quelques semaines. Aucune modification de la plateforme ou de longs cycles d’ingénierie n’est nécessaire.
* **Risque faible et réversible :** pris en charge avec une fonctionnalité de restauration en un clic qui peut rétablir la page en quelques minutes.
* **Aucun impact sur les performances :** les optimisations et la mise en cache basées sur Edge n’affectent pas la latence du site.
* **Indépendant du réseau de diffusion de contenu et de CMS :** fonctionne avec n’importe quelle configuration de réseau CDN et configuration front-end, indépendamment de CMS.

## Qui devrait l&#39;utiliser ?

Optimize at Edge est conçu pour les utilisateurs professionnels des équipes de marketing, d’optimisation du référencement, de contenu et de stratégie numérique. Il peut permettre aux utilisateurs professionnels d’effectuer l’ensemble du parcours dans LLM Optimizer : identification des opportunités, compréhension des suggestions et déploiement facile des correctifs. Avec Optimiser dans Edge, les utilisateurs et utilisatrices peuvent prévisualiser les modifications, les déployer rapidement en périphérie et vérifier que les optimisations sont actives. Les performances peuvent être suivies dans l’écosystème LLM Optimizer.

## Quelles opportunités ont été optimisées dans Edge ?

Les opportunités qui peuvent améliorer l’expérience web agentique sont prises en charge avec Optimizer sur Edge. En savoir plus sur chaque opportunité dans la section [Opportunités](/help/dashboards/opportunities.md).

## Intégration

Vous pouvez activer l’optimisation sur Edge après l’intégration à LLM Optimizer et le transfert de vos journaux CDN.

Un ingénieur du réseau CDN est nécessaire pour terminer la configuration initiale afin d’activer l’optimisation sur Edge.

Conditions requises pour la configuration :

* Générez une clé API.
* Ajoutez Optimiser au niveau des règles de routage Edge dans le réseau CDN.
* Placez sur la liste autorisée les chemins définis par l’utilisateur pour l’ensemble du domaine.
* Ajoutez une liste définie par l’utilisateur d’agents utilisateur LLM à cibler.
* Assurez-vous que le fichier robots.txt ne bloque aucun agent utilisateur destiné à cibler.
* Confirmez que l’optimisation au niveau du routage Edge est disponible dans l’interface utilisateur de LLM Optimizer.

Adobe fournit des exemples de fragments de code de configuration pour la plupart des principaux réseaux CDN afin de guider le processus de configuration. Les exemples de fragments de code inclus dans nos directives doivent être adaptés à la configuration active réelle. Adobe vous recommande d’implémenter d’abord les modifications dans les environnements inférieurs.

>[!BEGINTABS]

>[!TAB Réseau CDN géré par AEM Cloud Service (Fastly)]

**Tokowaka BYOCDN - Réseau CDN géré par Adobe**

Utilise uniquement originSelectors pour sélectionner l’origine Tokowaka.

L’exemple suivant achemine les requêtes des agents XML sur un domaine spécifique correspondant au modèle « /es/* » ou aux chemins d’accès exacts (seules les pages HTML sont acheminées). L’exemple est censé fournir un point de départ. Si votre configuration comporte plusieurs originSelectors, il est recommandé de placer celui-ci en premier.

Remarques importantes :

* x-tokowaka-request doit être vérifié avant le routage vers le serveur principal Tokowaka. Seules les requêtes qui ne disposent pas de cet en-tête doivent être acheminées vers le serveur principal Tokowaka.
* la règle originSelector qui achemine vers le serveur principal Tokowaka doit être la première de la liste s’il existe plusieurs règles.
* Le secret TOKOWAKA_API_KEY doit être déployé avant de déployer cdn.yaml

```
kind: "CDN"
version: "1"
data:
  # Origin selectors to route to Tokowaka backend
  originSelectors:
    rules:
      - name: route-to-tokowaka-backend
        when:
          allOf:
            - reqHeader: x-tokowaka-request
              exists: false # avoid loops when requests comes from Tokowaka
            - reqHeader: user-agent
              matches: "(?i)(Tokowaka-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)" # routed user agents
            - reqProperty: domain
              equals: "example.com" # routed domain
            - reqProperty: originalPath
              matches: '(/[^./]+|\.html|/)$' # routed extensions, with .html extension or without extension
            - anyOf:
              - { reqProperty: originalPath, in: [ "/page.html" ] } # routed pages, exact path matching
              - { reqProperty: originalPath, like: "/dir/*" } # routed pages, wildcard path matching
        action:
          type: selectOrigin
          originName: tokowaka-backend
          headers:
            x-tokowaka-api-key: "${{TOKOWAKA_API_KEY}}"
    origins:
      - name: tokowaka-backend
        domain: "edge.tokowaka.now"
```

>[!TAB Akamai (BYOCDN)]

**Tokowaka BYOCDN - Akamai**

```
{
    "name": "Project Tokowaka CDN Rule",
    "children": [
        {
            "name": "Connection settings",
            "children": [],
            "behaviors": [
                {
                    "name": "advanced",
                    "options": {
                        "description": "",
                        "xml": "<forward:availability.health-detect.status>off</forward:availability.health-detect.status>\n<forward:availability>\n<max-reforwards>1</max-reforwards>\n<max-reconnects>1</max-reconnects>\n</forward:availability>\n<match:forward.server-type value=\"CUSTOMER_ORIGIN\">\n<network:http.read>%(PMUSER_HTTP_READ)</network:http.read>\n<network:http.first-byte-timeout>%(PMUSER_FIRST_BYTE_TIMEOUT)</network:http.first-byte-timeout>\n<network:http.connect-timeout>%(PMUSER_HTTP_CONNECT_TIMEOUT)</network:http.connect-timeout> \n</match:forward.server-type>"
                    },
                    "uuid": "4a8c027b-1b23-44a7-8e12-f8d07e453679",
                    "templateUuid": "41c77091-419f-43f2-9a84-0b406b050cc8"
                }
            ],
            "uuid": "4759571b-8036-4c16-9b60-d3aeb84958f1",
            "criteria": [],
            "criteriaMustSatisfy": "all"
        },
        {
            "name": "Site Failover Behavior",
            "children": [],
            "behaviors": [
                {
                    "name": "failAction",
                    "options": {
                        "actionType": "RECREATED_CO",
                        "contentCustomPath": false,
                        "contentHostname": "www.adobe.com",
                        "enabled": true
                    }
                },
                {
                    "name": "advanced",
                    "options": {
                        "description": "",
                        "xml": "<forward:availability.fail-action2>\n<add-header>\n<status>on</status>\n<name>x-tokowaka-request</name>\n<value>fo</value>\n</add-header>\n</forward:availability.fail-action2>"
                    }
                }
            ],
            "uuid": "b3000c12-1ab8-49b1-a5d0-75e58bb18c9c",
            "criteria": [
                {
                    "name": "matchResponseCode",
                    "options": {
                        "lowerBound": 400,
                        "matchOperator": "IS_BETWEEN",
                        "upperBound": 599
                    }
                },
                {
                    "name": "originTimeout",
                    "options": {
                        "matchOperator": "ORIGIN_TIMED_OUT"
                    }
                }
            ],
            "criteriaMustSatisfy": "any",
            "comments": "If Tokowaka origin returns a 4xx or 5xx error (or times out), failover condition is to send the request back to Akamai and set the x-tokowaka-request header so we don't re-send the request to Tokowaka"
        }
    ],
    "behaviors": [
        {
            "name": "origin",
            "options": {
                "cacheKeyHostname": "ORIGIN_HOSTNAME",
                "compress": true,
                "customValidCnValues": [
                    "{{Origin Hostname}}",
                    "{{Forward Host Header}}",
                    "*.tokowaka.now"
                ],
                "enableTrueClientIp": true,
                "forwardHostHeader": "ORIGIN_HOSTNAME",
                "hostname": "edge.tokowaka.now",
                "httpPort": 80,
                "httpsPort": 443,
                "ipVersion": "IPV4",
                "minTlsVersion": "DYNAMIC",
                "originCertificate": "",
                "originCertsToHonor": "STANDARD_CERTIFICATE_AUTHORITIES",
                "originSni": true,
                "originType": "CUSTOMER",
                "ports": "",
                "standardCertificateAuthorities": [
                    "akamai-permissive",
                    "THIRD_PARTY_AMAZON"
                ],
                "tlsVersionTitle": "",
                "trueClientIpClientSetting": true,
                "trueClientIpHeader": "True-Client-IP",
                "verificationMode": "CUSTOM"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "transform": "NONE",
                "valueSource": "EXPRESSION",
                "variableName": "PMUSER_LLMCLIENT",
                "variableValue": "TRUE"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "caseSensitive": false,
                "extractLocation": "CLIENT_REQUEST_HEADER",
                "globalSubstitution": false,
                "headerName": "Accept-Language ",
                "regex": "^([a-zA-Z]{2}).*",
                "replacement": "$1",
                "transform": "SUBSTITUTE",
                "valueSource": "EXTRACT",
                "variableName": "PMUSER_LANG"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "transform": "NONE",
                "valueSource": "EXPRESSION",
                "variableName": "PMUSER_X_FORWARDED_HOST",
                "variableValue": "{{builtin.AK_HOST}}"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "transform": "NONE",
                "valueSource": "EXPRESSION",
                "variableName": "PMUSER_TOKOWAKA_CACHE_KEY",
                "variableValue": "LLMCLIENT={{user.PMUSER_LLMCLIENT}};LANG={{user.PMUSER_LANG}};X_FORWARDED_HOST={{user.PMUSER_X_FORWARDED_HOST}}"
            }
        },
        {
            "name": "caching",
            "options": {
                "behavior": "CACHE_CONTROL_AND_EXPIRES",
                "cacheControlDirectives": "",
                "defaultTtl": "1d",
                "enhancedRfcSupport": false,
                "honorMustRevalidate": false,
                "honorPrivate": false,
                "mustRevalidate": false
            }
        },
        {
            "name": "modifyIncomingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "X-tokowaka-api-key",
                "newHeaderValue": "<your api-key here>",
                "standardModifyHeaderName": "OTHER"
            }
        },
        {
            "name": "modifyIncomingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "x-tokowaka-config",
                "newHeaderValue": "LLMCLIENT={{user.PMUSER_LLMCLIENT}};LANG={{user.PMUSER_LANG}}",
                "standardModifyHeaderName": "OTHER"
            }
        },
        {
            "name": "modifyIncomingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "x-tokowaka-url",
                "newHeaderValue": "{{builtin.AK_URL}}",
                "standardModifyHeaderName": "OTHER"
            }
        },
        {
            "name": "cacheId",
            "options": {
                "rule": "INCLUDE_VARIABLE",
                "variableName": "PMUSER_TOKOWAKA_CACHE_KEY"
            }
        },
        {
            "name": "modifyIncomingResponseHeader",
            "options": {
                "action": "DELETE",
                "customHeaderName": "Age",
                "standardDeleteHeaderName": "OTHER"
            }
        },
        {
            "name": "prefreshCache",
            "options": {
                "enabled": true,
                "prefreshval": 90
            }
        },
        {
            "name": "modifyOutgoingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "X-Forwarded-Host",
                "newHeaderValue": "{{builtin.AK_HOST}}",
                "standardModifyHeaderName": "OTHER"
            }
        }
    ],
    "criteria": [
        {
            "name": "userAgent",
            "options": {
                "matchCaseSensitive": false,
                "matchOperator": "IS_ONE_OF",
                "matchWildcard": true,
                "values": [
                    "*Tokowaka-AI*",
                    "*ChatGPT-User*",
                    "*GPTBot*",
                    "*OAI-SearchBot*"
                ]
            }
        },
        {
            "name": "path",
            "options": {
                "matchCaseSensitive": false,
                "matchOperator": "MATCHES_ONE_OF",
                "normalize": false,
                "values": [
                ]
            }
        },
        {
            "name": "requestHeader",
            "options": {
                "headerName": "x-tokowaka-request",
                "matchOperator": "DOES_NOT_EXIST",
                "matchWildcardName": false
            }
        },
        {
            "name": "matchVariable",
            "options": {
                "matchCaseSensitive": true,
                "matchOperator": "IS",
                "matchWildcard": false,
                "variableExpression": "FALSE",
                "variableName": "PMUSER_TOKOWAKA_DISABLE"
            }
        }
    ],
    "criteriaMustSatisfy": "all"
}
```

Considérations importantes :

* La règle Tokowaka sera ON en fonction de User-Agent + Path + x-tokowaka-request (si non présente) + TOKOWAKA_DISABLE variable (pour permettre de la désactiver en utilisant un seul bouton (bascule) de variable)
* Configurez des règles pour **Modifier les en-têtes de demandes entrantes** règle pour définir des en-têtes personnalisés
* Définissez la clé de cache dans Akamai à l’aide d’une variable définie par l’utilisateur via le mécanisme de modification du Cache-ID. Une seule variable définie par l’utilisateur est autorisée. Créez donc une variable distincte pour cache_key et définissez-la en conséquence.
* Lang : extrait de l’en-tête Accept-Language à l’aide de « regex » : « ^([a-zA-Z]{2}).* »
* Avec la modification de l’ID de cache dans une correspondance sur l’agent utilisateur, le contenu ne peut pas être purgé par URL (uniquement à titre d’information)
* Mécanisme de basculement de site : avec la correspondance sur la règle Agent-utilisateur, Akamai ne permet pas le basculement en fonction du contrôle d’intégrité, mais uniquement en fonction de la réponse/connectivité d’origine par requête. Définissez l’en-tête resp **x-tokowaka-fo:true** en cas de réponse de basculement.
* Le SWR n’est pas pris en charge par Akamai. Ainsi, seule la mise en cache basée sur TTL est présente. Par conséquent, configurez une règle dans Akamai pour supprimer l’en-tête Age de la réponse d’origine, sinon la mise en cache basée sur TTL ne fonctionnerait pas.
* Assurez-vous que la règle Tokowaka est la règle la plus basse de la hiérarchie des règles (afin qu’elle remplace toutes les autres règles).

>[!TAB Fastly (BYOCDN)]

**Tokowaka BYOCDN - Fastly - VCL**

![Fastly VCL](/help/assets/optimize-at-edge/fastly-vcl.png)

![Ajouter des fragments de code VCL](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**fragment de code vcl_recv**

```
unset req.http.x-tokowaka-url;
unset req.http.x-tokowaka-config;
unset req.http.x-tokowaka-api-key;

if (!req.http.x-tokowaka-request
    && req.http.user-agent ~ "(?i)(Tokowaka-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-fowarded-host = req.http.host; # required for identifying the original host
  set req.http.x-tokowaka-url = req.url; # required for identifying the original url
  set req.http.x-tokowaka-config = "LLMCLIENT=true"; # required for cache key
  set req.http.x-tokowaka-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.backend = F_Tokowaka;
}
```

**fragment de code vcl_hash**

```
if (req.http.x-tokowaka-config) {
  set req.hash += "tokowaka";
  set req.hash += req.http.x-tokowaka-config;
}
```

**fragment de code vcl_delivery**

```
if (req.http.x-tokowaka-config && resp.status >= 400) {
  set req.http.x-tokowaka-request = "failover";
  set req.backend = F_Default_Origin;
  restart;
}

if (!req.http.x-tokowaka-config && req.http.x-tokowaka-request == "failover") {
  set resp.http.x-tokowaka-fo = "1";
}
```

>[!ENDTABS]


Pour les autres fournisseurs de réseau CDN, contactez llmo-at-edge@adobe.com pour aider vos équipes informatiques/CDN à l’intégration.

<!--This should probably be included Opportunities dashboard content. Content also needs serious editing - lots of "customer needs"and business user" etc.-->

Une fois les configurations terminées, les utilisateurs professionnels peuvent déployer des suggestions d’optimisation lors d’opportunités Edge dans LLM Optimizer.

## Opportunités

| Opportunité | Type | Auto-identification | Suggestion automatique | Optimiser automatiquement |
|---------|----------|----------|----------|----------|
| Récupérer la visibilité du contenu | GÉOLOCALISATION TECHNIQUE | Détecte les pages où le contenu critique est masqué aux agents d’IA. Affiche les URL affectées et le contenu attendu qui peut être récupéré. | Met en évidence le contenu qui peut être rendu disponible pour les agents d’IA et recommande d’activer le pré-rendu pour ces pages. | Fournit un instantané d’HTML complet et convivial pour l’IA au trafic d’agents qui récupère le contenu précédemment masqué. |
| Optimiser les en-têtes pour l’IA | Optimisation du contenu | Analyse les en-têtes pour détecter les en-têtes vides, en double, manquants ou ambigus qui peuvent réduire la lisibilité de la machine. | Propose une hiérarchie d’en-têtes plus épurée et des libellés améliorés, et affiche un aperçu de la structure mise à jour pour chaque page. | Injecte la structure d’en-tête améliorée pour les agents d’IA, préservant votre conception visuelle tout en rendant la page plus compréhensible pour les LLM. |
| Ajouter des résumés compatibles avec l’IA | Optimisation du contenu | Identifie les pages longues ou complexes qui ne disposent pas de résumés concis au niveau de la page ou de la section, ce qui les rend plus difficiles à analyser et à comprendre rapidement par l’IA. | Recommande des résumés courts générés par l’IA au niveau de la page et de la section qui capturent le contenu clé. | Insère les résumés dans les sections HTML appropriées, améliorant la façon dont les modèles interprètent et décrivent le contenu de la page. |
| Ajout de questions fréquentes pertinentes | Optimisation du contenu | Détecte les trous d’intention dans le contenu de page existant qui pourraient tirer parti des questions fréquentes. | Suggère du contenu de FAQ généré par l’IA aligné sur les intentions des utilisateurs et les rubriques existantes. | Injecte le contenu des FAQ dans HTML, ce qui rend les pages plus détectables et pertinentes dans les réponses pilotées par l’IA. |
| Simplification des contenus complexes | Optimisation du contenu | Indique les pages avec du texte complexe qui peut entraver la compréhension de l’IA. | Fournit des versions simplifiées de tests complexes générées par l’IA tout en conservant leur signification d’origine. | Réécrit des sections complexes dans la page, améliorant ainsi la lisibilité de l’IA. |

### Récupérer la visibilité du contenu

Cette opportunité signale les pages où le contenu clé est masqué pour les agents d’IA en raison du rendu côté client. Pour chaque page identifiée, il vous indique exactement quel contenu est absent de la vue de l’agent d’IA, met en évidence les écarts de visibilité et vous permet d’appliquer directement des modifications pour récupérer le contenu masqué. Lorsque vous déployez cette opportunité avec Optimize sur Edge, une version pré-générée et optimisée par l’IA de la page est diffusée aux agents utilisateurs LLM afin qu’ils puissent accéder au contexte complet sans exécuter Javascript.

**Cette fonctionnalité de pré-rendu s’applique automatiquement à toutes les opportunités qui suivent lorsqu’elles sont déployées avec Optimizer sur Edge.** Cela garantit d’abord que la page est entièrement visible par les agents d’IA. Des améliorations supplémentaires sont apportées en plus de ce rendu HTML prédéfini.

#### Outils supplémentaires

Votre page Web est-elle accessible ? Le [Adobe LLM Optimizer : votre page web est-elle accessible ?](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc)’extension Chrome vous permet de voir exactement à quelle proportion du contenu de votre page web les LLM peuvent accéder et ce qui reste masqué. Conçu comme un outil de diagnostic autonome et gratuit, il ne nécessite aucune licence de produit ni configuration.

En un seul clic, vous pouvez évaluer la lisibilité de la machine de n’importe quel site, afficher côte à côte ce que voient les agents d’IA par rapport à ce que voient les utilisateurs humains et estimer la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer. Voir [ L’IA peut-elle lire votre site web ?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) pour plus d’informations.

### Optimiser les en-têtes pour les LLM

Cette opportunité détecte les pages où la structure des en-têtes rend difficile, pour les agents d’IA, la compréhension de la page en raison de titres vides, en double, manquants ou ambigus. Pour chaque page affectée, l’opportunité fait apparaître les en-têtes sous-optimaux et recommande une hiérarchie plus claire. Lorsqu’ils sont déployés avec Optimize sur Edge, les en-têtes améliorés sont appliqués dans HTML au trafic agent, ce qui peut améliorer la lisibilité de la machine tout en laissant votre disposition face aux humains inchangée.

### Ajouter des résumés compatibles avec LLM

Cette opportunité identifie les pages qui peuvent bénéficier de résumés concis pour aider les ILM à comprendre rapidement le sujet de la page. Pour chaque page, l’opportunité détecte où un résumé est le plus nécessaire et crée des résumés générés par l’IA au niveau de la page et/ou de la section. Lorsque vous effectuez un déploiement avec Optimize sur Edge, ces résumés sont insérés dans l’HTML que les agents d’IA récupèrent, ce qui améliore les chances de voir votre contenu décrit plus précisément.

### Ajout de questions fréquentes pertinentes

Cette opportunité signale les pages où un contenu de questions/réponses supplémentaire pourrait mieux correspondre à l’intention et aux invites de l’utilisateur dans la découverte pilotée par l’IA. Pour chaque page, il propose des blocs de FAQ générés par l’IA liés à l’intention de l’utilisateur et au contenu de la page. Avec Optimize sur Edge, ces questions fréquentes sont insérées dans HTML, ce qui rend votre page plus conviviale pour l’IA et augmente la probabilité que les réponses de l’IA reflètent directement vos conseils.

### Simplification des contenus complexes

Cette opportunité trouve des pages avec des paragraphes longs et complexes qui peuvent réduire la compréhension de l’IA. Pour chaque page qui dépasse les seuils de lisibilité, il crée un contenu généré par l’IA plus simple et plus facile à analyser tout en conservant sa signification d’origine. Lorsqu’il est déployé en périphérie, le contenu simplifié diffusé au trafic d’agence aide les gestionnaires de contenu de terrain à interpréter et résumer votre contenu plus fidèlement.

## Suggestions

Pour chaque opportunité, vous pouvez prévisualiser, modifier, déployer, prévisualiser en direct et restaurer les optimisations en périphérie.

### Prévisualisation

L’aperçu permet aux utilisateurs de voir l’impact d’une suggestion sur la page avant que tout soit mis en ligne. Elle fait apparaître une différence côte à côte entre la page active et la version optimisée pour l’IA attendue après l’application de la suggestion. Cette vue utilise la même logique Optimiser pour Edge qui alimentera le trafic en direct, mais en mode d’aperçu sécurisé et isolé. Cela n’a aucune incidence sur le trafic en direct, car il s’agit d’une simulation en lecture seule pour révision.

![Prévisualisation](/help/assets/optimize-at-edge/preview.png)

### Modifier

La modification permet aux utilisateurs d’affiner ou de réécrire complètement la suggestion générée automatiquement avant de la déployer. Au lieu d’accepter passivement la suggestion, les utilisateurs et utilisatrices conservent un contrôle total par le biais de ce workflow intégré. La vue affiche les modifications proposées dans un éditeur structuré, où les utilisateurs et utilisatrices peuvent modifier le texte pour mieux correspondre à leur intention. La version modifiée sera ensuite diffusée aux agents d’IA une fois déployée.

![Modifier](/help/assets/optimize-at-edge/edit.png)

### Déployer

Déployer publie les suggestions sélectionnées afin que les expériences optimisées puissent être diffusées de la périphérie aux agents d’IA. Si le réseau CDN est entièrement routé, toutes les pages du domaine sont mises en ligne avec les nouvelles modifications, généralement en quelques minutes. Placer sur la liste autorisée Si le routage a été configuré pour des chemins sélectionnés uniquement, seules les pages sélectionnées sont mises en ligne avec les optimisations.

![Déployer](/help/assets/optimize-at-edge/deploy.png)

### Afficher en direct

L’option Afficher en direct permet aux utilisateurs et utilisatrices de vérifier que l’optimisation est en ligne et se comporte comme prévu pour le trafic d’agents, une vue qui serait autrement difficile d’accès. Les utilisateurs peuvent afficher la page active sous Suggestions fixes , ce qui rend la page telle qu’affichée pour les agents d’IA.

![Afficher en direct](/help/assets/optimize-at-edge/view-live.png)

### Restaurer

La restauration en toute sécurité rétablit une optimisation précédemment déployée. La version AI uniquement de la page est généralement renvoyée à son état précédent en quelques minutes, ce qui permet aux utilisateurs et aux utilisatrices de tester en toute sécurité les optimisations si nécessaire.

![Restaurer](/help/assets/optimize-at-edge/rollback.png)

## Questions fréquentes

Q. Quels types de gestion du cycle de vie ciblez-vous avec Optimize chez Edge ?

La liste des agents utilisateur à cibler est entièrement définie par le client lors de l’intégration.

Q. Que signifie « Edge » dans Optimize sur Edge ?

Dans notre cas, « Edge » signifie que l’optimisation est appliquée au niveau de la couche du réseau CDN et non au sein de votre CMS.

Q. Pourquoi cette optimisation nécessite-t-elle un réseau CDN ?

Le réseau CDN est l’endroit où la version optimisée de la page est assemblée et diffusée aux agents d’IA. Nous utilisons le réseau CDN pour nous assurer que votre CMS d’origine reste inchangé. Cette séparation vous permet d’améliorer la visibilité de LLM sans modifier vos workflows de publication existants.

Q. Que se passe-t-il si je ne suis pas encore intégré à Optimize sur Edge ?

Si vous cliquez sur **Déployer les optimisations** avant d’avoir terminé la configuration requise, rien ne sera appliqué à votre site. Au lieu de cela, une boîte de dialogue contextuelle vous invite à contacter notre équipe à l’adresse llmo-at-edge@adobe.com pour obtenir de l’aide sur l’intégration. Jusqu’à ce que l’intégration soit terminée, vous pouvez toujours explorer les opportunités et les suggestions détectées, mais le workflow de déploiement en un clic restera inactif.

Q : Que se passe-t-il lorsque le contenu est mis à jour à la source ?

Nous diffusons la version optimisée de la page à partir du cache tant que la page source sous-jacente n’a pas changé. Cependant, lorsque la source change, notre système s’actualise automatiquement afin que les agents d’IA reçoivent toujours le contenu le plus récent. En effet, nous utilisons des TTL de cache faibles par ordre de minutes afin que toute mise à jour de contenu sur votre site déclenche une nouvelle optimisation dans cette fenêtre. Comme il n’existe pas de TTL universelle adaptée à chaque site, nous pouvons configurer cette TTL en fonction de vos règles d’invalidation du cache afin de nous assurer que les deux systèmes restent synchronisés.

Q. L’optimisation sur Edge est-elle réservée aux sites qui utilisent Adobe Edge Delivery Service (EDS) ?

Non. Le service Optimize at Edge est compatible avec le réseau CDN et fonctionne avec n’importe quelle architecture front-end, et pas seulement avec celles déployées sur la pile Adobe EDS.

Q. En quoi le pré-rendu d’Optimisation sur Edge diffère-t-il du rendu côté serveur (SSR) traditionnel ?

Les deux résolvent des problèmes différents et peuvent fonctionner ensemble. Le rendu côté serveur traditionnel effectue le rendu du contenu côté serveur, mais n’inclut pas le contenu chargé ultérieurement dans le navigateur. Le pré-rendu Optimiser sur Edge capture la page après le chargement des données côté client et JavaScript, produisant ainsi la version entièrement assemblée à la périphérie du réseau CDN. Le rendu côté serveur se concentre sur l’amélioration de l’expérience humaine et Optimiser chez Edge améliore l’expérience web pour les LLM.


















