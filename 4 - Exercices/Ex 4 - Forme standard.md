---
tags: [exercices, forme-standard]
---
# Ex 4 — Formes canonique, mixte et standard

⬅️ [[Ex 3 - Résolution graphique]] · [[Exercices]] · ➡️ [[Ex 5 - Simplexe]] · 📖 [[04 - Formes canonique et standard]]

> [!formule] Rappel
> | Contrainte | Ajout | Base de départ |
> |---|---|---|
> | ≤ | $+e_i$ | $e_i$ |
> | ≥ | $-e_i + a_i$ | $a_i$ |
> | = | $+a_i$ | $a_i$ |
>
> Second membre négatif → **multiplier par −1 et inverser** le sens d'abord.

---

## Exercice 4.1 — Type I : forme standard et tableau initial

> [!exercice] Énoncé
> $$\max Z = 4x_1 + 3x_2 + 6x_3 \quad\text{s.c.}\quad 3x_1 + x_2 + 3x_3 \le 30,\quad 2x_1 + 2x_2 + 3x_3 \le 40,\quad x_1 + x_2 + x_3 \le 15,\quad x_j \ge 0$$
> 1. Quelle est la forme de ce PL ?
> 2. Écrire la forme standard.
> 3. Construire le tableau initial du simplexe et donner la solution de base associée. Quelle variable entre en premier ?

> [!solution]- ✅ Correction
> **1.** max + toutes les contraintes ≤ → **forme canonique de type I**.
>
> **2.**
> $$
> \begin{cases}
> \max Z = 4x_1 + 3x_2 + 6x_3\\
> 3x_1 + x_2 + 3x_3 + e_1 = 30\\
> 2x_1 + 2x_2 + 3x_3 + e_2 = 40\\
> x_1 + x_2 + x_3 + e_3 = 15\\
> x_1, x_2, x_3, e_1, e_2, e_3 \ge 0
> \end{cases}
> $$
> **3.**
>
> | Base | x1 | x2 | <span class="in">x3</span> | e1 | e2 | e3 | b |
> |---|---|---|---|---|---|---|---|
> | e1 | 3 | 1 | 3 | 1 | 0 | 0 | 30 |
> | e2 | 2 | 2 | 3 | 0 | 1 | 0 | 40 |
> | e3 | 1 | 1 | 1 | 0 | 0 | 1 | 15 |
> | −Z | 4 | 3 | **6** | 0 | 0 | 0 | 0 |
>
> Solution de base : hors base $x_1 = x_2 = x_3 = 0$ ; base $e_1 = 30$, $e_2 = 40$, $e_3 = 15$ ; $Z = 0$ (= le sommet O).
> Variable entrante : plus grand coefficient positif = **6** → $x_3$. Rapports : $30/3 = 10$, $40/3 \approx 13{,}3$, $15/1 = 15$ → $e_1$ sortirait (pivot 3).

---

## Exercice 4.2 — Forme mixte avec second membre négatif ⭐

> [!exercice] Énoncé
> $$\min Z = 2x_1 - x_2 + 4x_3 \quad\text{s.c.}\quad \begin{cases} x_1 + x_2 - x_3 \ge -3\\ 2x_1 + x_3 = 5\\ x_1 + 3x_2 \ge 2 \end{cases}\quad x_1,x_2,x_3 \ge 0$$
> 1. Rendre tous les seconds membres positifs.
> 2. Écrire la forme standard (préciser le rôle de chaque variable ajoutée).
> 3. Donner la base de départ, la fonction $Z_A$ et le tableau initial de la phase I (convention du TP).

> [!solution]- ✅ Correction
> **1.** La 1ʳᵉ contrainte a un second membre −3 : on multiplie par −1 **et on inverse** :
> $$-x_1 - x_2 + x_3 \le 3$$
> **2.**
> $$
> \begin{cases}
> -x_1 - x_2 + x_3 + e_1 = 3 & e_1 : \text{écart (≤)}\\
> 2x_1 + x_3 + a_2 = 5 & a_2 : \text{artificielle (=)}\\
> x_1 + 3x_2 - e_3 + a_3 = 2 & e_3 : \text{excédent},\ a_3 : \text{artificielle (≥)}
> \end{cases}
> $$
> **3.** Base de départ : $\{e_1, a_2, a_3\}$ avec $e_1 = 3$, $a_2 = 5$, $a_3 = 2$.
> $$Z_A = a_2 + a_3 = (5 - 2x_1 - x_3) + (2 - x_1 - 3x_2 + e_3) = 7 - 3x_1 - 3x_2 - x_3 + e_3$$
>
> | Base | x1 | x2 | x3 | e1 | e3 | a2 | a3 | b |
> |---|---|---|---|---|---|---|---|---|
> | e1 | −1 | −1 | 1 | 1 | 0 | 0 | 0 | 3 |
> | a2 | 2 | 0 | 1 | 0 | 0 | 1 | 0 | 5 |
> | a3 | 1 | 3 | 0 | 0 | −1 | 0 | 1 | 2 |
> | −Z | 2 | −1 | 4 | 0 | 0 | 0 | 0 | 0 |
> | ZA | 3 | 3 | 1 | 0 | −1 | 0 | 0 | 7 |
>
> ZA = ligne($a_2$) + ligne($a_3$) ; la ligne de $e_1$ **n'entre pas** dans la somme (pas d'artificielle).

---

## Exercice 4.3 — Classer et choisir la méthode

> [!exercice] Énoncé
> Pour chaque PL : forme (type I, type II, mixte, standard) ? nombre de variables de base ? méthode de résolution ?
> - (a) $\max 2x_1 + x_2$ ; $x_1 + x_2 \le 5$ ; $3x_1 - x_2 \le 4$ ; $x \ge 0$
> - (b) $\min x_1 + 4x_2$ ; $x_1 + 2x_2 \ge 3$ ; $4x_1 + x_2 \ge 2$ ; $x \ge 0$
> - (c) $\max x_1 + x_2$ ; $x_1 - x_2 \ge 1$ ; $x_1 + x_2 \le 6$ ; $x \ge 0$
> - (d) $\min 3x_1 + x_2 + x_3$ ; $x_1 + x_2 + x_3 = 10$ ; $x_1 - x_2 + 2x_3 = 4$ ; $x \ge 0$

> [!solution]- ✅ Correction
>
> | PL | Forme | Nb variables de base | Méthode |
> |---|---|---|---|
> | (a) | **canonique type I** (max, ≤) | 2 ($e_1, e_2$) | simplexe simple (ou graphique, 2 variables) |
> | (b) | **canonique type II** (min, ≥) | 2 ($a_1, a_2$) | deux phases — ou **dual** (max avec ≤) — ou graphique |
> | (c) | **mixte** (max avec un ≥) | 2 ($a_1, e_2$) | deux phases (ou graphique) |
> | (d) | déjà **standard** (que des =) | 2 ($a_1, a_2$) | deux phases (aucune base évidente → une artificielle par égalité) |
>
> Rappel : il y a toujours **autant de variables de base que de contraintes**.

➡️ [[Ex 5 - Simplexe]]
