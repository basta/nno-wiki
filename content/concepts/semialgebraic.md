---
title: Semialgebraic sets and functions
---

A subset $S \subseteq \mathbb{R}^n$ is **semialgebraic** if it is a finite Boolean combination (union, intersection, complement) of sets of the form
$$\{x \in \mathbb{R}^n : p(x) = 0\} \quad \text{or} \quad \{x \in \mathbb{R}^n : p(x) > 0\}$$
for polynomials $p \in \mathbb{R}[x_1, \dots, x_n]$.

A function $f: A \to \mathbb{R}^m$ is **semialgebraic** if its graph is a semialgebraic subset of $\mathbb{R}^{n+m}$.

## Key properties

- **Tarski–Seidenberg theorem**: the projection of a semialgebraic set is semialgebraic. Equivalently, the class is closed under quantifier elimination over the real-closed field.
- Semialgebraic sets are exactly the [[concepts/definable-functions|definable]] sets in the [[concepts/o-minimal-structures|o-minimal structure]] $\mathbb{R}_{\mathrm{alg}} = (\mathbb{R}, <, +, \cdot, 0, 1)$.
- Closed under finite unions/intersections, complements, projections, composition, and continuous semialgebraic inverses.
- Every semialgebraic set admits a finite [[concepts/cell-decomposition|cell decomposition]] into semialgebraic cells.

## Examples relevant to deep learning

- $\max(0, x)$ (ReLU), $|x|$, $\min$, $\max$.
- Indicator of a polyhedron, hinge loss, $\ell_1$- and $\ell_\infty$-norms.
- Piecewise-polynomial functions on semialgebraic pieces.
- Max-pooling, sorting-based layers (top-$k$).

## Relation to algebraic functions

[[concepts/algebraic-functions|Algebraic functions]] are a strict subclass: an algebraic function is a (multi-)function $y$ implicitly defined by $P(x, y) = 0$ for some polynomial $P$. Every algebraic function is semialgebraic, but ReLU is semialgebraic and **not** algebraic (its graph is not a real variety).

## See also

- [[concepts/algebraic-functions]]
- [[concepts/o-minimal-structures]]
- [[concepts/definable-functions]]
