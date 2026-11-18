---
tags: [exercices, simplexe]
---
# Ex 5 — Méthode du Simplexe

⬅️ [[Ex 4 - Forme standard]] · [[Exercices]] · ➡️ [[Ex 6 - Deux phases]] · 📖 [[05 - Méthode du Simplexe]]

> [!formule] Rappel (max)
> Entrante = plus grand coefficient **> 0** de −Z · Sortante = plus petit $b_i / a_{ik}$ avec $a_{ik} > 0$ · Ligne pivot ÷ pivot · $L' = L - A \times L_{\text{pivot}}'$ · Stop quand tout **≤ 0** · $Z = -(\text{case b de }-Z)$.

---

## Exercice 5.1 — Simplexe vs graphique

> [!exercice] Énoncé
> $$\max Z = 3x_1 + 5x_2 \quad\text{s.c.}\quad x_1 \le 4,\quad 2x_2 \le 12,\quad 3x_1 + 2x_2 \le 18,\quad x_1,x_2 \ge 0$$
> 1. Résoudre par le simplexe.
> 2. À quel sommet du graphique correspond chaque tableau ? (graphe dans [[03 - Résolution graphique#2. Exemple complet du cours]])

> [!solution]- ✅ Correction
> **Tableau initial**
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | e3 | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | e1 | 1 | 0 | 1 | 0 | 0 | 4 | ✗ (coef 0) |
> | <span class="out">e2</span> | 0 | <span class="pv">2</span> | 0 | 1 | 0 | 12 | **6** ✅ |
> | e3 | 3 | 2 | 0 | 0 | 1 | 18 | 9 |
> | −Z | 3 | **5** | 0 | 0 | 0 | 0 | |
>
> **It. 1** : $x_2$ entre, $e_2$ sort, pivot 2.
> - $x_2 = [0, 1, 0, \frac12, 0 \mid 6]$ ; $e_1$ inchangée ; $e_3 = L - 2x_2 = [3, 0, 0, -1, 1 \mid 6]$ ; $-Z = L - 5x_2 = [3, 0, 0, -\frac52, 0 \mid -30]$
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | e3 | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | e1 | 1 | 0 | 1 | 0 | 0 | 4 | 4 |
> | x2 | 0 | 1 | 0 | 1/2 | 0 | 6 | ✗ |
> | <span class="out">e3</span> | <span class="pv">3</span> | 0 | 0 | −1 | 1 | 6 | **2** ✅ |
> | −Z | **3** | 0 | 0 | −5/2 | 0 | −30 | |
>
> **It. 2** : $x_1$ entre, $e_3$ sort, pivot 3.
> - $x_1 = [1, 0, 0, -\frac13, \frac13 \mid 2]$ ; $e_1 = L - x_1 = [0, 0, 1, \frac13, -\frac13 \mid 2]$ ; $x_2$ inchangée ; $-Z = L - 3x_1 = [0, 0, 0, -\frac32, -1 \mid -36]$
>
> | Base | x1 | x2 | e1 | e2 | e3 | b |
> |---|---|---|---|---|---|---|
> | e1 | 0 | 0 | 1 | 1/3 | −1/3 | 2 |
> | x2 | 0 | 1 | 0 | 1/2 | 0 | 6 |
> | x1 | 1 | 0 | 0 | −1/3 | 1/3 | 2 |
> | −Z | 0 | 0 | 0 | −3/2 | −1 | −36 |
>
> Tout ≤ 0 → **optimum : $x_1 = 2$, $x_2 = 6$, $Z = 36$** ; $e_1 = 2$ (contrainte $x_1 \le 4$ non saturée).
>
> **2.** Tableau initial = **O(0 ; 0)** (Z = 0) → it. 1 = **A(0 ; 6)** (Z = 30) → it. 2 = **B(2 ; 6)** (Z = 36). Le simplexe se déplace de sommet voisin en sommet voisin !

---

## Exercice 5.2 — Trois variables

> [!exercice] Énoncé
> $$\max Z = 5x_1 + 4x_2 + 3x_3 \quad\text{s.c.}\quad 2x_1 + 3x_2 + x_3 \le 5,\quad 4x_1 + x_2 + 2x_3 \le 11,\quad 3x_1 + 4x_2 + 2x_3 \le 8,\quad x_j \ge 0$$

> [!solution]- ✅ Correction
> **Tableau initial**
>
> | Base | <span class="in">x1</span> | x2 | x3 | e1 | e2 | e3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | <span class="out">e1</span> | <span class="pv">2</span> | 3 | 1 | 1 | 0 | 0 | 5 | **5/2 = 2,5** ✅ |
> | e2 | 4 | 1 | 2 | 0 | 1 | 0 | 11 | 11/4 = 2,75 |
> | e3 | 3 | 4 | 2 | 0 | 0 | 1 | 8 | 8/3 ≈ 2,67 |
> | −Z | **5** | 4 | 3 | 0 | 0 | 0 | 0 | |
>
> **It. 1** : $x_1$ entre, $e_1$ sort, pivot 2.
> - $x_1 = [1, \frac32, \frac12, \frac12, 0, 0 \mid \frac52]$
> - $e_2 = L - 4x_1 = [0, -5, 0, -2, 1, 0 \mid 1]$
> - $e_3 = L - 3x_1 = [0, -\frac12, \frac12, -\frac32, 0, 1 \mid \frac12]$
> - $-Z = L - 5x_1 = [0, -\frac72, \frac12, -\frac52, 0, 0 \mid -\frac{25}{2}]$
>
> | Base | x1 | x2 | <span class="in">x3</span> | e1 | e2 | e3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | x1 | 1 | 3/2 | 1/2 | 1/2 | 0 | 0 | 5/2 | 5 |
> | e2 | 0 | −5 | 0 | −2 | 1 | 0 | 1 | ✗ (0) |
> | <span class="out">e3</span> | 0 | −1/2 | <span class="pv">1/2</span> | −3/2 | 0 | 1 | 1/2 | **1** ✅ |
> | −Z | 0 | −7/2 | **1/2** | −5/2 | 0 | 0 | −25/2 | |
>
> **It. 2** : $x_3$ entre (seul positif), $e_3$ sort, pivot 1/2.
> - $x_3 = L_{e3} \times 2 = [0, -1, 1, -3, 0, 2 \mid 1]$
> - $x_1 = L - \frac12 x_3 = [1, 2, 0, 2, 0, -1 \mid 2]$
> - $e_2$ inchangée (coef 0)
> - $-Z = L - \frac12 x_3 = [0, -3, 0, -1, 0, -1 \mid -13]$
>
> | Base | x1 | x2 | x3 | e1 | e2 | e3 | b |
> |---|---|---|---|---|---|---|---|
> | x1 | 1 | 2 | 0 | 2 | 0 | −1 | **2** |
> | e2 | 0 | −5 | 0 | −2 | 1 | 0 | **1** |
> | x3 | 0 | −1 | 1 | −3 | 0 | 2 | **1** |
> | −Z | 0 | −3 | 0 | −1 | 0 | −1 | **−13** |
>
> Tout ≤ 0 → **optimum : $x_1 = 2$, $x_2 = 0$, $x_3 = 1$, $Z_{\max} = 13$.**
> Vérif : $4 + 0 + 1 = 5$ ✓ (saturée) ; $8 + 2 = 10 \le 11$ ✓ (écart $e_2 = 1$) ; $6 + 2 = 8$ ✓ (saturée) ; $Z = 10 + 3 = 13$ ✓
> *(Ce tableau final resservira dans [[Ex 7 - Dualité]], exercice 7.3.)*

---

## Exercice 5.3 — Problème en texte + interprétation

> [!exercice] Énoncé
> Un menuisier fabrique des tables et des chaises.
> - Table : **4 h** de menuiserie, **2 h** de finition, profit **70 DH**.
> - Chaise : **3 h** de menuiserie, **1 h** de finition, profit **50 DH**.
> - Disponible : **240 h** de menuiserie, **100 h** de finition.
>
> 1. Modéliser. 2. Résoudre par le simplexe. 3. Quelles contraintes sont saturées ? 4. Que vaudrait 1 heure de finition supplémentaire ?

> [!solution]- ✅ Correction
> **1.** $x_1$ = tables, $x_2$ = chaises : $\max Z = 70x_1 + 50x_2$ ; $4x_1 + 3x_2 \le 240$ ; $2x_1 + x_2 \le 100$ ; $x \ge 0$.
>
> **2.**
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|
> | e1 | 4 | 3 | 1 | 0 | 240 | 60 |
> | <span class="out">e2</span> | <span class="pv">2</span> | 1 | 0 | 1 | 100 | **50** ✅ |
> | −Z | **70** | 50 | 0 | 0 | 0 | |
>
> **It. 1** : $x_1 = [1, \frac12, 0, \frac12 \mid 50]$ ; $e_1 = L - 4x_1 = [0, 1, 1, -2 \mid 40]$ ; $-Z = L - 70x_1 = [0, 15, 0, -35 \mid -3500]$
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|
> | <span class="out">e1</span> | 0 | <span class="pv">1</span> | 1 | −2 | 40 | **40** ✅ |
> | x1 | 1 | 1/2 | 0 | 1/2 | 50 | 100 |
> | −Z | 0 | **15** | 0 | −35 | −3500 | |
>
> **It. 2** : $x_2 = [0, 1, 1, -2 \mid 40]$ ; $x_1 = L - \frac12 x_2 = [1, 0, -\frac12, \frac32 \mid 30]$ ; $-Z = L - 15x_2 = [0, 0, -15, -5 \mid -4100]$
>
> | Base | x1 | x2 | e1 | e2 | b |
> |---|---|---|---|---|---|
> | x2 | 0 | 1 | 1 | −2 | **40** |
> | x1 | 1 | 0 | −1/2 | 3/2 | **30** |
> | −Z | 0 | 0 | −15 | −5 | **−4100** |
>
> **Optimum : 30 tables, 40 chaises, Z = 4100 DH.**
> **3.** $e_1 = e_2 = 0$ → menuiserie ($120 + 120 = 240$) et finition ($60 + 40 = 100$) **toutes les deux saturées**.
> **4.** Sous $e_2$ dans −Z : **−5** → 1 h de finition en plus rapporterait **5 DH** (et 1 h de menuiserie : 15 DH). Ce sont les **prix marginaux** = solution du dual.

➡️ [[Ex 6 - Deux phases]]
