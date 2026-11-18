---
tags: [exercices, introduction]
---
# Ex 1 — Introduction à la RO

⬅️ [[Exercices]] · 📖 Cours : [[01 - Introduction à la RO]]

---

## Exercice 1.1 — Reconnaître le problème

> [!exercice] Énoncé
> Pour chaque situation, donner : **(a)** le nom du problème classique (cours), **(b)** l'objectif (max ou min de quoi ?), **(c)** les contraintes principales, **(d)** une méthode de résolution adaptée.
> 1. Un livreur part de l'entrepôt, doit passer **une seule fois** chez 15 clients et revenir à l'entrepôt.
> 2. Un étudiant part en voyage avec une valise de 23 kg et choisit des objets ayant chacun un poids et une utilité.
> 3. Trois usines approvisionnent cinq magasins ; chaque usine a une capacité, chaque magasin une demande.
> 4. Un paquet de données doit aller du serveur A au serveur B via un réseau de routeurs.
> 5. Un processeur doit exécuter 10 tâches, certaines devant être finies avant d'autres.

> [!solution]- ✅ Correction
>
> | # | (a) Problème | (b) Objectif | (c) Contraintes | (d) Méthode |
> |---|---|---|---|---|
> | 1 | **Voyageur de commerce** | **min** distance / temps total | chaque client visité exactement une fois, cycle unique | métaheuristiques (NP-difficile) |
> | 2 | **Sac-à-dos** (knapsack) | **max** utilité totale | poids total ≤ 23 kg, objets pris ou non (0/1) | programmation dynamique / Branch and Bound (variables **entières**) |
> | 3 | **Transport** | **min** coût total de transport | quantités envoyées ≤ capacités, demandes satisfaites | **programmation linéaire** (simplexe) |
> | 4 | **Routage / plus court chemin** | **min** coût, distance ou latence | capacités des liaisons, routeurs disponibles | théorie des graphes (**Dijkstra**) |
> | 5 | **Ordonnancement** | **min** temps total d'exécution | précédences, ressources de calcul limitées | graphes (PERT), PL |

---

## Exercice 1.2 — Le processus d'optimisation

> [!exercice] Énoncé
> 1. Remettre dans l'ordre : *Interprétation · Mise en œuvre · Analyse du problème · Résolution · Modélisation*.
> 2. À quelle étape appartient chaque action ?
>    a. Choisir le solveur GLPK. b. Former les équipes au nouvel outil. c. Définir les variables de décision. d. Étudier comment la solution change si le prix d'une matière augmente. e. Identifier les ressources disponibles.
> 3. Pourquoi dit-on que l'optimisation est un processus **itératif** ?

> [!solution]- ✅ Correction
> 1. **Analyse du problème → Modélisation → Résolution → Interprétation → Mise en œuvre.**
> 2. a. **Résolution** (solveurs CPLEX, Gurobi, GLPK) · b. **Mise en œuvre** · c. **Modélisation** · d. **Interprétation** (analyse de sensibilité) · e. **Analyse du problème**.
> 3. Si la solution finale ne convient pas (incohérente avec le terrain, refusée par les décideurs), il faut **revenir à la modélisation** et recommencer.

---

## Exercice 1.3 — Vrai ou faux ? (justifier)

> [!exercice] Énoncé
> 1. La RO est née aux États-Unis dans les années 1970.
> 2. Une métaheuristique garantit toujours la solution optimale.
> 3. Le simplexe s'applique aux PL à variables continues.
> 4. $Z = 3x_1 + 2x_1x_2$ est une fonction linéaire.
> 5. Pour un PL à variables entières, on utilise Branch and Bound.
> 6. La programmation dynamique repose sur le principe d'optimalité de Bellman.
> 7. La simulation est utilisée quand aucun modèle mathématique exact n'est résoluble.
> 8. Un modèle mathématique est une représentation exacte de la réalité.

> [!solution]- ✅ Correction
> 1. **Faux** : Seconde Guerre mondiale, **Royaume-Uni**, opérations militaires.
> 2. **Faux** : elle ne garantit **pas** l'optimalité, mais trouve rapidement de très bonnes solutions.
> 3. **Vrai**.
> 4. **Faux** : le produit $x_1x_2$ n'est pas linéaire.
> 5. **Vrai** (PLNE).
> 6. **Vrai** (décomposition en sous-problèmes, efficace pour le sac-à-dos).
> 7. **Vrai** (ou quand l'expérimentation réelle est impossible).
> 8. **Faux** : tout modèle est une **simplification** de la réalité.

➡️ [[Ex 2 - Modélisation]]
