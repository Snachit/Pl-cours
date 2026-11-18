---
tags: [exercices, deux-phases, examen]
---
# Ex 6 — Méthode des deux phases ⭐

⬅️ [[Ex 5 - Simplexe]] · [[Exercices]] · ➡️ [[Ex 7 - Dualité]] · 📖 [[06 - Méthode des deux phases]] · ⭐ [[10 - TP corrigé - Deux phases (modèle d'examen)]]

> [!formule] Rappel (convention du TP)
> Ligne **ZA** = somme des lignes contenant une artificielle (0 sous les $a_i$), b = somme des b.
> Phase I : entrante = plus grand **positif** de ZA ; fin quand plus de positif et $Z_A = 0$.
> Phase II : on supprime les $a_i$ et ZA ; **max** → plus grand positif de −Z ; **min** → plus négatif.

---

## Exercice 6.1 — Max avec deux contraintes ≥

> [!exercice] Énoncé
> $$\max Z = 3x_1 + 2x_2 \quad\text{s.c.}\quad x_1 + x_2 \le 6,\quad x_1 \ge 2,\quad x_2 \ge 1,\quad x_1,x_2 \ge 0$$

> [!solution]- ✅ Correction
> **Forme standard** : $x_1 + x_2 + e_1 = 6$ ; $x_1 - e_2 + a_2 = 2$ ; $x_2 - e_3 + a_3 = 1$.
> $Z_A = a_2 + a_3 = 3 - x_1 - x_2 + e_2 + e_3$ → ZA $= [1, 1, 0, -1, -1 \mid 3]$.
>
> **Phase I — tableau initial**
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | e3 | a2 | a3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | e1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 6 | 6 |
> | <span class="out">a2</span> | <span class="pv">1</span> | 0 | 0 | −1 | 0 | 1 | 0 | 2 | **2** ✅ |
> | a3 | 0 | 1 | 0 | 0 | −1 | 0 | 1 | 1 | ✗ |
> | −Z | 3 | 2 | 0 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | **1** | 1 | 0 | −1 | −1 | 0 | 0 | 3 | |
>
> Égalité (1 et 1) → on prend la première : $x_1$. Sortante $a_2$, pivot 1.
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | e3 | a2 | a3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | e1 | 0 | 1 | 1 | 1 | 0 | −1 | 0 | 4 | 4 |
> | x1 | 1 | 0 | 0 | −1 | 0 | 1 | 0 | 2 | ✗ |
> | <span class="out">a3</span> | 0 | <span class="pv">1</span> | 0 | 0 | −1 | 0 | 1 | 1 | **1** ✅ |
> | −Z | 0 | 2 | 0 | 3 | 0 | −3 | 0 | −6 | |
> | ZA | 0 | **1** | 0 | 0 | −1 | −1 | 0 | 1 | |
>
> $x_2$ entre, $a_3$ sort, pivot 1.
>
> | Base | x1 | x2 | e1 | e2 | e3 | a2 | a3 | b |
> |---|---|---|---|---|---|---|---|---|
> | e1 | 0 | 0 | 1 | 1 | 1 | −1 | −1 | 3 |
> | x1 | 1 | 0 | 0 | −1 | 0 | 1 | 0 | 2 |
> | x2 | 0 | 1 | 0 | 0 | −1 | 0 | 1 | 1 |
> | −Z | 0 | 0 | 0 | 3 | 2 | −3 | −2 | −8 |
> | ZA | 0 | 0 | 0 | 0 | 0 | −1 | −1 | **0** ✅ |
>
> **Phase II** (max)
>
> | Base | x1 | x2 | e1 | <span class="in">e2</span> | e3 | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | <span class="out">e1</span> | 0 | 0 | 1 | <span class="pv">1</span> | 1 | 3 | **3** ✅ |
> | x1 | 1 | 0 | 0 | −1 | 0 | 2 | ✗ |
> | x2 | 0 | 1 | 0 | 0 | −1 | 1 | ✗ |
> | −Z | 0 | 0 | 0 | **3** | 2 | −8 | |
>
> $e_2$ entre (3 = plus grand positif), $e_1$ sort, pivot 1 :
> - $x_1 = L + e_2 = [1, 0, 1, 0, 1 \mid 5]$ ; $-Z = L - 3e_2 = [0, 0, -3, 0, -1 \mid -17]$
>
> | Base | x1 | x2 | e1 | e2 | e3 | b |
> |---|---|---|---|---|---|---|
> | e2 | 0 | 0 | 1 | 1 | 1 | **3** |
> | x1 | 1 | 0 | 1 | 0 | 1 | **5** |
> | x2 | 0 | 1 | 0 | 0 | −1 | **1** |
> | −Z | 0 | 0 | −3 | 0 | −1 | **−17** |
>
> **Optimum : $x_1 = 5$, $x_2 = 1$, $Z_{\max} = 17$.** Vérif : $5 + 1 = 6$ ✓ ; $5 \ge 2$ ✓ (surplus 3) ; $1 \ge 1$ ✓ ; $Z = 15 + 2 = 17$ ✓

---

## Exercice 6.2 — Min à 3 variables (comme le TP)

> [!exercice] Énoncé
> $$\min Z = 10x_1 + 15x_2 + 12x_3 \quad\text{s.c.}\quad x_1 + 2x_2 + x_3 \ge 4,\quad 2x_1 + x_2 + 2x_3 \ge 5,\quad x_j \ge 0$$

> [!solution]- ✅ Correction
> **Forme standard** : $x_1 + 2x_2 + x_3 - e_1 + a_1 = 4$ ; $2x_1 + x_2 + 2x_3 - e_2 + a_2 = 5$.
> $Z_A = 9 - 3x_1 - 3x_2 - 3x_3 + e_1 + e_2$ → ZA $= [3, 3, 3, -1, -1 \mid 9]$.
>
> | Base | <span class="in">x1</span> | x2 | x3 | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | a1 | 1 | 2 | 1 | −1 | 0 | 1 | 0 | 4 | 4 |
> | <span class="out">a2</span> | <span class="pv">2</span> | 1 | 2 | 0 | −1 | 0 | 1 | 5 | **5/2** ✅ |
> | −Z | 10 | 15 | 12 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | **3** | 3 | 3 | −1 | −1 | 0 | 0 | 9 | |
>
> Triple égalité (3, 3, 3) → on prend $x_1$. Sortante $a_2$, pivot 2.
> - $x_1 = [1, \frac12, 1, 0, -\frac12, 0, \frac12 \mid \frac52]$
> - $a_1 = L - x_1 = [0, \frac32, 0, -1, \frac12, 1, -\frac12 \mid \frac32]$
> - $-Z = L - 10x_1 = [0, 10, 2, 0, 5, 0, -5 \mid -25]$
> - ZA $= L - 3x_1 = [0, \frac32, 0, -1, \frac12, 0, -\frac32 \mid \frac32]$
>
> | Base | x1 | <span class="in">x2</span> | x3 | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | <span class="out">a1</span> | 0 | <span class="pv">3/2</span> | 0 | −1 | 1/2 | 1 | −1/2 | 3/2 | **1** ✅ |
> | x1 | 1 | 1/2 | 1 | 0 | −1/2 | 0 | 1/2 | 5/2 | 5 |
> | −Z | 0 | 10 | 2 | 0 | 5 | 0 | −5 | −25 | |
> | ZA | 0 | **3/2** | 0 | −1 | 1/2 | 0 | −3/2 | 3/2 | |
>
> $x_2$ entre (3/2 > 1/2), $a_1$ sort, pivot 3/2.
> - $x_2 = L \times \frac23 = [0, 1, 0, -\frac23, \frac13, \frac23, -\frac13 \mid 1]$
> - $x_1 = L - \frac12 x_2 = [1, 0, 1, \frac13, -\frac23, -\frac13, \frac23 \mid 2]$
> - $-Z = L - 10x_2 = [0, 0, 2, \frac{20}{3}, \frac53, -\frac{20}{3}, -\frac53 \mid -35]$
> - ZA $= [0, 0, 0, 0, 0, -1, -1 \mid 0]$ ✅
>
> **Phase II** : ligne −Z $= [0, 0, 2, \frac{20}{3}, \frac53 \mid -35]$ → **aucun négatif** → déjà **optimal**.
>
> | Base | x1 | x2 | x3 | e1 | e2 | b |
> |---|---|---|---|---|---|---|
> | x2 | 0 | 1 | 0 | −2/3 | 1/3 | **1** |
> | x1 | 1 | 0 | 1 | 1/3 | −2/3 | **2** |
> | −Z | 0 | 0 | 2 | 20/3 | 5/3 | **−35** |
>
> **Optimum : $x_1 = 2$, $x_2 = 1$, $x_3 = 0$, $Z_{\min} = 20 + 15 = 35$.**
> Vérif : $2 + 2 = 4$ ✓ ; $4 + 1 = 5$ ✓ (les deux saturées).
> Bonus dual : sous $e_1, e_2$ → $y_1 = \frac{20}{3}$, $y_2 = \frac53$ ; $Z' = 4 \cdot \frac{20}{3} + 5 \cdot \frac53 = \frac{105}{3} = 35$ ✓

---

## Exercice 6.3 — Min avec =, ≥ et ≤

> [!exercice] Énoncé
> $$\min Z = 2x_1 + 3x_2 \quad\text{s.c.}\quad x_1 + x_2 = 5,\quad x_1 + 2x_2 \ge 6,\quad x_1 \le 4,\quad x_1,x_2 \ge 0$$

> [!solution]- ✅ Correction
> **Forme standard** : $x_1 + x_2 + a_1 = 5$ ; $x_1 + 2x_2 - e_2 + a_2 = 6$ ; $x_1 + e_3 = 4$. Base : $\{a_1, a_2, e_3\}$.
> ZA = ligne($a_1$) + ligne($a_2$) $= [2, 3, -1, 0 \mid 11]$ (colonnes $x_1, x_2, e_2, e_3$).
>
> | Base | x1 | <span class="in">x2</span> | e2 | e3 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | a1 | 1 | 1 | 0 | 0 | 1 | 0 | 5 | 5 |
> | <span class="out">a2</span> | 1 | <span class="pv">2</span> | −1 | 0 | 0 | 1 | 6 | **3** ✅ |
> | e3 | 1 | 0 | 0 | 1 | 0 | 0 | 4 | ✗ |
> | −Z | 2 | 3 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | 2 | **3** | −1 | 0 | 0 | 0 | 11 | |
>
> $x_2$ entre, $a_2$ sort, pivot 2.
>
> | Base | <span class="in">x1</span> | x2 | e2 | e3 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | <span class="out">a1</span> | <span class="pv">1/2</span> | 0 | 1/2 | 0 | 1 | −1/2 | 2 | **4** ✅ |
> | x2 | 1/2 | 1 | −1/2 | 0 | 0 | 1/2 | 3 | 6 |
> | e3 | 1 | 0 | 0 | 1 | 0 | 0 | 4 | 4 (égalité) |
> | −Z | 1/2 | 0 | 3/2 | 0 | 0 | −3/2 | −9 | |
> | ZA | **1/2** | 0 | 1/2 | 0 | 0 | −3/2 | 2 | |
>
> Égalité 1/2 ($x_1$ et $e_2$) → $x_1$. Rapports égaux (4 et 4) → on fait sortir l'**artificielle** $a_1$ (bon réflexe : on veut se débarrasser des artificielles). Pivot 1/2.
>
> | Base | x1 | x2 | e2 | e3 | a1 | a2 | b |
> |---|---|---|---|---|---|---|---|
> | x1 | 1 | 0 | 1 | 0 | 2 | −1 | 4 |
> | x2 | 0 | 1 | −1 | 0 | −1 | 1 | 1 |
> | e3 | 0 | 0 | −1 | 1 | −2 | 1 | 0 |
> | −Z | 0 | 0 | 1 | 0 | −1 | −1 | −11 |
> | ZA | 0 | 0 | 0 | 0 | −1 | −1 | **0** ✅ |
>
> **Phase II** : −Z $= [0, 0, 1, 0 \mid -11]$ → aucun négatif → **optimal**.
> **Solution : $x_1 = 4$, $x_2 = 1$, $Z_{\min} = 8 + 3 = 11$.**
> Vérif : $4 + 1 = 5$ ✓ ; $4 + 2 = 6 \ge 6$ ✓ ; $4 \le 4$ ✓ ($e_3 = 0$ en base : solution **dégénérée**, normal après une égalité de rapports).

➡️ [[Ex 7 - Dualité]]
