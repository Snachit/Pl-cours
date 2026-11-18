---
tags: [exercices, graphique]
---
# Ex 3 — Résolution graphique

⬅️ [[Ex 2 - Modélisation]] · [[Exercices]] · ➡️ [[Ex 4 - Forme standard]] · 📖 [[03 - Résolution graphique]]

> [!methode] Rappel
> Tracer chaque droite (2 points sur les axes) → garder le bon demi-plan (test de O) → région admissible → sommets (systèmes 2×2) → **tableau des Z** → conclure.
> ⚠️ Vérifier que chaque sommet respecte **toutes** les contraintes.

---

## Exercice 3.1 — Maximisation avec 4 contraintes

> [!exercice] Énoncé
> $$\max Z = 5x_1 + 4x_2 \quad\text{s.c.}\quad 6x_1 + 4x_2 \le 24,\quad x_1 + 2x_2 \le 6,\quad -x_1 + x_2 \le 1,\quad x_2 \le 2,\quad x_1,x_2 \ge 0$$
> Résoudre graphiquement (méthode analytique **et** méthode géométrique).

> [!solution]- ✅ Correction
> **Droites :**
>
> | Contrainte | Points de tracé | Côté gardé |
> |---|---|---|
> | $6x_1 + 4x_2 = 24$ | $(0 ; 6)$, $(4 ; 0)$ | côté de O |
> | $x_1 + 2x_2 = 6$ | $(0 ; 3)$, $(6 ; 0)$ | côté de O |
> | $-x_1 + x_2 = 1$ | $(0 ; 1)$, $(1 ; 2)$ | côté de O ($0 \le 1$ vrai) |
> | $x_2 = 2$ | horizontale | en dessous |
>
> ![[ex-G1.svg]]
>
> **Sommets et valeurs de Z :**
>
> | Sommet | Obtenu par | $Z = 5x_1 + 4x_2$ |
> |---|---|---|
> | O(0 ; 0) | origine | 0 |
> | (4 ; 0) | $6x_1 + 4x_2 = 24$, $x_2 = 0$ | 20 |
> | **(3 ; 1,5)** | $6x_1 + 4x_2 = 24$ ∩ $x_1 + 2x_2 = 6$ | **21** ✅ |
> | (2 ; 2) | $x_1 + 2x_2 = 6$ ∩ $x_2 = 2$ | 18 |
> | (1 ; 2) | $-x_1 + x_2 = 1$ ∩ $x_2 = 2$ | 13 |
> | (0 ; 1) | $-x_1 + x_2 = 1$, $x_1 = 0$ | 4 |
>
> Calcul de (3 ; 1,5) : $x_1 = 6 - 2x_2$ ⇒ $6(6 - 2x_2) + 4x_2 = 24$ ⇒ $36 - 8x_2 = 24$ ⇒ $x_2 = 1{,}5$, $x_1 = 3$.
> **Méthode géométrique** : les droites $5x_1 + 4x_2 = p$ s'éloignent de O ; la dernière qui touche la région passe par $(3 ; 1{,}5)$ avec $p = 21$.
> **Solution : $x_1^* = 3$, $x_2^* = 1{,}5$, $Z_{\max} = 21$.**

---

## Exercice 3.2 — Minimisation, région non bornée

> [!exercice] Énoncé
> $$\min Z = 3x_1 + 2x_2 \quad\text{s.c.}\quad 2x_1 + x_2 \ge 6,\quad x_1 + x_2 \ge 4,\quad x_1 + 3x_2 \ge 6,\quad x_1,x_2 \ge 0$$
> 1. Résoudre graphiquement.
> 2. Pourquoi l'optimum existe-t-il alors que la région n'est pas bornée ?

> [!solution]- ✅ Correction
> ![[ex-G2.svg]]
>
> | Sommet | Obtenu par | $Z = 3x_1 + 2x_2$ |
> |---|---|---|
> | (0 ; 6) | $2x_1 + x_2 = 6$, $x_1 = 0$ | 12 |
> | **(2 ; 2)** | $2x_1 + x_2 = 6$ ∩ $x_1 + x_2 = 4$ ⇒ $x_1 = 2$ | **10** ✅ |
> | (3 ; 1) | $x_1 + x_2 = 4$ ∩ $x_1 + 3x_2 = 6$ ⇒ $2x_2 = 2$ | 11 |
> | (6 ; 0) | $x_1 + 3x_2 = 6$, $x_2 = 0$ | 18 |
>
> Vérif de (2 ; 2) dans la 3ᵉ : $2 + 6 = 8 \ge 6$ ✓.
> **Solution : $x_1^* = 2$, $x_2^* = 2$, $Z_{\min} = 10$.**
>
> **2.** On **minimise** avec des coefficients positifs : Z augmente quand on s'éloigne de l'origine. La région part à l'infini « vers le haut/droite », donc dans la direction où Z **augmente** : le minimum est atteint sur un sommet proche de l'origine. (Un **max** sur cette région serait **non borné**.)

---

## Exercice 3.3 — Problème en texte (modélisation + graphique)

> [!exercice] Énoncé
> Une entreprise fabrique des imprimantes ($x_1$) et des scanners ($x_2$). Profit : **40 DH** par imprimante, **30 DH** par scanner.
> - Au plus **12 appareils** par jour (capacité de stockage).
> - Montage : 2 h par imprimante, 1 h par scanner, **16 h** disponibles.
> - Une commande impose **au moins 2 imprimantes** par jour.
>
> Formuler puis résoudre graphiquement. Quelles contraintes sont saturées ?

> [!solution]- ✅ Correction
> $$\max Z = 40x_1 + 30x_2 \quad\text{s.c.}\quad x_1 + x_2 \le 12,\quad 2x_1 + x_2 \le 16,\quad x_1 \ge 2,\quad x_1,x_2\ge0$$
> ![[ex-G3.svg]]
>
> | Sommet | Obtenu par | $Z$ |
> |---|---|---|
> | (2 ; 0) | $x_1 = 2$, $x_2 = 0$ | 80 |
> | (8 ; 0) | $2x_1 + x_2 = 16$, $x_2 = 0$ | 320 |
> | **(4 ; 8)** | $x_1 + x_2 = 12$ ∩ $2x_1 + x_2 = 16$ ⇒ $x_1 = 4$ | **400** ✅ |
> | (2 ; 10) | $x_1 = 2$ ∩ $x_1 + x_2 = 12$ | 380 |
>
> **Solution : 4 imprimantes et 8 scanners, Z = 400 DH.**
> Saturées : stockage ($4 + 8 = 12$) et montage ($8 + 8 = 16$). Non saturée : commande ($4 > 2$, surplus de 2).

➡️ [[Ex 4 - Forme standard]]
