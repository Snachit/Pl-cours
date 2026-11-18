---
tags: [exercices, examen-blanc, examen]
---
# Ex 9 — 📝 Examen blanc (2 h · /20)

⬅️ [[Ex 8 - Cas particuliers]] · [[Exercices]] · 📋 [[22 - Modèle de rédaction pour l'examen]]

> [!examen] Conditions réelles
> ⏱️ **2 heures**, sans notes, sans calculatrice si possible (fractions à la main).
> Rédige comme dans [[22 - Modèle de rédaction pour l'examen]]. Corrige-toi ensuite avec le **barème** et note ton score dans [[Exercices]].

---

## 📄 Sujet

> [!exercice] Exercice 1 — Questions de cours (4 pts)
> 1. Définir la **forme standard** d'un programme linéaire. (1 pt)
> 2. Pourquoi introduit-on des **variables artificielles** ? Que conclut-on si $Z_A \ne 0$ à la fin de la phase I ? (1 pt)
> 3. Énoncer le **théorème de dualité forte** et les **conditions de complémentarité**. (1 pt)
> 4. Comment reconnaît-on, dans un tableau du simplexe, un problème **non borné** ? et des **solutions multiples** ? (1 pt)

> [!exercice] Exercice 2 — Modélisation et résolution graphique (5 pts)
> Une start-up développe des applications **web** et **mobiles**.
> - Une appli web demande **4 jours** de développement et **1 jour** de test ; elle rapporte **3 k DH**.
> - Une appli mobile demande **2 jours** de développement et **3 jours** de test ; elle rapporte **4 k DH**.
> - L'équipe dispose de **40 jours** de développement et **30 jours** de test.
> - Un client impose **au moins 2 applis mobiles**.
>
> 1. Formuler le programme linéaire. (1,5 pt)
> 2. Le résoudre graphiquement. (2,5 pts)
> 3. Quelles contraintes sont saturées ? (1 pt)

> [!exercice] Exercice 3 — Méthode des deux phases (8 pts)
> $$\min Z = 8x_1 + 6x_2 + 10x_3 \quad\text{s.c.}\quad 2x_1 + x_2 + 2x_3 \ge 8,\quad x_1 + 2x_2 + 3x_3 \ge 10,\quad x_1,x_2,x_3 \ge 0$$
> 1. Mettre sous forme standard et écrire $Z_A$. (1,5 pt)
> 2. Phase I. (3 pts)
> 3. Phase II et solution optimale. (2,5 pts)
> 4. Vérification. (1 pt)

> [!exercice] Exercice 4 — Dualité (3 pts)
> 1. Écrire le dual du PL de l'exercice 3. (1 pt)
> 2. Le résoudre graphiquement et vérifier le théorème de dualité forte. (1,5 pt)
> 3. Où lit-on la solution du dual dans le tableau final de l'exercice 3 ? (0,5 pt)

---

## ✅ Corrigé et barème

> [!solution]- Exercice 1 — Cours (4 pts)
> 1. Forme standard : **toutes les contraintes sont des égalités**, **toutes les variables sont ≥ 0**, objectif max ou min. (1)
> 2. Avec des contraintes **≥** ou **=**, il n'y a pas de base réalisable évidente (un excédent serait négatif) ; les artificielles forcent une base de départ. Si $Z_A \ne 0$ en fin de phase I → **aucune solution réalisable**. (0,5 + 0,5)
> 3. Dualité forte : si P et D ont des solutions optimales, **$Z^* = Z'^*$**. Complémentarité : $x_j^* > 0$ ⇒ j-ième contrainte duale saturée ; contrainte non saturée ⇒ variable associée nulle (et symétriquement pour $y_i$). (0,5 + 0,5)
> 4. Non borné : la colonne de la variable entrante n'a **aucun coefficient > 0**. Multiples : à l'optimum, une variable **hors base** a un coefficient **0** dans la ligne objectif (ratio > 0). (0,5 + 0,5)

> [!solution]- Exercice 2 — Modélisation + graphique (5 pts)
> **1.** $x_1$ = applis web, $x_2$ = applis mobiles. (0,5)
> $$\max Z = 3x_1 + 4x_2 \quad\text{s.c.}\quad 4x_1 + 2x_2 \le 40\ \text{(dév.)},\quad x_1 + 3x_2 \le 30\ \text{(test)},\quad x_2 \ge 2,\quad x_1,x_2 \ge 0 \quad (1)$$
> **2.** ![[exam-Q2.svg]]
>
> | Sommet | Obtenu par | $Z = 3x_1 + 4x_2$ |
> |---|---|---|
> | (0 ; 2) | $x_1 = 0$, $x_2 = 2$ | 8 |
> | (9 ; 2) | $4x_1 + 2x_2 = 40$, $x_2 = 2$ | 35 |
> | **(6 ; 8)** | $4x_1 + 2x_2 = 40$ ∩ $x_1 + 3x_2 = 30$ | **50** ✅ |
> | (0 ; 10) | $x_1 + 3x_2 = 30$, $x_1 = 0$ | 40 |
>
> Calcul : $x_1 = 30 - 3x_2$ ⇒ $120 - 12x_2 + 2x_2 = 40$ ⇒ $x_2 = 8$, $x_1 = 6$.
> **6 applis web, 8 applis mobiles, Z = 50 k DH.** (tracé 1 + sommets 1 + conclusion 0,5)
>
> **3.** Développement $24 + 16 = 40$ → **saturée** ; test $6 + 24 = 30$ → **saturée** ; $x_2 = 8 > 2$ → non saturée (surplus 6). (1)

> [!solution]- Exercice 3 — Deux phases (8 pts)
> **1. Forme standard** (1,5)
> $$2x_1 + x_2 + 2x_3 - e_1 + a_1 = 8 \qquad x_1 + 2x_2 + 3x_3 - e_2 + a_2 = 10$$
> $$\min Z_A = a_1 + a_2 = 18 - 3x_1 - 3x_2 - 5x_3 + e_1 + e_2$$
>
> **2. Phase I** (3)
>
> | Base | x1 | x2 | <span class="in">x3</span> | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | a1 | 2 | 1 | 2 | −1 | 0 | 1 | 0 | 8 | 4 |
> | <span class="out">a2</span> | 1 | 2 | <span class="pv">3</span> | 0 | −1 | 0 | 1 | 10 | **10/3** ✅ |
> | −Z | 8 | 6 | 10 | 0 | 0 | 0 | 0 | 0 | |
> | ZA | 3 | 3 | **5** | −1 | −1 | 0 | 0 | 18 | |
>
> **It. 1** : $x_3$ entre (5), $a_2$ sort ($\frac{10}{3} < 4$), pivot 3.
> - $x_3 = [\frac13, \frac23, 1, 0, -\frac13, 0, \frac13 \mid \frac{10}{3}]$
> - $a_1 = L - 2x_3 = [\frac43, -\frac13, 0, -1, \frac23, 1, -\frac23 \mid \frac43]$
> - $-Z = L - 10x_3 = [\frac{14}{3}, -\frac23, 0, 0, \frac{10}{3}, 0, -\frac{10}{3} \mid -\frac{100}{3}]$
> - ZA $= L - 5x_3 = [\frac43, -\frac13, 0, -1, \frac23, 0, -\frac53 \mid \frac43]$
>
> | Base | <span class="in">x1</span> | x2 | x3 | e1 | e2 | a1 | a2 | b | Rapport |
> |---|---|---|---|---|---|---|---|---|---|
> | <span class="out">a1</span> | <span class="pv">4/3</span> | −1/3 | 0 | −1 | 2/3 | 1 | −2/3 | 4/3 | **1** ✅ |
> | x3 | 1/3 | 2/3 | 1 | 0 | −1/3 | 0 | 1/3 | 10/3 | 10 |
> | −Z | 14/3 | −2/3 | 0 | 0 | 10/3 | 0 | −10/3 | −100/3 | |
> | ZA | **4/3** | −1/3 | 0 | −1 | 2/3 | 0 | −5/3 | 4/3 | |
>
> **It. 2** : $x_1$ entre (4/3 > 2/3), $a_1$ sort, pivot 4/3.
> - $x_1 = L \times \frac34 = [1, -\frac14, 0, -\frac34, \frac12, \frac34, -\frac12 \mid 1]$
> - $x_3 = L - \frac13 x_1 = [0, \frac34, 1, \frac14, -\frac12, -\frac14, \frac12 \mid 3]$
> - $-Z = L - \frac{14}{3}x_1 = [0, \frac12, 0, \frac72, 1, -\frac72, -1 \mid -38]$
> - ZA $= [0, 0, 0, 0, 0, -1, -1 \mid 0]$ ✅ → **fin de la phase I**, $Z_A = 0$.
>
> **3. Phase II** (2,5) — on supprime $a_1, a_2$ et ZA :
>
> | Base | x1 | x2 | x3 | e1 | e2 | b |
> |---|---|---|---|---|---|---|
> | x1 | 1 | −1/4 | 0 | −3/4 | 1/2 | **1** |
> | x3 | 0 | 3/4 | 1 | 1/4 | −1/2 | **3** |
> | −Z | 0 | 1/2 | 0 | 7/2 | 1 | **−38** |
>
> Problème de **min** : tous les coefficients de −Z sont **≥ 0** → la solution est **déjà optimale**.
> $$\boxed{x_1^* = 1,\ x_2^* = 0,\ x_3^* = 3,\qquad Z_{\min} = 8(1) + 10(3) = 38}$$
>
> **4. Vérification** (1) : $2 + 0 + 6 = 8 \ge 8$ ✓ ; $1 + 0 + 9 = 10 \ge 10$ ✓ — les deux contraintes sont **saturées**.

> [!solution]- Exercice 4 — Dualité (3 pts)
> **1.** (1)
> $$\max Z' = 8y_1 + 10y_2 \quad\text{s.c.}\quad 2y_1 + y_2 \le 8,\quad y_1 + 2y_2 \le 6,\quad 2y_1 + 3y_2 \le 10,\quad y_1,y_2 \ge 0$$
> **2.** (1,5) ![[exam-Q4.svg]]
>
> | Sommet | $Z' = 8y_1 + 10y_2$ |
> |---|---|
> | O(0 ; 0) | 0 |
> | (4 ; 0) | 32 |
> | **(3,5 ; 1)** : $2y_1 + y_2 = 8$ ∩ $2y_1 + 3y_2 = 10$ ⇒ $2y_2 = 2$ | **38** ✅ |
> | (2 ; 2) : $2y_1 + 3y_2 = 10$ ∩ $y_1 + 2y_2 = 6$ | 36 |
> | (0 ; 3) | 30 |
>
> $Z'^* = 38 = Z^*$ ✓ **dualité forte**. (Complémentarité : $y_1 + 2y_2 = 5{,}5 < 6$ → non saturée ⇒ $x_2 = 0$ ✓.)
>
> **3.** (0,5) Dans la ligne −Z finale de l'exercice 3, sous les **excédents** $e_1$ et $e_2$ : $y_1 = \frac72$, $y_2 = 1$ ✓.

> [!astuce] Après l'examen blanc
> - < 12/20 : refais [[10 - TP corrigé - Deux phases (modèle d'examen)]] et [[Ex 6 - Deux phases]].
> - 12–16 : relis [[21 - Pièges et conventions des tableaux]] et refais les itérations où tu t'es trompé.
> - \> 16 : tu es prêt·e 💪 — entraîne-toi juste à aller plus vite.
