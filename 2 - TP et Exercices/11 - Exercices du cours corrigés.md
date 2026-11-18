---
tags: [exercices, corrigés]
---
# 11 — Exercices du cours : corrigés détaillés

🏠 [[00 - Accueil]] · ⬅️ [[10 - TP corrigé - Deux phases (modèle d'examen)]] · ➡️ [[12 - Exercices d'entraînement type examen]]

> [!methode] Comment travailler cette page
> Les énoncés sont visibles, les **solutions sont repliées** (callouts « Solution »). Essaie d'abord **sur papier**, puis déplie pour corriger.

---

## Exercice 1 — Mélange X et Y (graphique)

> [!exercice] Énoncé (cours, chapitre PL)
> Mélange de X et Y. Pas plus de **22 kg de X** et **14 kg de Y**. X coûte **20 DH**, Y **40 DH**.
> X contient 2 kg de A, 1 kg de B, 1 kg de C ; Y contient 1 kg de A, 1 kg de B, 3 kg de C.
> Besoins : **au moins** 14 kg de A, 12 kg de B, 18 kg de C. Minimiser le coût.

> [!solution]- Solution
> **Modèle** : $x$ = kg de X, $y$ = kg de Y.
> $$\min Z = 20x + 40y \quad\text{s.c.}\quad 2x + y \ge 14,\ \ x + y \ge 12,\ \ x + 3y \ge 18,\ \ x \le 22,\ \ y \le 14,\ \ x,y\ge0$$
> ![[graph-melange.svg]]
> **Sommets de la région** (vérifiés dans toutes les contraintes) :
>
> | Sommet | Intersection | $Z = 20x + 40y$ |
> |---|---|---|
> | (0 ; 14) | $x = 0$ et $y = 14$ | 560 |
> | (2 ; 10) | $2x + y = 14$ et $x + y = 12$ ⇒ $x = 2$ | 440 |
> | **(9 ; 3)** | $x + y = 12$ et $x + 3y = 18$ ⇒ $2y = 6$ | **300** ✅ |
> | (18 ; 0) | $x + 3y = 18$ et $y = 0$ | 360 |
> | (22 ; 0) | $x = 22$ et $y = 0$ | 440 |
> | (22 ; 14) | $x = 22$ et $y = 14$ | 1000 |
>
> **Optimum : acheter 9 kg de X et 3 kg de Y, coût minimal 300 DH.**
> Vérif : A : $18 + 3 = 21 \ge 14$ ✓ ; B : $12 \ge 12$ ✓ ; C : $9 + 9 = 18 \ge 18$ ✓.

---

## Exercice 2 — Les pilules (graphique)

Corrigé complet dans [[03 - Résolution graphique#3. Exercice du cours - les pilules]] : **2 petites + 8 grandes pilules = 10 pilules**.

---

## Exercice 3 — Pièces P1 et P2 (simplexe + graphique)

> [!exercice] Énoncé (cours, chapitre Simplexe)
> P1 : 3 h en A1, 6 h en A2. P2 : 4 h en A1, 3 h en A2. Disponibilités : A1 = 160 h, A2 = 180 h. Marges : 1200 (P1), 1000 (P2). Maximiser.

> [!solution]- Solution par le simplexe
> **Modèle** : $x_1$ = nombre de P1, $x_2$ = nombre de P2.
> $$\max Z = 1200x_1 + 1000x_2 \quad\text{s.c.}\quad 3x_1 + 4x_2 \le 160,\quad 6x_1 + 3x_2 \le 180,\quad x_1,x_2 \ge 0$$
> **Forme standard** : $3x_1 + 4x_2 + e_1 = 160$ ; $6x_1 + 3x_2 + e_2 = 180$.
>
> **Tableau initial**
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|
> | e1 | 3 | 4 | 1 | 0 | 160 | 160/3 ≈ 53,3 |
> | <span class="out">e2</span> | <span class="pv">6</span> | 3 | 0 | 1 | 180 | 180/6 = **30** ✅ |
> | −Z | **1200** | 1000 | 0 | 0 | 0 | |
>
> Entrante $x_1$ (1200), sortante $e_2$, pivot 6.
> - $x_1$ : $[6, 3, 0, 1 \mid 180] \div 6 = [1, \frac12, 0, \frac16 \mid 30]$
> - $e_1$ : $[3, 4, 1, 0 \mid 160] - 3\times[1, \frac12, 0, \frac16 \mid 30] = [0, \frac52, 1, -\frac12 \mid 70]$
> - $-Z$ : $[1200, 1000, 0, 0 \mid 0] - 1200\times[\dots] = [0, 400, 0, -200 \mid -36000]$
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|
> | <span class="out">e1</span> | 0 | <span class="pv">5/2</span> | 1 | −1/2 | 70 | 70 ÷ 5/2 = **28** ✅ |
> | x1 | 1 | 1/2 | 0 | 1/6 | 30 | 30 ÷ 1/2 = 60 |
> | −Z | 0 | **400** | 0 | −200 | −36 000 | |
>
> Entrante $x_2$ (400), sortante $e_1$, pivot 5/2.
> - $x_2$ : $[0, \frac52, 1, -\frac12 \mid 70] \times \frac25 = [0, 1, \frac25, -\frac15 \mid 28]$
> - $x_1$ : $[1, \frac12, 0, \frac16 \mid 30] - \frac12\times[0, 1, \frac25, -\frac15 \mid 28] = [1, 0, -\frac15, \frac{4}{15} \mid 16]$
> - $-Z$ : $[0, 400, 0, -200 \mid -36000] - 400\times[0, 1, \frac25, -\frac15 \mid 28] = [0, 0, -160, -120 \mid -47200]$
>
> | Base | x1 | x2 | e1 | e2 | b |
> |---|---|---|---|---|---|
> | x2 | 0 | 1 | 2/5 | −1/5 | **28** |
> | x1 | 1 | 0 | −1/5 | 4/15 | **16** |
> | −Z | 0 | 0 | −160 | −120 | **−47 200** |
>
> Tous ≤ 0 → **optimum** : $x_1 = 16$, $x_2 = 28$, $Z_{\max} = 47\,200$. Les deux ateliers sont **saturés** ($e_1 = e_2 = 0$).
> Vérif : $3(16) + 4(28) = 48 + 112 = 160$ ✓ ; $6(16) + 3(28) = 96 + 84 = 180$ ✓ ; $Z = 19\,200 + 28\,000 = 47\,200$ ✓

> [!solution]- Solution graphique
> ![[graph-P1P2.svg]]
>
> | Sommet | $Z = 1200x_1 + 1000x_2$ |
> |---|---|
> | O(0 ; 0) | 0 |
> | (0 ; 40) | 40 000 |
> | **(16 ; 28)** : $3x_1 + 4x_2 = 160$ ∩ $6x_1 + 3x_2 = 180$ | **47 200** ✅ |
> | (30 ; 0) | 36 000 |
>
> Calcul de l'intersection : $\times 2$ la 1ʳᵉ : $6x_1 + 8x_2 = 320$ ; moins la 2ᵉ : $5x_2 = 140 \Rightarrow x_2 = 28$ ; puis $3x_1 = 160 - 112 = 48 \Rightarrow x_1 = 16$.
> Le simplexe a suivi le chemin **O → (30 ; 0) → (16 ; 28)** : chaque tableau = un sommet !

---

## Exercice 4 — Déchets Plastique et Métal (deux phases, max)

> [!exercice] Énoncé (cours, chapitre Deux phases)
> Plastique : 40 €/t ; Métal : 30 €/t. Temps : 2 h/t (P), 1 h/t (M), total **≤ 16 h**. Obligation de traiter **au minimum 4 t** au total. Coût : 10 €/t (P), 20 €/t (M), budget **exactement 80 €**.
> 1) Formuler le PL. 2) Résoudre par la méthode des deux phases.

> [!solution]- 1) Formulation
> $x_1$ = tonnes de Plastique, $x_2$ = tonnes de Métal.
> $$
> \begin{cases}
> \max Z = 40x_1 + 30x_2\\
> 2x_1 + x_2 \le 16 & \text{(temps)}\\
> x_1 + x_2 \ge 4 & \text{(engagement)}\\
> 10x_1 + 20x_2 = 80 & \text{(budget)}\\
> x_1, x_2 \ge 0
> \end{cases}
> $$

> [!solution]- 2) Forme standard et phase I
> $$2x_1 + x_2 + e_1 = 16 \qquad x_1 + x_2 - e_2 + a_2 = 4 \qquad 10x_1 + 20x_2 + a_3 = 80$$
> (≤ → écart $e_1$ ; ≥ → excédent $e_2$ + artificielle $a_2$ ; = → artificielle $a_3$)
>
> $\min Z_A = a_2 + a_3 = 84 - 11x_1 - 21x_2 + e_2$ → ligne ZA = ligne($a_2$) + ligne($a_3$) = $[11, 21, 0, -1 \mid 84]$.
>
> **Tableau initial**
>
> | Base | x1 | <span class="in">x2</span> | e1 | e2 | a2 | a3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | e1 | 2 | 1 | 1 | 0 | 0 | 0 | 16 | 16 |
> | <span class="out">a2</span> | 1 | <span class="pv">1</span> | 0 | −1 | 1 | 0 | 4 | **4** ✅ |
> | a3 | 10 | 20 | 0 | 0 | 0 | 1 | 80 | 4 (égalité) |
> | −Z | 40 | 30 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | 11 | **21** | 0 | −1 | 0 | 0 | 84 | |
>
> Entrante $x_2$ (21). **Égalité des rapports** (4 et 4) : on choisit la première ($a_2$). Pivot 1.
> - $x_2$ : $[1, 1, 0, -1, 1, 0 \mid 4]$
> - $e_1$ : $L - 1\times L_{x2} = [1, 0, 1, 1, -1, 0 \mid 12]$
> - $a_3$ : $L - 20\times L_{x2} = [-10, 0, 0, 20, -20, 1 \mid 0]$
> - $-Z$ : $L - 30\times L_{x2} = [10, 0, 0, 30, -30, 0 \mid -120]$
> - ZA : $L - 21\times L_{x2} = [-10, 0, 0, 20, -21, 0 \mid 0]$
>
> | Base | x1 | x2 | e1 | <span class="in">e2</span> | a2 | a3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|
> | e1 | 1 | 0 | 1 | 1 | −1 | 0 | 12 | 12 |
> | x2 | 1 | 1 | 0 | −1 | 1 | 0 | 4 | ✗ |
> | <span class="out">a3</span> | −10 | 0 | 0 | <span class="pv">20</span> | −20 | 1 | 0 | 0/20 = **0** ✅ |
> | −Z | 10 | 0 | 0 | 30 | −30 | 0 | −120 | |
> | ZA | −10 | 0 | 0 | **20** | −21 | 0 | 0 | |
>
> ⚠️ $Z_A = 0$ mais $a_3$ est **encore en base (valeur 0)** et il reste un coefficient positif (20) → on continue : entrante $e_2$, sortante $a_3$ (rapport 0 : pivot **dégénéré**, les valeurs ne changent pas). Pivot 20.
> - $e_2$ : $[-10, 0, 0, 20, -20, 1 \mid 0] \div 20 = [-\frac12, 0, 0, 1, -1, \frac1{20} \mid 0]$
> - $e_1$ : $L - 1\times L_{e2} = [\frac32, 0, 1, 0, 0, -\frac1{20} \mid 12]$
> - $x_2$ : $L + 1\times L_{e2} = [\frac12, 1, 0, 0, 0, \frac1{20} \mid 4]$
> - $-Z$ : $L - 30\times L_{e2} = [25, 0, 0, 0, 0, -\frac32 \mid -120]$
> - ZA : $L - 20\times L_{e2} = [0, 0, 0, 0, -1, -1 \mid 0]$ ✅
>
> **Fin de phase I** : $Z_A = 0$, les deux artificielles sont hors base.

> [!solution]- 3) Phase II
> On supprime $a_2$, $a_3$ et la ligne ZA :
>
> | Base | <span class="in">x1</span> | x2 | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|
> | <span class="out">e1</span> | <span class="pv">3/2</span> | 0 | 1 | 0 | 12 | 12 ÷ 3/2 = **8** ✅ |
> | x2 | 1/2 | 1 | 0 | 0 | 4 | 4 ÷ 1/2 = 8 (égalité) |
> | e2 | −1/2 | 0 | 0 | 1 | 0 | ✗ |
> | −Z | **25** | 0 | 0 | 0 | −120 | |
>
> **max** → entrante $x_1$ (25 > 0). Égalité des rapports → on prend $e_1$. Pivot 3/2.
> - $x_1$ : $[\frac32, 0, 1, 0 \mid 12] \times \frac23 = [1, 0, \frac23, 0 \mid 8]$
> - $x_2$ : $L - \frac12 L_{x1} = [0, 1, -\frac13, 0 \mid 0]$
> - $e_2$ : $L + \frac12 L_{x1} = [0, 0, \frac13, 1 \mid 4]$
> - $-Z$ : $L - 25 L_{x1} = [0, 0, -\frac{50}{3}, 0 \mid -320]$
>
> | Base | x1 | x2 | e1 | e2 | b |
> |---|---|---|---|---|---|
> | x1 | 1 | 0 | 2/3 | 0 | **8** |
> | x2 | 0 | 1 | −1/3 | 0 | **0** |
> | e2 | 0 | 0 | 1/3 | 1 | **4** |
> | −Z | 0 | 0 | −50/3 | 0 | **−320** |
>
> Tous ≤ 0 → **optimum**.
> **Solution : 8 t de Plastique, 0 t de Métal, gain maximal Z = 320 €.**
> Vérif : temps $2(8) = 16 \le 16$ ✓ (saturée) ; engagement $8 \ge 4$ ✓ (surplus $e_2 = 4$) ; budget $10(8) = 80$ ✓.
>
> 💡 $x_2 = 0$ **en base** : solution **dégénérée** (c'est la conséquence des égalités de rapports). Ce n'est pas une erreur.

---

## Exercice 5 — PL mixte de l'introduction des deux phases

> [!exercice] Énoncé (exemple d'introduction du cours, non résolu dans les diapos)
> $$\max Z = 20x_1 + 25x_2 + 4x_3 \quad\text{s.c.}\quad 2x_1 + 3x_2 + 5x_3 \le 40,\ \ 4x_1 + 2x_2 + 3x_3 \ge 20,\ \ 4x_1 + 2x_2 + x_3 = 10,\ \ x_j \ge 0$$

> [!solution]- Solution complète
> **Forme standard** : $2x_1 + 3x_2 + 5x_3 + e_1 = 40$ ; $4x_1 + 2x_2 + 3x_3 - e_2 + a_2 = 20$ ; $4x_1 + 2x_2 + x_3 + a_3 = 10$.
> $Z_A = a_2 + a_3$ → ligne ZA = $[8, 4, 4, 0, -1 \mid 30]$.
>
> **Phase I — tableau initial**
>
> | Base | <span class="in">x1</span> | x2 | x3 | e1 | e2 | a2 | a3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | e1 | 2 | 3 | 5 | 1 | 0 | 0 | 0 | 40 | 20 |
> | a2 | 4 | 2 | 3 | 0 | −1 | 1 | 0 | 20 | 5 |
> | <span class="out">a3</span> | <span class="pv">4</span> | 2 | 1 | 0 | 0 | 0 | 1 | 10 | **5/2** ✅ |
> | −Z | 20 | 25 | 4 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | **8** | 4 | 4 | 0 | −1 | 0 | 0 | 30 | |
>
> **Après itération 1** ($x_1$ entre, $a_3$ sort, pivot 4)
>
> | Base | x1 | x2 | <span class="in">x3</span> | e1 | e2 | a2 | a3 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | e1 | 0 | 2 | 9/2 | 1 | 0 | 0 | −1/2 | 35 | 70/9 ≈ 7,8 |
> | <span class="out">a2</span> | 0 | 0 | <span class="pv">2</span> | 0 | −1 | 1 | −1 | 10 | **5** ✅ |
> | x1 | 1 | 1/2 | 1/4 | 0 | 0 | 0 | 1/4 | 5/2 | 10 |
> | −Z | 0 | 15 | −1 | 0 | 0 | 0 | −5 | −50 | |
> | ZA | 0 | 0 | **2** | 0 | −1 | 0 | −2 | 10 | |
>
> **Après itération 2** ($x_3$ entre, $a_2$ sort, pivot 2)
>
> | Base | x1 | x2 | x3 | e1 | e2 | a2 | a3 | b |
> |---|---|---|---|---|---|---|---|---|
> | e1 | 0 | 2 | 0 | 1 | 9/4 | −9/4 | 7/4 | 25/2 |
> | x3 | 0 | 0 | 1 | 0 | −1/2 | 1/2 | −1/2 | 5 |
> | x1 | 1 | 1/2 | 0 | 0 | 1/8 | −1/8 | 3/8 | 5/4 |
> | −Z | 0 | 15 | 0 | 0 | −1/2 | 1/2 | −11/2 | −45 |
> | ZA | 0 | 0 | 0 | 0 | 0 | −1 | −1 | **0** ✅ |
>
> **Phase II** (on supprime $a_2, a_3$, ZA)
>
> | Base | x1 | <span class="in">x2</span> | x3 | e1 | e2 | b | Rapport |
> |---|---|---|---|---|---|---|---|
> | e1 | 0 | 2 | 0 | 1 | 9/4 | 25/2 | 25/4 |
> | x3 | 0 | 0 | 1 | 0 | −1/2 | 5 | ✗ |
> | <span class="out">x1</span> | 1 | <span class="pv">1/2</span> | 0 | 0 | 1/8 | 5/4 | **5/2** ✅ |
> | −Z | 0 | **15** | 0 | 0 | −1/2 | −45 | |
>
> **Après itération 3** ($x_2$ entre, $x_1$ sort, pivot 1/2)
>
> | Base | x1 | x2 | x3 | e1 | e2 | b |
> |---|---|---|---|---|---|---|
> | e1 | −4 | 0 | 0 | 1 | 7/4 | 15/2 |
> | x3 | 0 | 0 | 1 | 0 | −1/2 | 5 |
> | x2 | 2 | 1 | 0 | 0 | 1/4 | 5/2 |
> | −Z | −30 | 0 | 0 | 0 | −17/4 | −165/2 |
>
> Tous ≤ 0 → **optimum** : $x_1 = 0$, $x_2 = \frac52$, $x_3 = 5$, $Z_{\max} = \frac{165}{2} = 82{,}5$.
> Vérif : $3(2{,}5) + 5(5) = 32{,}5 \le 40$ ✓ ; $2(2{,}5) + 3(5) = 20 \ge 20$ ✓ ; $2(2{,}5) + 5 = 10$ ✓ ; $Z = 62{,}5 + 20 = 82{,}5$ ✓

---

## Exercice 6 — Dual de l'exemple 2 et construction de duals

Voir [[07 - Dualité#Exemples avec cas particuliers]] : cache la colonne « Dual » et retrouve-la seul.

➡️ Ensuite : [[12 - Exercices d'entraînement type examen]]
