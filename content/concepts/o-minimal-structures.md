---
title: o-minimal structures
---

A [[concepts/structures|structure]] $\mathcal{R}$ on $\mathbb{R}$ is **o-minimal** ("order-minimal") if every [[concepts/definable-sets|definable subset]] of $\mathbb{R}$ — i.e., every $A \in \mathcal{R}_1$ — is a finite union of points and open intervals (with endpoints in $\mathbb{R} \cup \{\pm\infty\}$). This is axiom **(S6)** below.

That is: the only definable subsets of the line are those *already forced* by the order $<$, namely Boolean combinations of intervals. The "o" is for *order*; "minimal" means the one-dimensional definable sets are as simple as the order alone permits.

## o-minimal expansion

An **o-minimal expansion** of the ordered real field is a structure $\mathcal{R}$ satisfying (S1)–(S6):

- **(S1)–(S4)** the [[concepts/structures|structure axioms]] (Boolean algebra, products, projections, diagonals) — so $\mathcal{R}$ is a structure on $\mathbb{R}$.
- **(S5) Contains the ordered real field.** $\{(x, y) \in \mathbb{R}^2 : x < y\} \in \mathcal{R}_2$, and the graphs of $+ : \mathbb{R}^2 \to \mathbb{R}$ and $\cdot : \mathbb{R}^2 \to \mathbb{R}$ are in $\mathcal{R}_3$. This forces $\mathcal{R} \supseteq \mathcal{R}_{\mathrm{alg}}$ — every [[concepts/semialgebraic|semialgebraic set]] is definable.
- **(S6) o-minimality.** Every $A \in \mathcal{R}_1$ is a finite union of points and open intervals.

Equivalently: $\mathcal{R}$ has $<$, $+$, $\cdot$, and the constants $0, 1$ among its basic definable relations/functions, and is o-minimal.

"Expansion" is the model-theoretic term for *adding* basic predicates or functions to a structure: starting from $(\mathbb{R}, <, +, \cdot)$ one expands by, say, the graph of $\exp$, then closes under (S1)–(S4) to obtain a new structure. That structure is an *o-minimal expansion* iff (S6) survives the closure.

Most expansions break o-minimality immediately — for example, adding $\sin$ on all of $\mathbb{R}$ makes $\mathbb{Z} = \{x : \sin(\pi x) = 0\}$ definable, an infinite discrete set. The non-trivial content of the theory is that certain analytic functions ($\exp$, restricted analytic functions) *can* be added without breaking it.

## Why a condition only on $\mathbb{R}^1$ controls every $\mathbb{R}^n$

The one-dimensional condition looks weak, but combined with closure under [[concepts/structures|projection (S3)]] it propagates upward: definable subsets of $\mathbb{R}^n$ admit a [[concepts/cell-decomposition|cell decomposition]], definable functions are piecewise [[concepts/monotonicity-theorem|monotone]] and continuous, and a robust [[concepts/dimension-theorem|dimension theory]] exists. This is the central miracle of the subject — finiteness in dimension 1 forces tameness in all dimensions.

## Standard examples

| Structure | Adds | Captures |
|---|---|---|
| $\mathbb{R}_{\mathrm{alg}}$ | semialgebraic sets | polynomials, ReLU, max-pooling |
| $\mathbb{R}_{\mathrm{an}}$ | restricted analytic functions | bump functions, restricted $\exp$ |
| $\mathbb{R}_{\exp}$ | $\exp$ on $\mathbb{R}$ (Wilkie) | sigmoid, softplus |
| $\mathbb{R}_{\mathrm{an,exp}}$ | both | essentially every smooth activation |

## Key consequences

- [[concepts/dimension-theorem|Dimension theorem]]
- [[concepts/monotonicity-theorem|Monotonicity theorem]]
- [[concepts/cell-decomposition|Cell decomposition]]
- [[concepts/curve-selection|Curve selection]]

## See also

- [[concepts/tame-geometry]]
- [[references|van den Dries — Tame topology and o-minimal structures]]
