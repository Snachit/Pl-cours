---
tags: [exercices, entrainement, examen]
---
# 12 — Exercices d'entraînement type examen

🏠 [[00 - Accueil]] · ⬅️ [[11 - Exercices du cours corrigés]] · 📋 [[22 - Modèle de rédaction pour l'examen]]

> [!examen] Mode examen
> Nouveaux exercices construits **sur le modèle du TP**, toutes les solutions ont été **vérifiées par calcul exact**.
> ⏱️ Chronomètre-toi. Feuille blanche, pas de notes. Déplie la solution **seulement après**.

| # | Thème | Difficulté | Temps visé |
|---|---|---|---|
| 1 | Deux phases, min, 2 variables (+ vérif graphique) | ⭐⭐ | 20 min |
| 2 | Deux phases avec =, ≥ et ≤ | ⭐⭐⭐ | 30 min |
| 3 | **Modélisation + deux phases + dual** (le plus proche du TP) | ⭐⭐⭐⭐ | 40 min |
| 4 | Détecter un problème impossible | ⭐⭐ | 10 min |
| 5 | Construire un dual (cas général) | ⭐⭐⭐ | 10 min |

---

## Exercice 1

> [!exercice] Énoncé
> $$\min Z = 2x_1 + 3x_2 \quad\text{s.c.}\quad x_1 + x_2 \ge 4,\quad x_1 + 3x_2 \ge 6,\quad x_1,x_2\ge0$$
> 1. Résoudre par la méthode des deux phases.
> 2. Vérifier graphiquement.

> [!solution]- Solution
> **Forme standard** : $x_1 + x_2 - e_1 + a_1 = 4$ ; $x_1 + 3x_2 - e_2 + a_2 = 6$.
> $Z_A = a_1 + a_2 = 10 - 2x_1 - 4x_2 + e_1 + e_2$ → ligne ZA $= [2, 4, -1, -1 \mid 10]$.
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | a1 | 1 | 1 | −1 | 0 | 1 | 0 | 4 | 4 |
> | <span class="out">a2</span> | 1 | <span class="pv">3</span> | 0 | −1 | 0 | 1 | 6 | **2** ✅ |
> | −Z | 2 | 3 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | 2 | **4** | −1 | −1 | 0 | 0 | 10 | |
>
> **It. 1** : $x_2$ entre (4), $a_2$ sort, pivot 3.
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | <span class="out">a1</span> | <span class="pv">2/3</span> | 0 | −1 | 1/3 | 1 | −1/3 | 2 | 2 ÷ 2/3 = **3** ✅ |
> | x2 | 1/3 | 1 | 0 | −1/3 | 0 | 1/3 | 2 | 2 ÷ 1/3 = 6 |
> | −Z | 1 | 0 | 0 | 1 | 0 | −1 | −6 | |
> | ZA | **2/3** | 0 | −1 | 1/3 | 0 | −4/3 | 2 | |
>
> **It. 2** : $x_1$ entre (2/3 > 1/3), $a_1$ sort, pivot 2/3.
>
> | Base | x1 | x2 | e1 | e2 | a1 | a2 | b |
> |---|---|---|---|---|---|---|---|
> | x1 | 1 | 0 | −3/2 | 1/2 | 3/2 | −1/2 | 3 |
> | x2 | 0 | 1 | 1/2 | −1/2 | −1/2 | 1/2 | 1 |
> | −Z | 0 | 0 | 3/2 | 1/2 | −3/2 | −1/2 | −9 |
> | ZA | 0 | 0 | 0 | 0 | −1 | −1 | **0** ✅ |
>
> **Phase II** : après suppression de $a_1, a_2$, ZA, la ligne −Z vaut $[0, 0, \frac32, \frac12 \mid -9]$ : **aucun coefficient négatif** → c'est **déjà optimal** (ça peut arriver : la phase II a 0 itération).
>
> **Solution** : $x_1^* = 3$, $x_2^* = 1$, $Z_{\min} = 2(3) + 3(1) = 9$.
> Vérif : $3 + 1 = 4 \ge 4$ ✓ ; $3 + 3 = 6 \ge 6$ ✓.
> **Graphique** : sommets $(0 ; 4) \to 12$, $(3 ; 1) \to 9$ ✅, $(6 ; 0) \to 12$.
> **Dual** (bonus) : sous $e_1, e_2$ → $y_1 = \frac32$, $y_2 = \frac12$ ; $Z' = 4(\frac32) + 6(\frac12) = 9$ ✓.

---

## Exercice 2

> [!exercice] Énoncé
> $$\min Z = 4x_1 + x_2 \quad\text{s.c.}\quad 3x_1 + x_2 = 3,\quad 4x_1 + 3x_2 \ge 6,\quad x_1 + 2x_2 \le 4,\quad x_1,x_2\ge0$$
> Résoudre par la méthode des deux phases.

> [!solution]- Solution
> **Forme standard** :
> $$3x_1 + x_2 + a_1 = 3 \qquad 4x_1 + 3x_2 - e_2 + a_2 = 6 \qquad x_1 + 2x_2 + e_3 = 4$$
> Base de départ : $\{a_1, a_2, e_3\}$. ZA = ligne($a_1$) + ligne($a_2$) $= [7, 4, -1, 0 \mid 9]$.
>
> | Base | <span class="in">x1</span> | x2 | e2 | e3 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | <span class="out">a1</span> | <span class="pv">3</span> | 1 | 0 | 0 | 1 | 0 | 3 | **1** ✅ |
> | a2 | 4 | 3 | −1 | 0 | 0 | 1 | 6 | 3/2 |
> | e3 | 1 | 2 | 0 | 1 | 0 | 0 | 4 | 4 |
> | −Z | 4 | 1 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | **7** | 4 | −1 | 0 | 0 | 0 | 9 | |
>
> **It. 1** : $x_1$ entre, $a_1$ sort, pivot 3.
>
> | Base | x1 | <span class="in">x2</span> | e2 | e3 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | x1 | 1 | 1/3 | 0 | 0 | 1/3 | 0 | 1 | 3 |
> | <span class="out">a2</span> | 0 | <span class="pv">5/3</span> | −1 | 0 | −4/3 | 1 | 2 | **6/5** ✅ |
> | e3 | 0 | 5/3 | 0 | 1 | −1/3 | 0 | 3 | 9/5 |
> | −Z | 0 | −1/3 | 0 | 0 | −4/3 | 0 | −4 | |
> | ZA | 0 | **5/3** | −1 | 0 | −7/3 | 0 | 2 | |
>
> **It. 2** : $x_2$ entre, $a_2$ sort, pivot 5/3.
>
> | Base | x1 | x2 | e2 | e3 | a1 | a2 | b |
> |---|---|---|---|---|---|---|---|
> | x1 | 1 | 0 | 1/5 | 0 | 3/5 | −1/5 | 3/5 |
> | x2 | 0 | 1 | −3/5 | 0 | −4/5 | 3/5 | 6/5 |
> | e3 | 0 | 0 | 1 | 1 | 1 | −1 | 1 |
> | −Z | 0 | 0 | −1/5 | 0 | −8/5 | 1/5 | −18/5 |
> | ZA | 0 | 0 | 0 | 0 | −1 | −1 | **0** ✅ |
>
> **Phase II**
>
> | Base | x1 | x2 | <span class="in">e2</span> | e3 | b | Rapport |
> |---|---|---|---|---|---|---|
> | x1 | 1 | 0 | 1/5 | 0 | 3/5 | 3 |
> | x2 | 0 | 1 | −3/5 | 0 | 6/5 | ✗ |
> | <span class="out">e3</span> | 0 | 0 | <span class="pv">1</span> | 1 | 1 | **1** ✅ |
> | −Z | 0 | 0 | **−1/5** | 0 | −18/5 | |
>
> **min** → coefficient négatif −1/5 sous $e_2$ → $e_2$ entre ; $e_3$ sort ; pivot 1.
>
> | Base | x1 | x2 | e2 | e3 | b |
> |---|---|---|---|---|---|
> | x1 | 1 | 0 | 0 | −1/5 | 2/5 |
> | x2 | 0 | 1 | 0 | 3/5 | 9/5 |
> | e2 | 0 | 0 | 1 | 1 | 1 |
> | −Z | 0 | 0 | 0 | 1/5 | −17/5 |
>
> Tous ≥ 0 → **optimum** : $x_1^* = \frac25$, $x_2^* = \frac95$, $Z_{\min} = \frac{17}{5} = 3{,}4$.
> Vérif : $3(\frac25) + \frac95 = \frac{15}{5} = 3$ ✓ ; $\frac85 + \frac{27}{5} = 7 \ge 6$ ✓ (surplus $e_2 = 1$) ; $\frac25 + \frac{18}{5} = 4 \le 4$ ✓ ; $Z = \frac85 + \frac95 = \frac{17}{5}$ ✓

---

## Exercice 3 — Le plus proche de l'examen ⭐

> [!exercice] Énoncé
> Un data center doit garantir **au moins 8 unités de calcul** et **au moins 6 unités de stockage**. Il peut louer trois types de serveurs :
>
> | Serveur | Calcul | Stockage | Coût (k DH) |
> |---|---|---|---|
> | S1 | 1 | 2 | 6 |
> | S2 | 2 | 1 | 8 |
> | S3 | 3 | 2 | 12 |
>
> 1. Formuler le PL.
> 2. Le résoudre par la méthode des deux phases.
> 3. Écrire le dual, le résoudre graphiquement et vérifier le théorème de dualité forte.
> 4. Retrouver la solution du dual dans le tableau final du primal.

> [!solution]- 1) Modèle
> $x_1, x_2, x_3$ = nombre de serveurs S1, S2, S3 loués.
> $$\min Z = 6x_1 + 8x_2 + 12x_3 \quad\text{s.c.}\quad x_1 + 2x_2 + 3x_3 \ge 8\ \text{(calcul)},\quad 2x_1 + x_2 + 2x_3 \ge 6\ \text{(stockage)},\quad x_j \ge 0$$

> [!solution]- 2) Deux phases
> $x_1 + 2x_2 + 3x_3 - e_1 + a_1 = 8$ ; $2x_1 + x_2 + 2x_3 - e_2 + a_2 = 6$.
> $Z_A = 14 - 3x_1 - 3x_2 - 5x_3 + e_1 + e_2$ → ligne ZA $= [3, 3, 5, -1, -1 \mid 14]$.
>
> | Base | x1 | x2 | <span class="in">x3</span> | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | <span class="out">a1</span> | 1 | 2 | <span class="pv">3</span> | −1 | 0 | 1 | 0 | 8 | **8/3** ✅ |
> | a2 | 2 | 1 | 2 | 0 | −1 | 0 | 1 | 6 | 3 |
> | −Z | 6 | 8 | 12 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | 3 | 3 | **5** | −1 | −1 | 0 | 0 | 14 | |
>
> **It. 1** : $x_3$ entre (5), $a_1$ sort ($\frac83 < 3$), pivot 3.
>
> | Base | <span class="in">x1</span> | x2 | x3 | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | x3 | 1/3 | 2/3 | 1 | −1/3 | 0 | 1/3 | 0 | 8/3 | 8 |
> | <span class="out">a2</span> | <span class="pv">4/3</span> | −1/3 | 0 | 2/3 | −1 | −2/3 | 1 | 2/3 | **1/2** ✅ |
> | −Z | 2 | 0 | 0 | 4 | 0 | −4 | 0 | −32 | |
> | ZA | **4/3** | −1/3 | 0 | 2/3 | −1 | −5/3 | 0 | 2/3 | |
>
> **It. 2** : $x_1$ entre (4/3 > 2/3), $a_2$ sort, pivot 4/3.
>
> | Base | x1 | x2 | x3 | e1 | e2 | a1 | a2 | b |
> |---|---|---|---|---|---|---|---|---|
> | x3 | 0 | 3/4 | 1 | −1/2 | 1/4 | 1/2 | −1/4 | 5/2 |
> | x1 | 1 | −1/4 | 0 | 1/2 | −3/4 | −1/2 | 3/4 | 1/2 |
> | −Z | 0 | 1/2 | 0 | 3 | 3/2 | −3 | −3/2 | −33 |
> | ZA | 0 | 0 | 0 | 0 | 0 | −1 | −1 | **0** ✅ |
>
> **Phase II** : ligne −Z $= [0, \frac12, 0, 3, \frac32 \mid -33]$ → tous ≥ 0 → **déjà optimal**.
>
> **Solution** : $x_1^* = \frac12$, $x_2^* = 0$, $x_3^* = \frac52$, $Z_{\min} = 6(\frac12) + 12(\frac52) = 3 + 30 = 33$ k DH.
> Vérif : $\frac12 + \frac{15}{2} = 8 \ge 8$ ✓ ; $1 + 5 = 6 \ge 6$ ✓.
> *(Remarque : en pratique on louerait un nombre entier de serveurs → ce serait un PLNE, résolu par Branch and Bound ; ici on reste en continu comme au cours.)*

> [!solution]- 3) Dual + graphique
> $$\max Z' = 8y_1 + 6y_2 \quad\text{s.c.}\quad y_1 + 2y_2 \le 6,\quad 2y_1 + y_2 \le 8,\quad 3y_1 + 2y_2 \le 12,\quad y_1,y_2\ge0$$
> ![[graph-ex3-dual.svg]]
>
> | Sommet | $Z' = 8y_1 + 6y_2$ |
> |---|---|
> | (0 ; 0) | 0 |
> | (4 ; 0) | 32 |
> | **(3 ; 3/2)** : $y_1 + 2y_2 = 6$ ∩ $3y_1 + 2y_2 = 12$ ⇒ $2y_1 = 6$ | **33** ✅ |
> | (0 ; 3) | 18 |
>
> $Z'^* = 33 = Z^*$ ✓ **dualité forte**.
> Complémentarité : $2y_1 + y_2 = 7.5 < 8$ → 2ᵉ contrainte duale non saturée ⇒ $x_2 = 0$ ✓. $y_1, y_2 > 0$ ⇒ les deux contraintes primales saturées ⇒ système $x_1 + 3x_3 = 8$, $2x_1 + 2x_3 = 6$ ⇒ $x_3 = \frac52$, $x_1 = \frac12$ ✓.

> [!solution]- 4) Lecture dans le tableau final du primal
> Ligne −Z finale : $[0,\ \frac12,\ 0,\ 3,\ \frac32 \mid -33]$.
> Sous les **excédents** $e_1, e_2$ : $y_1^* = 3$, $y_2^* = \frac32$ ✓.
> Sous $x_2$ : $\frac12$ = écart de la 2ᵉ contrainte duale ($8 - 7{,}5$) ✓.

---

## Exercice 4 — Impossible ?

> [!exercice] Énoncé
> $$\max Z = x_1 + x_2 \quad\text{s.c.}\quad x_1 + 2x_2 \le 4,\quad x_1 + x_2 \ge 6,\quad x_1,x_2 \ge 0$$

> [!solution]- Solution
> $x_1 + 2x_2 + e_1 = 4$ ; $x_1 + x_2 - e_2 + a_2 = 6$. ZA $= [1, 1, 0, -1 \mid 6]$.
>
> It. 1 : $x_1$ entre (égalité 1/1 avec $x_2$, on prend le premier), rapports $4/1 = 4$ et $6/1 = 6$ → $e_1$ sort.
>
> | Base | x1 | x2 | e1 | e2 | a2 | b |
> |---|---|---|---|---|---|---|
> | x1 | 1 | 2 | 1 | 0 | 0 | 4 |
> | a2 | 0 | −1 | −1 | −1 | 1 | **2** |
> | −Z | 0 | −1 | −1 | 0 | 0 | −4 |
> | ZA | 0 | −1 | −1 | −1 | 0 | **2** |
>
> Plus aucun coefficient positif dans ZA mais **$Z_A = 2 \ne 0$** ($a_2 = 2$ en base) ⇒ **aucune solution réalisable**.
> Explication : $x_1 + x_2 \le x_1 + 2x_2 \le 4 < 6$. Les contraintes sont contradictoires.

---

## Exercice 5 — Construire un dual (cas général)

> [!exercice] Énoncé
> $$\max Z = 3x_1 + 2x_2 - x_3 \quad\text{s.c.}\quad \begin{cases}x_1 + x_2 + x_3 \le 10\\ 2x_1 - x_2 \ge 2\\ x_1 + 3x_3 = 6\end{cases}\quad x_1 \ge 0,\ x_2 \ge 0,\ x_3 \in \mathbb{R}$$

> [!solution]- Solution
> Primal = **max** → dual = **min**, 3 contraintes → 3 variables $y_1, y_2, y_3$.
> - Contrainte 1 « ≤ » (normale pour un max) → $y_1 \ge 0$
> - Contrainte 2 « ≥ » (inversée pour un max) → $y_2 \le 0$
> - Contrainte 3 « = » → $y_3 \in \mathbb{R}$
> - $x_1 \ge 0$ → contrainte duale **≥** ; $x_2 \ge 0$ → **≥** ; $x_3$ libre → **=**
>
> Colonnes de $A$ : $x_1 : (1, 2, 1)$ ; $x_2 : (1, -1, 0)$ ; $x_3 : (1, 0, 3)$.
> $$
> (D)\begin{cases}
> \min Z' = 10y_1 + 2y_2 + 6y_3\\
> y_1 + 2y_2 + y_3 \ge 3\\
> y_1 - y_2 \ge 2\\
> y_1 + 3y_3 = -1\\
> y_1 \ge 0,\ y_2 \le 0,\ y_3 \in \mathbb{R}
> \end{cases}
> $$

➡️ Révision finale : [[20 - Fiche résumé]]
