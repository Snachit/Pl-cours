---
tags: [exercices, dualite]
---
# Ex 7 — Dualité

⬅️ [[Ex 6 - Deux phases]] · [[Exercices]] · ➡️ [[Ex 8 - Cas particuliers]] · 📖 [[07 - Dualité]]

> [!formule] Rappel
> max ↔ min · $B \leftrightarrow C$ · $A \to A^t$ · 1 contrainte ↔ 1 variable.
> (côté max) ≤ ↔ $y \ge 0$ · ≥ ↔ $y \le 0$ · = ↔ $y$ libre · variable ≥ 0 ↔ contrainte « normale » · variable libre ↔ =.
> **Complémentarité** : variable > 0 ⇒ contrainte associée saturée ; contrainte non saturée ⇒ variable associée = 0.

---

## Exercice 7.1 — Écrire le dual (3 cas)

> [!exercice] Énoncé
> Écrire le dual de :
> - (a) $\max Z = 4x_1 + 3x_2 + x_3$ ; $x_1 + x_2 + x_3 \le 10$ ; $2x_1 + x_2 \le 12$ ; $x_1 + 3x_3 \le 9$ ; $x_j \ge 0$
> - (b) $\min Z = 5x_1 + 2x_2$ ; $x_1 + x_2 \ge 3$ ; $2x_1 - x_2 \ge 1$ ; $x_1 + 4x_2 \ge 4$ ; $x_1, x_2 \ge 0$
> - (c) $\min Z = 3x_1 + x_2 + 2x_3$ ; $x_1 + x_2 \ge 2$ ; $x_1 + 2x_3 \le 5$ ; $x_2 + x_3 = 4$ ; $x_1 \ge 0$, $x_2 \ge 0$, $x_3 \in \mathbb{R}$

> [!solution]- ✅ Correction
> **(a)** Forme canonique max/≤ → dual min/≥, 3 contraintes → 3 variables.
> $A = \begin{pmatrix}1&1&1\\2&1&0\\1&0&3\end{pmatrix}$ → $A^t = \begin{pmatrix}1&2&1\\1&1&0\\1&0&3\end{pmatrix}$
> $$\min Z' = 10y_1 + 12y_2 + 9y_3 \ ;\ y_1 + 2y_2 + y_3 \ge 4 \ ;\ y_1 + y_2 \ge 3 \ ;\ y_1 + 3y_3 \ge 1 \ ;\ y_1,y_2,y_3 \ge 0$$
>
> **(b)** Forme canonique min/≥ → dual max/≤, 3 contraintes → 3 variables, 2 variables → 2 contraintes.
> $$\max Z' = 3y_1 + y_2 + 4y_3 \ ;\ y_1 + 2y_2 + y_3 \le 5 \ ;\ y_1 - y_2 + 4y_3 \le 2 \ ;\ y_1,y_2,y_3 \ge 0$$
>
> **(c)** Primal **min** (contraintes « normales » = ≥) :
> - $x_1 + x_2 \ge 2$ (normale) → $y_1 \ge 0$
> - $x_1 + 2x_3 \le 5$ (inversée pour un min) → $y_2 \le 0$
> - $x_2 + x_3 = 4$ → $y_3 \in \mathbb{R}$
> - $x_1 \ge 0$, $x_2 \ge 0$ → contraintes duales **≤** ; $x_3$ libre → contrainte duale **=**
>
> Colonnes : $x_1 : (1, 1, 0)$ ; $x_2 : (1, 0, 1)$ ; $x_3 : (0, 2, 1)$.
> $$
> \begin{cases}
> \max Z' = 2y_1 + 5y_2 + 4y_3\\
> y_1 + y_2 \le 3\\
> y_1 + y_3 \le 1\\
> 2y_2 + y_3 = 2\\
> y_1 \ge 0,\ y_2 \le 0,\ y_3 \in \mathbb{R}
> \end{cases}
> $$

---

## Exercice 7.2 — Résoudre un min par la dualité (méthode du cours) ⭐

> [!exercice] Énoncé
> $$(P)\quad \min Z = 4x_1 + 6x_2 + 3x_3 \quad\text{s.c.}\quad x_1 + 2x_2 + x_3 \ge 6,\quad 2x_1 + x_2 + x_3 \ge 8,\quad x_j \ge 0$$
> 1. Écrire le dual (D).
> 2. Résoudre (D) graphiquement.
> 3. En déduire la solution de (P) avec les théorèmes de dualité.

> [!solution]- ✅ Correction
> **1.** $A = \begin{pmatrix}1&2&1\\2&1&1\end{pmatrix}$, $A^t = \begin{pmatrix}1&2\\2&1\\1&1\end{pmatrix}$ :
> $$(D)\quad \max Z' = 6y_1 + 8y_2 \quad\text{s.c.}\quad y_1 + 2y_2 \le 4\ (d_1),\quad 2y_1 + y_2 \le 6\ (d_2),\quad y_1 + y_2 \le 3\ (d_3),\quad y_1,y_2 \ge 0$$
>
> **2.** ![[ex-Du2.svg]]
>
> | Sommet | Obtenu par | $Z' = 6y_1 + 8y_2$ |
> |---|---|---|
> | O(0 ; 0) | | 0 |
> | (3 ; 0) | $d_2$ et $d_3$ coupent l'axe en 3 | 18 |
> | **(2 ; 1)** | $d_1 \cap d_3$ : $y_1 + 2y_2 = 4$, $y_1 + y_2 = 3$ ⇒ $y_2 = 1$ | **20** ✅ |
> | (0 ; 2) | $d_1$ ∩ axe | 16 |
>
> Vérif de (2 ; 1) dans $d_2$ : $4 + 1 = 5 \le 6$ ✓. **$y^* = (2, 1)$, $Z'^* = 20$.**
>
> **3.**
> - **Th. 1** : (D) a un optimum ⇒ (P) aussi. **Th. 2** : $Z^* = Z'^* = 20$.
> - **Th. 3** : $d_2$ : $2(2) + 1 = 5 < 6$ → **non saturée** ⇒ $x_2 = 0$.
> - $y_1 = 2 > 0$ et $y_2 = 1 > 0$ ⇒ les 2 contraintes de (P) sont **saturées** :
> $$\begin{cases}x_1 + x_3 = 6\\ 2x_1 + x_3 = 8\end{cases} \Rightarrow x_1 = 2,\ x_3 = 4$$
>
> **Solution de (P) : $x^* = (2, 0, 4)$, $Z = 8 + 0 + 12 = 20 = Z'^*$ ✓**

---

## Exercice 7.3 — Lire le dual dans un tableau final

> [!exercice] Énoncé
> Le tableau final de l'[[Ex 5 - Simplexe#Exercice 5.2 — Trois variables|exercice 5.2]] ($\max 5x_1 + 4x_2 + 3x_3$, trois contraintes ≤ de seconds membres 5, 11, 8) est :
>
> | Base | x1 | x2 | x3 | e1 | e2 | e3 | b |
> |---|---|---|---|---|---|---|---|
> | x1 | 1 | 2 | 0 | 2 | 0 | −1 | 2 |
> | e2 | 0 | −5 | 0 | −2 | 1 | 0 | 1 |
> | x3 | 0 | −1 | 1 | −3 | 0 | 2 | 1 |
> | −Z | 0 | −3 | 0 | −1 | 0 | −1 | −13 |
>
> 1. Écrire le dual. 2. Lire sa solution dans le tableau. 3. Vérifier la dualité forte et la complémentarité.

> [!solution]- ✅ Correction
> **1.**
> $$\min Z' = 5y_1 + 11y_2 + 8y_3 \ ;\ 2y_1 + 4y_2 + 3y_3 \ge 5 \ ;\ 3y_1 + y_2 + 4y_3 \ge 4 \ ;\ y_1 + 2y_2 + 2y_3 \ge 3 \ ;\ y \ge 0$$
> **2.** Valeurs absolues sous les **écarts** $e_1, e_2, e_3$ dans −Z : **$y_1 = 1$, $y_2 = 0$, $y_3 = 1$**.
> **3.**
> - $Z' = 5(1) + 11(0) + 8(1) = 13 = Z^*$ ✓ (dualité forte)
> - $y_2 = 0$ ↔ la 2ᵉ contrainte primale n'est pas saturée ($e_2 = 1 > 0$) ✓
> - Contraintes duales : $2 + 3 = 5$ (saturée, $x_1 > 0$ ✓) ; $3 + 4 = 7 > 4$ (non saturée ⇒ $x_2 = 0$ ✓) ; $1 + 2 = 3$ (saturée, $x_3 > 0$ ✓)
> - Bonus : sous $x_2$ dans −Z on lit −3 → $|−3| = 7 - 4$ = surplus de la 2ᵉ contrainte duale ✓

➡️ [[Ex 8 - Cas particuliers]]
