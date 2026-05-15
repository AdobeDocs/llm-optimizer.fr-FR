---
title: Erreurs de trafic d’agent
description: Découvrez comment LLM Optimizer détecte les erreurs HTTP rencontrées par les agents d’IA qui explorent à votre site et comment les corriger pour améliorer l’accessibilité du contenu et la visibilité de l’IA.
feature: Opportunities
autotag-review: '2026-05-15T17:32:31.900Z'
TQID: 'https://experienceleague.adobe.com/9Gbva-14SNt8A0G0B2Qu26OOp34L5NaM0z6lCv4yrTg'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: e06fae5f-830b-4222-a469-b5e148d36465
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 1045
ht-degree: 1%

---


# Erreurs de trafic d’agent

Les agents d’IA qui explorent à votre site rencontrent les mêmes erreurs HTTP que les navigateurs humains, mais les conséquences sont différentes. Lorsqu’un agent d’IA rencontre une erreur 404, 403 ou 5xx, il ne peut pas accéder à ce contenu ni le citer, ce qui réduit directement la visibilité de votre marque dans les réponses générées par l’IA.

L’opportunité Erreurs de trafic d’agent surveille vos journaux CDN à la recherche d’erreurs HTTP renvoyées aux agents AI et fait apparaître les URL affectées avec leurs volumes d’accès et leurs suggestions de correctifs. Il couvre trois types d’erreurs, chacun ayant sa propre opportunité dans le tableau de bord :

- **404 Introuvable** — Liens rompus qui empêchent les agents d&#39;IA d&#39;accéder au contenu qui n&#39;existe plus à l&#39;URL prévue.
- **403 Interdit** — Restrictions d’accès qui bloquent les robots d&#39;exploration d’IA du contenu auquel ils devraient pouvoir accéder.
- **5xx Server Errors** : instabilité côté serveur qui rend le contenu temporairement ou de manière persistante indisponible pour les agents d&#39;IA.

Chaque type d’erreur peut apparaître comme une opportunité distincte dans votre tableau de bord, selon les erreurs détectées pour votre site.

L’opportunité fait également apparaître deux mesures clés pour chaque type d’erreur :

- **Nombre total d’URL** — Nombre d’URL uniques renvoyant des erreurs aux agents d’IA.
- **Nombre total d’accès** — Nombre total de réponses d’erreur enregistrées pour toutes les requêtes d’agent AI.

![Tableau de bord des erreurs de trafic agent présentant des mesures récapitulatives et des détails sur les erreurs](/help/dashboards/opportunities/assets/agentic-traffic-errors-overview.png)

## Fonctionnement

LLM Optimizer interroge vos journaux CDN via Athena pour identifier les URL qui renvoient des codes d’état 404, 403 ou 5xx aux agents utilisateurs de l’agent d’IA. Les agents utilisateurs incluent ChatGPT, Claude, Perplexity et Gemini. Jusqu’à 500 URL par audit sont analysées et classées par volume de trafic. Par défaut, l’audit s’exécute toutes les semaines.

Les URL sont validées avant d’être affichées pour filtrer les faux positifs et les données obsolètes. LLM Optimizer teste à nouveau chaque URL pour confirmer son statut actuel et compare les réponses de l’agent AI aux réponses du navigateur humain afin d’identifier les problèmes spécifiques au robot d&#39;exploration.

Pour les erreurs **404** les suggestions sont optimisées par l’IA. Par conséquent, LLM Optimizer analyse la structure et le contenu de l’URL rompue pour recommander d’autres URL qui préservent l’intention de l’utilisateur, ainsi qu’un score de confiance et une justification expliquant la recommandation.

Pour les erreurs **403 et 5xx**, les suggestions sont basées sur des modèles, fournissant des conseils ciblés pour chaque type d’erreur.

## Tableau des détails des erreurs

Le tableau des détails de l’erreur répertorie toutes les URL affectées, filtrées par **Agent utilisateur**, **Code de pays** et **Catégorie**. Pour chaque URL, il affiche :

- **URL** — Page concernée.
- **Total** — Nombre total d’accès en erreur provenant des agents d’IA.
- Le nombre d’accès hebdomadaires pour les dernières semaines vous permet de déterminer si le problème est persistant ou s’il s’améliore.

![Tableau des détails des erreurs avec filtres et colonnes d’accès hebdomadaires](/help/dashboards/opportunities/assets/agentic-traffic-errors-table.png)

## Détails des suggestions

Cliquez sur n’importe quelle suggestion pour ouvrir un panneau **Détails de la suggestion** affichant les éléments suivants :

- L’URL affectée et l’action recommandée ; par exemple, « Doit être une URL valide ou être redirigé vers une autre URL ».
- Un graphique **Statistiques** indiquant le nombre total d’accès par semaine par agent utilisateur de l’agent AI, afin que vous puissiez comprendre l’impact sur le trafic et si le problème est persistant ou s’il s’améliore.
- Actions **Partager** et **Ignorer** pour gérer la suggestion.

![Panneau Détails des suggestions pour un graphique 404 avec statistiques](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion.png)

Dans certains cas **5xx** (et similaires), le panneau peut noter qu’aucune autre URL de même domaine n’est disponible et expliquer comment les recommandations suivent les règles de domaine et de liste. Par exemple, en suggérant l’URL du domaine de base pour conserver la valeur SEO lorsqu’une correspondance plus proche ne peut pas être proposée.

![Panneau Détails de la suggestion en cas d’erreur de serveur avec un message d’explication](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion-503.png)

## Résolution

Le correctif dépend du type d’erreur :

**404 erreurs** — La suggestion inclut une ou plusieurs URL alternatives recommandées par l’IA, en fonction de la structure et du contenu de l’URL rompue, ainsi qu’un score de confiance et une justification. Implémentez une redirection côté serveur à partir de l’URL rompue vers l’alternative suggérée pour restaurer l’accès à l’agent AI et préserver la visibilité du contenu.

**403 errors** — Vérifiez les autorisations d&#39;accès pour vous assurer que les robots d&#39;exploration d&#39;IA ne sont pas bloqués du contenu auquel ils devraient pouvoir accéder. Plus précisément :
- Vérifier les autorisations d’accès — robot d&#39;exploration d’IA bloqué.
- Vérifiez que les paramètres de sécurité ne bloquent pas les robots d&#39;exploration légitimes.

Erreurs **5xx** — Examinez les problèmes côté serveur affectant les pages marquées. Plus précisément :
- Vérifiez la stabilité du serveur pour les pages à trafic élevé.
- Recherchez des erreurs récurrentes dans les journaux d’application.
- Surveillez l’intégrité et la capacité des infrastructures.

## Faites un essai dans la démonstration

Consultez l’opportunité Erreurs de trafic d’agent en action à l’aide de l’environnement de démonstration Frescopa.

- [Afficher les erreurs 404 dans la démo Frescopa](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-4xxs)
- [Afficher les erreurs 5xx dans la démo Frescopa](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-5xxs)

## Questions fréquentes

**Pourquoi les erreurs HTTP sont-elles importantes pour la visibilité de l’IA ?**

Dans les systèmes de récupération augmentée, les robots d&#39;exploration d’IA découvrent des liens et tentent de récupérer le contenu de la page pour l’inclure dans leurs réponses. Si une page est manquante, renvoie une erreur ou est inaccessible, son contenu ne peut pas être récupéré ou cité. La correction directe de ces erreurs techniques améliore la probabilité que votre contenu soit correctement indexé et cité par les systèmes d’IA.

**Quelle est la différence entre une erreur 404 et une erreur 403 ?**

Une erreur 404 signifie que la page n’existe pas à l’URL demandée. Elle a été supprimée ou déplacée sans redirection. Une erreur 403 signifie que la page existe mais que l’accès est refusé, soit à tous les robots d&#39;exploration, soit spécifiquement aux agents d’IA. Les deux empêchent les agents d’IA d’accéder à votre contenu, mais le correctif est différent pour chacun d’eux.

**Pourquoi une erreur 403 peut-elle uniquement affecter les agents d’IA et non les visiteurs humains ?**

Certaines configurations de sécurité ou certains paramètres de contrôle d’accès peuvent bloquer les agents utilisateurs de l’agent AI du contenu auquel les visiteurs humains peuvent accéder normalement. LLM Optimizer signale spécifiquement ces cas en comparant les réponses de l’agent AI aux réponses du navigateur humain.

**Comment les faux positifs sont-ils filtrés ?**

LLM Optimizer teste à nouveau les URL pour confirmer leur statut actuel avant de les afficher sous forme de suggestions et compare les réponses de l’agent AI aux réponses du navigateur humain afin d’identifier les problèmes spécifiques au robot d&#39;exploration. Les URL qui ne renvoient plus d’erreurs ne s’affichent pas.

**À quelle fréquence l’analyse est-elle mise à jour ?**

L’audit s’exécute toutes les semaines par défaut, extrayant les données d’erreur des journaux CDN de la semaine précédente. Le tableau des détails des erreurs affiche le nombre d’accès hebdomadaires afin que vous puissiez suivre les tendances au fil du temps.

**Quels agents d’IA sont surveillés ?**

LLM Optimizer surveille les réponses d’erreur de tous les modèles d’agent utilisateur de l’agent AI détectés, y compris les robots d&#39;exploration ChatGPT, Claude, Perplexité et Gemini.
