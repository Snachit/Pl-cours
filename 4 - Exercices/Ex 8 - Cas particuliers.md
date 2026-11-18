---
tags: [exercices, cas-particuliers]
---
# Ex 8 — Cas particuliers

⬅️ [[Ex 7 - Dualité]] · [[Exercices]] · ➡️ [[Ex 9 - Examen blanc]] · 📖 [[08 - Cas particuliers]]

> [!formule] Rappel
> | Cas | Signal |
> |---|---|
> | Non borné | colonne entrante : tous les coefficients **≤ 0** |
> | Impossible | fin de phase I avec $Z_A > 0$ |
> | Solutions multiples | coef **0** sous une variable **hors base** à l'optimum (ratio > 0) |

---

## Exercice 8.1 — Non borné

> [!exercice] Énoncé
> $$\max Z = 2x_1 + x_2 \quad\text{s.c.}\quad x_1 - x_2 \le 2,\quad -2x_1 + x_2 \le 2,\quad x_1,x_2 \ge 0$$
> Appliquer le simplexe et conclure.

> [!solution]- ✅ Correction
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|
> | <span class="out">e1</span> | <span class="pv">1</span> | −1 | 1 | 0 | 2 | **2** ✅ |
> | e2 | −2 | 1 | 0 | 1 | 2 | ✗ (−2) |
> | −Z | **2** | 1 | 0 | 0 | 0 | |
>
> $x_1$ entre, $e_1$ sort, pivot 1 : $x_1 = [1, -1, 1, 0 \mid 2]$ ; $e_2 = L + 2x_1 = [0, -1, 2, 1 \mid 6]$ ; $-Z = L - 2x_1 = [0, 3, -2, 0 \mid -4]$
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|
> | x1 | 1 | **−1** | 1 | 0 | 2 | ✗ |
> | e2 | 0 | **−1** | 2 | 1 | 6 | ✗ |
> | −Z | 0 | **3** | −2 | 0 | −4 | |
>
> $x_2$ doit entrer (3 > 0) mais **tous les coefficients de sa colonne sont ≤ 0** → aucun rapport → **problème non borné** : $Z \to +\infty$.
> Interprétation : on peut augmenter $x_2$ (et $x_1 = 2 + x_2$) indéfiniment sans violer les contraintes. Il manque probablement une contrainte de capacité.

---

## Exercice 8.2 — Impossible

> [!exercice] Énoncé
> $$\min Z = 3x_1 + 2x_2 \quad\text{s.c.}\quad x_1 + x_2 \le 3,\quad 2x_1 + x_2 \ge 8,\quad x_1,x_2 \ge 0$$
> Appliquer la phase I et conclure. Justifier aussi « à la main ».

> [!solution]- ✅ Correction
> Forme standard : $x_1 + x_2 + e_1 = 3$ ; $2x_1 + x_2 - e_2 + a_2 = 8$. ZA $= [2, 1, 0, -1 \mid 8]$.
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | <span class="out">e1</span> | <span class="pv">1</span> | 1 | 1 | 0 | 0 | 3 | **3** ✅ |
> | a2 | 2 | 1 | 0 | −1 | 1 | 8 | 4 |
> | −Z | 3 | 2 | 0 | 0 | 0 | 0 | |
> | ZA | **2** | 1 | 0 | −1 | 0 | 8 | |
>
> $x_1$ entre, $e_1$ sort, pivot 1 :
>
> | Base | x1 | x2 | e1 | e2 | a2 | b |
> |---|---|---|---|---|---|---|
> | x1 | 1 | 1 | 1 | 0 | 0 | 3 |
> | a2 | 0 | −1 | −2 | −1 | 1 | **2** |
> | −Z | 0 | −1 | −3 | 0 | 0 | −9 |
> | ZA | 0 | −1 | −2 | −1 | 0 | **2** |
>
> Plus aucun positif dans ZA, mais **$Z_A = 2 \ne 0$** ($a_2 = 2$ reste en base) ⇒ **aucune solution réalisable**.
> À la main : $2x_1 + x_2 \le 2(x_1 + x_2) \le 2 \times 3 = 6 < 8$ → la 2ᵉ contrainte ne peut jamais être satisfaite.

---

## Exercice 8.3 — Solutions multiples

> [!exercice] Énoncé
> $$\max Z = 2x_1 + 4x_2 \quad\text{s.c.}\quad x_1 + 2x_2 \le 8,\quad x_1 \le 6,\quad x_2 \le 3,\quad x_1,x_2 \ge 0$$
> 1. Résoudre par le simplexe. 2. Montrer que la solution n'est pas unique et trouver un 2ᵉ sommet optimal. 3. Interpréter graphiquement.

> [!solution]- ✅ Correction
> **1.**
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | e3 | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | e1 | 1 | 2 | 1 | 0 | 0 | 8 | 4 |
> | e2 | 1 | 0 | 0 | 1 | 0 | 6 | ✗ |
> | <span class="out">e3</span> | 0 | <span class="pv">1</span> | 0 | 0 | 1 | 3 | **3** ✅ |
> | −Z | 2 | **4** | 0 | 0 | 0 | 0 | |
>
> $x_2$ entre, $e_3$ sort : $e_1 = [1, 0, 1, 0, -2 \mid 2]$ ; $-Z = [2, 0, 0, 0, -4 \mid -12]$.
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | e3 | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | <span class="out">e1</span> | <span class="pv">1</span> | 0 | 1 | 0 | −2 | 2 | **2** ✅ |
> | e2 | 1 | 0 | 0 | 1 | 0 | 6 | 6 |
> | x2 | 0 | 1 | 0 | 0 | 1 | 3 | ✗ |
> | −Z | **2** | 0 | 0 | 0 | −4 | −12 | |
>
> $x_1$ entre, $e_1$ sort : $e_2 = L - x_1 = [0, 0, -1, 1, 2 \mid 4]$ ; $-Z = L - 2x_1 = [0, 0, -2, 0, 0 \mid -16]$.
>
> | Base | x1 | x2 | e1 | e2 | <span class="in">e3</span> | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | x1 | 1 | 0 | 1 | 0 | −2 | 2 | ✗ |
> | <span class="out">e2</span> | 0 | 0 | −1 | 1 | <span class="pv">2</span> | 4 | **2** ✅ |
> | x2 | 0 | 1 | 0 | 0 | 1 | 3 | 3 |
> | −Z | 0 | 0 | −2 | 0 | <span class="ok">0</span> | −16 | |
>
> Tout ≤ 0 → optimum : $(x_1, x_2) = (2, 3)$, $Z = 16$.
>
> **2.** $e_3$ est **hors base** avec un coefficient **0** dans −Z, et son ratio vaut 2 > 0 ⇒ **infinité de solutions**. Pivot supplémentaire ($e_3$ entre, $e_2$ sort, pivot 2) :
> - $e_3 = [0, 0, -\frac12, \frac12, 1 \mid 2]$ ; $x_1 = L + 2e_3 = [1, 0, 0, 1, 0 \mid 6]$ ; $x_2 = L - e_3 = [0, 1, \frac12, -\frac12, 0 \mid 1]$ ; −Z inchangée ($-16$)
>
> 2ᵉ sommet optimal : **(6 ; 1)**, $Z = 12 + 4 = 16$ ✓.
>
> **3.** $Z = 2x_1 + 4x_2 = 2(x_1 + 2x_2)$ : la droite de Z est **parallèle** à la contrainte $x_1 + 2x_2 \le 8$. Tout le **segment [(2 ; 3) ; (6 ; 1)]** est optimal, $Z^* = 16$.
>
> ![[ex-C3.svg]]

➡️ [[Ex 9 - Examen blanc]]
