---
title: Trafic bloqué par robots.txt
description: Découvrez comment LLM Optimizer détecte que votre fichier robots.txt empêche les agents d’IA d’accéder à votre contenu et comment le corriger.
feature: Opportunities
autotag-review: '2026-05-15T18:00:25.453Z'
TQID: 'https://experienceleague.adobe.com/9LGbxeIbWYZp-MN5Zww6g-dQ6BZT0IWzlA7XB-2Xlho'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 817
ht-degree: 1%

---


# Trafic bloqué par robots.txt

Votre fichier `robots.txt` contrôle les robots d&#39;exploration qui peuvent accéder à votre site. Lorsque les agents d’IA sont bloqués de manière sélective du contenu qui est autrement accessible aux robots d&#39;exploration généraux, ces agents ne peuvent pas indexer ou citer ce contenu, ce qui réduit directement la visibilité de votre marque dans les réponses générées par l’IA.

L’opportunité Trafic bloqué par robots.txt analyse votre fichier `robots.txt` par rapport à vos pages les plus consultées et identifie les règles qui empêchent les agents d’IA d’accéder au contenu qu’ils devraient être en mesure d’atteindre. Il permet d’afficher les résultats au niveau de chaque ligne de `robots.txt` afin que vous puissiez réviser et mettre à jour des directives spécifiques plutôt que d’auditer manuellement l’ensemble du fichier.

Il fait apparaître deux mesures clés en un coup d’œil :

- **Nombre total d’URL** — Nombre d’URL affectées par les règles de blocage dans votre `robots.txt`.
- **Agents bloqués** — Nombre d’agents AI dont l’accès à ces URL est bloqué.

![Trafic bloqué par le tableau de bord robots.txt](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-overview.png)

## Fonctionnement

LLM Optimizer récupère votre fichier `robots.txt` et compare vos pages les plus consultées à six principaux agents utilisateurs d’agents AI :

- ClaudeBot
- GPTBot
- OAI-SearchBot
- OAI-User
- PerplexityBot
- Perplexity-User

Une URL n’est marquée que lorsqu’elle est **autorisée pour l’agent utilisateur de caractères génériques (`*`), mais interdite pour un agent d’IA spécifique**. Le blocage général — où tous les robots d&#39;exploration sont soumis aux mêmes restrictions — n&#39;est pas signalé. L&#39;audit cible spécifiquement l&#39;exclusion sélective des agents d&#39;IA, qui représente la constatation la plus exploitable pour GEO.

>[!NOTE]
>Cette opportunité n’utilise pas l’IA pour développer ou diffuser des suggestions. Les résultats sont entièrement basés sur l&#39;analyse directe de votre fichier `robots.txt`.

Les résultats s’affichent dans deux onglets : **robots.txt** et **Détails du trafic bloqué par l’agent**.

## robots.txt

Cet onglet affiche l’intégralité du fichier `robots.txt` avec les directives de blocage mises en surbrillance en rouge. Chaque ligne mise en surbrillance représente une règle qui bloque de manière sélective un ou plusieurs agents d’IA d’accéder à une URL qui est autrement accessible au public.

![vue robots.txt avec directives de blocage mises en surbrillance](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-robotstxt.png)

Cliquez sur une directive mise en surbrillance pour afficher plus d’informations sur son impact et sur le correctif suggéré.

## Détails du trafic bloqué par agent

Cet onglet fournit une répartition du trafic bloqué organisé par l’agent IA. Pour chaque agent bloqué, il affiche :

- **Description du problème** — Une explication de l’agent bloqué et de son importance.
- **Résolution** — Conseils pour ouvrir le fichier `robots.txt` et consulter le numéro de ligne spécifique indiqué à côté de chaque URL affectée.
- Tableau des URL affectées avec les **Ligne**, **Classement** et **URL** pour chaque page bloquée.

Chaque agent (par exemple, OAI-User, GPTBot, OAI-SearchBot) possède son propre sous-onglet afin que vous puissiez adresser des blocs par agent.

## Résolution

Pour résoudre une recherche d’agent bloquée, ouvrez votre fichier `robots.txt` et recherchez le numéro de ligne affiché à côté de chaque URL affectée dans l’onglet Détails du trafic bloqué par l’agent . Mettez à jour ou supprimez la directive d’interdiction pour l’agent d’IA approprié afin d’autoriser l’accès à l’URL affectée.

Par exemple, pour débloquer GPTBot à partir d’une page spécifique, supprimez ou mettez à jour la directive :

```
User-agent: GPTBot
Disallow: /blog/cold-brewing-101
```

Une fois votre fichier `robots.txt` mis à jour et republié, LLM Optimizer détectera la modification lors de la prochaine exécution d’audit et marquera la suggestion comme résolue.

## Faites un essai dans la démonstration

Consultez l’opportunité Trafic bloqué par robots.txt en action à l’aide de l’environnement de démonstration Frescopa.

[Afficher le trafic bloqué par robots.txt dans la démo Frescopa](https://play.llmo.now/org/demo-org/opportunities/blocked-urls-llm-agents)

## Questions fréquentes

**Pourquoi le blocage des agents d’IA est-il important pour GEO ?**

L’optimisation du moteur de génération nécessite que les robots d&#39;exploration d’IA puissent accéder au contenu de votre site et l’indexer. Le blocage des agents d’IA empêche directement vos pages d’apparaître dans les réponses générées par l’IA, ce qui réduit les citations, les mentions de marque et la visibilité globale de l’IA. Même une seule page à trafic élevé bloquée peut représenter une perte significative de l’exposition de la marque pilotée par l’IA.

**Quelle est la différence entre blocage général et blocage sélectif ?**

Le blocage global signifie que tous les robots d&#39;exploration, y compris les robots d&#39;exploration web généraux, sont interdits à partir d’une page. Le blocage sélectif signifie que les robots d&#39;exploration généraux peuvent accéder à la page, mais pas les agents d’IA spécifiques. Cette opportunité ne signale que le blocage sélectif, car il représente une exclusion intentionnelle ou accidentelle des agents d’IA du contenu qui est par ailleurs public, ce qui est la conclusion la plus exploitable.

**Quels agents d’IA LLM Optimizer vérifie-t-il ?**

LLM Optimizer vérifie ClaudeBot, GPTBot, OAI-SearchBot, OAI-User, PerplexityBot et Perplexity-User.

**Que faire si je souhaite intentionnellement bloquer certains agents d’IA ?**

Vous pouvez passer en revue chaque directive marquée et choisir de conserver le bloc intentionnellement. Les suggestions ignorées sont conservées lors des exécutions d’audit et ne seront pas réaffichées à moins que le fichier `robots.txt` ne change et que la règle ne réapparaisse.

**Comment LLM Optimizer suit-il les modifications apportées à mon fichier robots.txt au fil du temps ?**

LLM Optimizer utilise le hachage pour suivre le contenu `robots.txt` sur plusieurs exécutions. Si une règle de blocage précédemment résolue réapparaît (par exemple, après une mise à jour de `robots.txt`), elle sera réaffichée sous la forme d’une nouvelle suggestion.

**Comment les pages principales sont-elles déterminées ?**

Les pages sont sourcées à partir d’une combinaison de vos pages d’optimisation du moteur de recherche (SEO) à trafic le plus élevé, des principales URL visitées par les agents d’IA à partir des journaux du réseau CDN et de toutes les URL personnalisées spécifiées dans la configuration de votre site.
