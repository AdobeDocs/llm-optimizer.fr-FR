---
title: Trafic bloqué par robots.txt
description: Découvrez comment LLM Optimizer détecte que votre fichier robots.txt empêche les agents IA d’accéder à votre contenu et comment corriger ce problème.
feature: Opportunities
autotag-review: '2026-07-15T18:04:23.113Z'
TQID: 'https://experienceleague.adobe.com/rk82xEtvYBr47tTNzhC6ZbFw1Bim3Otr-D2ncBWPmwM'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2:
  - id: e0ec491f-fe51-42b6-801c-1c0dfcc0e64f
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 817
ht-degree: 100%

---


# Trafic bloqué par robots.txt

Votre fichier `robots.txt` contrôle les robots d’exploration qui peuvent accéder à votre site. Lorsque les agents IA sont bloqués de manière sélective du contenu qui est autrement accessible aux robots d’exploration généraux, ces agents ne peuvent pas indexer ou citer ce contenu, ce qui réduit directement la visibilité de votre marque dans les réponses générées par l’IA.

L’opportunité Trafic bloqué par robots.txt analyse votre fichier `robots.txt` par rapport à vos pages les plus consultées et identifie les règles qui empêchent les agents IA d’accéder au contenu auquel ils devraient pouvoir accéder. Elle permet d’afficher les résultats au niveau de chaque ligne de `robots.txt` afin que vous puissiez vérifier et mettre à jour des directives spécifiques plutôt que d’auditer manuellement l’ensemble du fichier.

Elle met en évidence deux mesures clés en un coup d’œil :

- **Nombre total d’URL** : nombre d’URL affectées par les règles de blocage dans votre `robots.txt`.
- **Agents bloqués** : nombre d’agents IA dont l’accès à ces URL est bloqué.

![Tableau de bord Trafic bloqué par robots.txt](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-overview.png)

## Fonctionnement

LLM Optimizer récupère votre fichier `robots.txt` et compare vos pages les plus consultées à six principaux agents utilisateurs d’agent IA :

- ClaudeBot
- GPTBot
- OAI-SearchBot
- OAI-User
- PerplexityBot
- Perplexity-User

Une URL n’est signalée que lorsqu’elle est **autorisée pour l’agent utilisateur générique (`*`), mais interdite pour un agent IA spécifique**. Le blocage général — où tous les robots d’exploration sont soumis aux mêmes restrictions — n’est pas signalé. L’audit cible spécifiquement l’exclusion sélective des agents IA, ce qui représente le résultat la plus exploitable pour GEO.

>[!NOTE]
>Cette opportunité n’utilise pas l’IA pour développer ou diffuser des suggestions. Les résultats sont entièrement basés sur l’analyse directe de votre fichier `robots.txt`.

Les résultats s’affichent dans deux onglets : **robots.txt** et **Détails du trafic bloqué par l’agent**.

## robots.txt

Cet onglet affiche l’intégralité du fichier `robots.txt` avec les directives de blocage mises en évidence en rouge. Chaque ligne mise en évidence représente une règle qui empêche de manière sélective un ou plusieurs agents IA d’accéder à une URL qui est autrement accessible au public.

![vue robots.txt avec directives de blocage mises en évidence](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-robotstxt.png)

Cliquez sur une directive mise en évidence pour afficher plus d’informations sur son impact et sur la correction suggérée.

## Détails du trafic bloqué par agent

Cet onglet présente une répartition du trafic bloqué, organisée par agent IA. Pour chaque agent bloqué, il affiche :

- **Description du problème** : une explication indiquant quel agent est bloqué et l’importance de ce blocage.
- **Résolution** : instructions pour ouvrir le fichier`robots.txt` et examiner le numéro de ligne spécifique indiqué à côté de chaque URL concernée.
- Un tableau des URL affectées avec la **Ligne**, le **Classement** et l’**URL** pour chaque page bloquée.

Chaque agent (par exemple, OAI-User, GPTBot, OAI-SearchBot) possède son propre sous-onglet afin que vous puissiez traiter les blocs par agent.

## Résolution

Pour résoudre un problème d’agent bloqué, ouvrez votre fichier `robots.txt` et repérez le numéro de ligne indiqué à côté de chaque URL concernée dans l’onglet Détails du trafic bloqué par agent. Mettez à jour ou supprimez la directive d’interdiction pour l’agent d’IA concerné afin d’autoriser l’accès à l’URL affectée.

Par exemple, pour débloquer GPTBot sur une page spécifique, supprimez ou mettez à jour la directive :

```
User-agent: GPTBot
Disallow: /blog/cold-brewing-101
```

Une fois votre fichier `robots.txt` mis à jour et republié, LLM Optimizer détectera le changement lors de la prochaine exécution d’audit et marquera la suggestion comme résolue.

## Tester l’opportunité avec la démo

Découvrez l’opportunité « Trafic bloqué par robots.txt » en action grâce à l’environnement de démonstration Frescopa.

[Afficher le trafic bloqué par robots.txt dans la démo Frescopa](https://play.llmo.now/org/demo-org/opportunities/blocked-urls-llm-agents)

## Questions fréquentes

**Pourquoi est-il important pour GEO de bloquer les agents IA ?**

La GEO exige que les robots d’exploration IA puissent accéder au contenu de votre site et l’indexer. Le blocage direct des agents IA empêche vos pages d’apparaître dans les réponses générées par l’IA, réduisant ainsi les citations, les mentions de marque et la visibilité globale dans l’IA. Le blocage d’une seule page à fort trafic peut à elle seule représenter une perte significative de la visibilité de marque générée par l’IA.

**Quelle est la différence entre un blocage général et un blocage sélectif ?**

Le blocage général signifie que tous les robots d’indexation, y compris les robots d’indexation Web généralistes, sont interdits d’accès à une page. Le blocage sélectif signifie que les robots d’indexation généralistes peuvent accéder à la page, mais pas les agents IA spécifiques. Cette opportunité n’indique que le blocage sélectif car il représente une exclusion intentionnelle ou accidentelle d’agents IA d’un contenu qui est sinon public, ce qui constitue le résultat le plus exploitable.

**Quels agents IA LLM Optimizer vérifie-t-il ?**

LLM Optimizer vérifie les agents ClaudeBot, GPTBot, OAI-SearchBot, OAI-User, PerplexityBot et Perplexity-User.

**Comment dois-je faire pour bloquer intentionnellement certains agents IA ?**

Vous pouvez examiner chaque directive marquée et choisir de conserver le bloc intentionnellement. Les suggestions ignorées sont conservées lors des exécutions d’audit et ne seront pas réaffichées à moins que le fichier `robots.txt` ne soit modifié et que la règle ne réapparaisse.

**Comment LLM Optimizer applique-t-il un suivi des modifications apportées à mon fichier robots.txt au fil du temps ?**

LLM Optimizer utilise le hachage pour suivre le contenu de votre `robots.txt` au fil des différentes exécutions. Si une règle de blocage précédemment résolue réapparaît (par exemple, après une mise à jour du fichier `robots.txt`), elle sera réaffichée sous la forme d’une nouvelle suggestion.

**Comment les meilleures pages sont-elles déterminées ?**

Les pages sont récupérées à partir d’une combinaison de vos pages en référencement naturel (SEO) dont le trafic est le plus élevé, des principales URL visitées par les agents IA à partir des journaux du réseau CDN et de toutes les URL personnalisées spécifiées dans la configuration de votre site.
