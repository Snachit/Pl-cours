---
tags: [revision, fiche]
---
# 20 — Fiche résumé (tout le cours sur une page)

🏠 [[00 - Accueil]] · 🧨 [[21 - Pièges et conventions des tableaux]] · 📋 [[22 - Modèle de rédaction pour l'examen]]

---

## 🔵 Modélisation — [[02 - Modélisation d'un PL]]
1. Variables de décision (avec unités) → 2. Fonction objectif (max/min) → 3. Contraintes → 4. $x_j \ge 0$ → 5. Cohérence.
« au plus / disponible » → **≤** ; « au moins / besoin » → **≥** ; « exactement » → **=**.
Matriciel : $\max C^tX$, $AX \le B$, $X \ge 0$.

## 🟢 Graphique — [[03 - Résolution graphique]]
1ᵉʳ quadrant → tracer les droites (2 points sur les axes) → demi-plans (test de O) → région admissible = intersection → sommets → **Z à chaque sommet** (ou droites parallèles : max = le plus loin de O, min = le plus proche).
**Région bornée non vide ⇒ optimum sur un sommet.**

## 🟠 Forme standard — [[04 - Formes canonique et standard]]

| Contrainte | Ajout | Base de départ |
|---|---|---|
| ≤ | $+e_i$ | $e_i$ |
| ≥ | $-e_i + a_i$ | $a_i$ |
| = | $+a_i$ | $a_i$ |

Type I : max + ≤. Type II : min + ≥. Mixte : mélange. Standard : que des =, variables ≥ 0.

## 🟣 Simplexe — [[05 - Méthode du Simplexe]]

| | **MAX** | **MIN** |
|---|---|---|
| Entrante (ligne −Z) | plus grand **> 0** | plus **négatif** |
| Sortante | min $b_i / a_{ik}$, $a_{ik} > 0$ | idem |
| Stop | tout **≤ 0** | tout **≥ 0** |
| Z | $-(\text{case b de }-Z)$ | idem |

**Pivotage** : ligne pivot ÷ pivot ; autres lignes : $L' = L - (\text{coef colonne pivot}) \times L_{\text{pivot}}'$.
Écart nul = contrainte **saturée** ; écart > 0 = **marginale**.

## 🔴 Deux phases — [[06 - Méthode des deux phases]]
- **Phase I** : $\min Z_A = \sum a_i$. Ligne ZA = **somme des lignes avec artificielle** (0 sous les $a_i$), b = $\sum b$.
  - TP : entrante = plus grand **positif** de ZA ; stop quand plus de positif.
  - (Cours : ligne −Za = opposé, entrante = plus négatif.)
  - Garder et mettre à jour la ligne −Z pendant la phase I.
- **$Z_A = 0$** → supprimer colonnes $a_i$ + ligne ZA → **Phase II** (simplexe normal sur −Z).
- **$Z_A > 0$** → **impossible**.

## 🟤 Dualité — [[07 - Dualité]]
$$\max C^tX,\ AX \le B,\ X\ge0 \iff \min B^tY,\ A^tY \ge C,\ Y \ge 0$$
- max ↔ min ; B ↔ C ; $A \to A^t$ ; 1 contrainte ↔ 1 variable.
- (max) contrainte ≤ ↔ $y \ge 0$ ; ≥ ↔ $y \le 0$ ; = ↔ $y$ libre. Variable ≥ 0 ↔ contrainte ≥ (min) ; libre ↔ =.
- **Th. 1** : P a un optimum ⇔ D en a un. **Th. 2** : $Z^* = Z'^*$.
- **Th. 3 (complémentarité)** : variable > 0 ⇒ contrainte associée saturée ; contrainte non saturée ⇒ variable associée = 0.
- **Lecture directe** : solution de l'autre problème = |coefficients de la ligne objectif finale sous les écarts / excédents / artificielles|.

## ⚫ Cas particuliers — [[08 - Cas particuliers]]

| Cas | Signal dans le tableau |
|---|---|
| Impossible | $Z_A > 0$ en fin de phase I |
| Non borné | colonne entrante toute **≤ 0** |
| Solutions multiples | coef **0** sous une hors-base à l'optimum (ratio > 0) |
| Unique | tous les coefs des hors-base **≠ 0** |

## ⭐ TP — [[10 - TP corrigé - Deux phases (modèle d'examen)]]
$\min 12x_1 + 42x_2 + 20x_3$ ; $2x_1 + 6x_2 + 2x_3 \ge 6$ ; $x_1 + 3x_2 + 2x_3 \ge 4$.
ZA $= [3, 9, 4, -1, -1 \mid 10]$ → it. 1 : $x_2$ entre, $a_1$ sort (pivot 6) → it. 2 : $x_3$ entre, $a_2$ sort (pivot 1) → $Z_A = 0$ → it. 3 : $x_1$ entre (−2), $x_2$ sort (pivot 1/3).
**$x^* = (2, 0, 1)$, $Z_{\min} = 44$** ; dual $y^* = (2, 8)$, $Z' = 44$.
