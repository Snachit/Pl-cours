---
tags: [revision, flashcards]
---
# 23 — Questions de cours (flashcards) 🧠

🏠 [[00 - Accueil]] · 📄 [[20 - Fiche résumé]]

> [!methode] Mode d'emploi
> Lis la question, réponds **à voix haute** ou par écrit, puis déplie la réponse (clique sur la question).

---

## 🔵 Introduction

> [!question]- Définir la Recherche Opérationnelle.
> Discipline scientifique qui utilise des méthodes mathématiques, des modèles et des algorithmes pour analyser des problèmes de décision et rechercher une solution optimale ou satisfaisante sous un ensemble de contraintes.

> [!question]- Où et quand est née la RO ?
> Pendant la Seconde Guerre mondiale, au Royaume-Uni, pour les opérations militaires (équipes pluridisciplinaires).

> [!question]- Citer les 5 étapes du processus d'optimisation.
> Analyse du problème → Modélisation → Résolution → Interprétation → Mise en œuvre (processus itératif).

> [!question]- Différence entre méthode exacte et métaheuristique ?
> Exacte : garantit la solution optimale (ex. simplexe). Métaheuristique (algorithmes génétiques, recuit simulé) : ne garantit pas l'optimalité mais trouve rapidement de très bonnes solutions pour les problèmes très complexes (NP-difficiles).

> [!question]- Quelle méthode pour un PL à variables entières ?
> Branch and Bound (PLNE).

## 🟢 Modélisation et graphique

> [!question]- Que signifie « linéaire » dans « programmation linéaire » ?
> La fonction objectif ET les contraintes sont linéaires (pas de produits de variables, pas de puissances).

> [!question]- Quels sont les éléments d'un PL ?
> Variables de décision, fonction objectif (économique), contraintes, contraintes de non-négativité.

> [!question]- Qu'est-ce que la région admissible ? Quelles formes peut-elle avoir ?
> L'intersection de tous les demi-plans des contraintes = ensemble des solutions réalisables. Elle peut être vide, bornée ou non bornée.

> [!question]- Énoncer le théorème fondamental de la résolution graphique.
> Si la région admissible est bornée et non vide, la solution optimale existe toujours et se trouve sur au moins un sommet de la région.

> [!question]- Quelles sont les deux méthodes pour trouver l'optimum graphiquement ?
> Méthode analytique (recensement des sommets, calcul de Z à chacun) et méthode géométrique (droites parallèles de niveau Z = p, déplacées loin de l'origine en max, vers l'origine en min).

## 🟠 Formes et simplexe

> [!question]- Forme canonique de type I et de type II ?
> Type I : max avec contraintes ≤. Type II : min avec contraintes ≥.

> [!question]- Caractéristiques de la forme standard ?
> Toutes les contraintes sont des égalités, toutes les variables sont positives, objectif max ou min.

> [!question]- Que représente une variable d'écart ?
> La quantité disponible non utilisée : l'écart entre la disponibilité et le besoin.

> [!question]- Variable de base / hors base ?
> De base : dans la colonne de gauche du tableau, valeur = b. Hors base : valent 0.

> [!question]- Comment choisit-on la variable entrante (max) ? la sortante ?
> Entrante : plus fort coefficient strictement positif de la ligne objectif. Sortante : plus petit rapport b / coefficient de la colonne entrante (coefficients > 0).

> [!question]- Quel est le critère d'optimalité (max ; min) ?
> Max : tous les coefficients de la ligne objectif ≤ 0. Min : tous ≥ 0.

> [!question]- Contrainte saturée / marginale ?
> Saturée : écart nul. Marginale : écart non nul. (Pour ≥ on parle de surplus.)

## 🔴 Deux phases

> [!question]- Pourquoi la méthode des deux phases ?
> Quand il y a des contraintes ≥ ou =, il n'y a pas de solution de base réalisable évidente (l'excédent serait négatif). On ajoute des variables artificielles pour forcer une base de départ.

> [!question]- Quel est l'objectif de la phase I ?
> Minimiser la somme des variables artificielles Z_A = Σaᵢ pour s'en débarrasser et obtenir une solution de base réalisable du problème initial.

> [!question]- Que conclure si Z_A ≠ 0 à la fin de la phase I ? Et si Z_A = 0 ?
> Z_A ≠ 0 : aucune solution réalisable (problème impossible). Z_A = 0 : on a une solution réalisable, on supprime les colonnes des artificielles et la ligne Z_A, et on passe à la phase II avec l'objectif initial.

> [!question]- Une variable artificielle a-t-elle un sens réel ?
> Non : c'est un artifice mathématique temporaire, elle n'appartient pas au problème réel.

## 🟤 Dualité

> [!question]- Comment construit-on le dual de max CᵗX, AX ≤ B, X ≥ 0 ?
> min BᵗY, AᵗY ≥ C, Y ≥ 0 : seconds membres ↔ coefficients de l'objectif, max ↔ min, ≤ ↔ ≥, A transposée.

> [!question]- Contrainte = dans le primal (max) → ? ; variable libre → ?
> Contrainte = → variable duale quelconque (libre). Variable libre → contrainte duale =.

> [!question]- Énoncer le théorème de dualité forte.
> Si le primal et le dual ont des solutions optimales, alors Z* = Z'*.

> [!question]- Énoncer les conditions de complémentarité.
> Si xⱼ* > 0, la j-ième contrainte duale est saturée ; si la j-ième contrainte duale n'est pas saturée, xⱼ* = 0. Si yᵢ* > 0, la i-ième contrainte primale est saturée ; si elle n'est pas saturée, yᵢ* = 0.

> [!question]- Comment lire la solution du primal dans le tableau optimal du dual ?
> Ce sont les coefficients (en valeur absolue) de la ligne objectif sous les colonnes des variables d'écart du dual (excédent pour ≥, artificielle pour =).

> [!question]- Pourquoi résoudre le dual plutôt que le primal ?
> Quand le primal a beaucoup de variables, ou est un min avec des ≥ (deux phases), le dual peut être plus simple (max avec ≤, voire 2 variables → graphique).

## ⚫ Cas particuliers

> [!question]- Comment détecter un problème non borné au simplexe ?
> La colonne de la variable entrante n'a aucun coefficient strictement positif : pas de rapport possible.

> [!question]- Comment détecter des solutions optimales multiples ?
> À l'optimum, une variable hors base (non artificielle) a un coût marginal nul dans la ligne objectif, avec un ratio > 0.

> [!question]- Condition d'unicité de la solution optimale ?
> Les coûts marginaux de toutes les variables hors base sont strictement différents de 0.

> [!question]- « Non borné » signifie-t-il « pas de solution » ?
> Non : il y a une infinité de solutions réalisables, c'est l'optimum qui est infini. Souvent dû à l'oubli d'une contrainte.
