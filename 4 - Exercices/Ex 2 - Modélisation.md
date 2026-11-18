---
tags: [exercices, modelisation]
---
# Ex 2 — Modélisation

⬅️ [[Ex 1 - Introduction]] · [[Exercices]] · ➡️ [[Ex 3 - Résolution graphique]] · 📖 [[02 - Modélisation d'un PL]]

> [!methode] Rappel de la méthode (5 étapes)
> 1. « On pose $x_1$ = … (unité) » → 2. Objectif max/min → 3. Une contrainte par ressource ou exigence → 4. $x_j \ge 0$ → 5. Vérifier les unités et le sens des inégalités.
> « au plus / disponible » = **≤** · « au moins / minimum » = **≥** · « exactement » = **=**

---

## Exercice 2.1 — L'agriculteur (max, 2 variables)

> [!exercice] Énoncé
> Un agriculteur dispose de **100 hectares** pour cultiver du blé et du maïs.
> - Un hectare de blé demande **1 jour** de travail et rapporte **300 DH**.
> - Un hectare de maïs demande **2 jours** de travail et rapporte **500 DH**.
> - Il dispose de **160 jours** de travail au total.
> - Un contrat l'oblige à cultiver **au moins 20 hectares** de blé.
>
> 1. Formuler le programme linéaire.
> 2. De quelle forme s'agit-il (canonique I, II, mixte) ? Quelle méthode utiliser ?
> 3. *(Bonus)* Résoudre graphiquement.

> [!solution]- ✅ Correction
> **1.** $x_1$ = hectares de blé, $x_2$ = hectares de maïs.
> $$
> \begin{cases}
> \max Z = 300x_1 + 500x_2\\
> x_1 + x_2 \le 100 & \text{(surface)}\\
> x_1 + 2x_2 \le 160 & \text{(jours de travail)}\\
> x_1 \ge 20 & \text{(contrat blé)}\\
> x_1, x_2 \ge 0
> \end{cases}
> $$
> **2.** Max avec des **≤** et un **≥** → **forme mixte**. 2 variables → **graphique** ; par le simplexe il faudrait les **deux phases** (à cause du ≥).
>
> **3.** Sommets : $(20 ; 0) \to 6000$ ; $(100 ; 0) \to 30\,000$ ; $(40 ; 60) \to 42\,000$ ✅ ; $(20 ; 70) \to 41\,000$.
> $(40 ; 60)$ : $x_1 + x_2 = 100$ et $x_1 + 2x_2 = 160$ ⇒ $x_2 = 60$, $x_1 = 40$.
> **Optimum : 40 ha de blé, 60 ha de maïs, Z = 42 000 DH.** Surface et jours **saturés**, contrat dépassé de 20 ha.

---

## Exercice 2.2 — Problème de transport (4 variables)

> [!exercice] Énoncé
> Deux usines U1 et U2 produisent au maximum **50** et **70** unités. Deux clients C1 et C2 demandent **exactement 40** et **60** unités. Coûts unitaires de transport (DH) :
>
> | | C1 | C2 |
> |---|---|---|
> | U1 | 4 | 6 |
> | U2 | 5 | 3 |
>
> 1. Définir les variables de décision (attention aux indices).
> 2. Écrire le PL complet puis sa forme matricielle ($A$, $B$, $C$).
> 3. *(Bonus)* Trouver intuitivement une solution optimale et son coût.

> [!solution]- ✅ Correction
> **1.** $x_{ij}$ = quantité transportée de l'usine $i$ vers le client $j$ : $x_{11}, x_{12}, x_{21}, x_{22}$.
>
> **2.**
> $$
> \begin{cases}
> \min Z = 4x_{11} + 6x_{12} + 5x_{21} + 3x_{22}\\
> x_{11} + x_{12} \le 50 & \text{(capacité U1)}\\
> x_{21} + x_{22} \le 70 & \text{(capacité U2)}\\
> x_{11} + x_{21} = 40 & \text{(demande C1)}\\
> x_{12} + x_{22} = 60 & \text{(demande C2)}\\
> x_{ij} \ge 0
> \end{cases}
> $$
> $X = (x_{11}, x_{12}, x_{21}, x_{22})^t$, $C^t = (4, 6, 5, 3)$,
> $$A = \begin{pmatrix}1&1&0&0\\0&0&1&1\\1&0&1&0\\0&1&0&1\end{pmatrix},\quad B = \begin{pmatrix}50\\70\\40\\60\end{pmatrix}$$
> (ici les 2 dernières lignes sont des égalités).
>
> **3.** Chaque client prend sa route la moins chère : C1 ← U1 (4 < 5), C2 ← U2 (3 < 6), et les capacités suffisent (40 ≤ 50, 60 ≤ 70).
> $x_{11} = 40$, $x_{22} = 60$, les autres = 0 ; **Z = 160 + 180 = 340 DH** (confirmé par le simplexe en deux phases).

---

## Exercice 2.3 — Allocation de machines virtuelles (3 variables, forme mixte) ⭐

> [!exercice] Énoncé
> Un serveur cloud possède **32 vCPU** et **96 Go de RAM**. On peut y louer trois types de machines virtuelles :
>
> | VM | vCPU | RAM (Go) | Revenu (DH/h) |
> |---|---|---|---|
> | Small | 1 | 2 | 10 |
> | Medium | 2 | 8 | 25 |
> | Large | 4 | 16 | 45 |
>
> Le client exige **au moins 2 VM Large**, et le serveur doit héberger **exactement 14 VM** au total.
> 1. Formuler le PL qui maximise le revenu horaire.
> 2. Écrire sa forme standard et la base de départ.
> 3. Quelle méthode faut-il utiliser ? Pourquoi ?

> [!solution]- ✅ Correction
> **1.** $x_1, x_2, x_3$ = nombre de VM Small, Medium, Large.
> $$
> \begin{cases}
> \max Z = 10x_1 + 25x_2 + 45x_3\\
> x_1 + 2x_2 + 4x_3 \le 32 & \text{(vCPU)}\\
> 2x_1 + 8x_2 + 16x_3 \le 96 & \text{(RAM)}\\
> x_3 \ge 2 & \text{(Large minimum)}\\
> x_1 + x_2 + x_3 = 14 & \text{(total)}\\
> x_1, x_2, x_3 \ge 0
> \end{cases}
> $$
> **2.**
> $$
> \begin{cases}
> x_1 + 2x_2 + 4x_3 + e_1 = 32\\
> 2x_1 + 8x_2 + 16x_3 + e_2 = 96\\
> x_3 - e_3 + a_3 = 2\\
> x_1 + x_2 + x_3 + a_4 = 14
> \end{cases}
> \qquad \text{Base de départ : } \{e_1, e_2, a_3, a_4\}
> $$
> **3.** Il y a un **≥** et un **=** → pas de base réalisable évidente → **méthode des deux phases**, avec $\min Z_A = a_3 + a_4 = 16 - x_1 - x_2 - 2x_3 + e_3$ (ligne ZA du TP : $[1, 1, 2, 0, 0, -1 \mid 16]$).
>
> *(Pour info : la solution continue est $x = (\frac{64}{7}, 0, \frac{34}{7})$, $Z = 310$. Comme on ne peut pas louer 9,14 VM, le vrai problème est un **PLNE** → Branch and Bound.)*

➡️ [[Ex 3 - Résolution graphique]]
