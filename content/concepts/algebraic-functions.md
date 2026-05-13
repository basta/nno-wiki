---
title: Algebraic functions
---

A function $y = f(x)$ is **algebraic** if it satisfies a polynomial equation
$$P(x_1, \dots, x_n, y) = 0$$
for some non-zero polynomial $P \in \mathbb{R}[x_1, \dots, x_n, y]$. Equivalently, the graph of $f$ is contained in a real-algebraic variety (the zero set of a polynomial).

A **real-algebraic set** is the zero locus of a finite system of polynomial equations.

## Examples

- Polynomials, rational functions on their domain.
- $\sqrt{x}$ on $x \ge 0$ (satisfies $y^2 - x = 0$).
- $\sqrt{1 - x^2}$ (a branch of $y^2 + x^2 - 1 = 0$).
- Roots of $y^5 + y + x = 0$ — algebraic but with no closed-form radical expression.

## Non-examples

- $\exp$, $\log$, $\sin$ — transcendental.
- ReLU $= \max(0, x)$ — its graph is the union of two half-lines, which is **not** a real variety (no single polynomial vanishes on it without vanishing everywhere). ReLU is [[concepts/semialgebraic|semialgebraic]] but not algebraic.
- $|x|$ — same reason.

## Relationship to semialgebraic

| Class | Defined by | Example | Non-example |
|---|---|---|---|
| Algebraic | $P(x,y) = 0$ | $\sqrt{x}$ | ReLU |
| [[concepts/semialgebraic\|Semialgebraic]] | polynomial equalities **and inequalities** | ReLU, $\|x\|$ | $\exp$ |

**Algebraic $\subsetneq$ Semialgebraic.** Inequalities (the strict containment) are exactly what semialgebraic adds.

## Why this matters for NNO

Polynomial / algebraic layers fall under $\mathbb{R}_{\mathrm{alg}}$, but most useful piecewise-linear activations need the semialgebraic class. Smooth activations (sigmoid, GELU, …) need the larger [[concepts/o-minimal-structures|o-minimal expansions]] $\mathbb{R}_{\exp}$ or $\mathbb{R}_{\mathrm{an,exp}}$ since they are transcendental.

## See also

- [[concepts/semialgebraic]]
- [[concepts/o-minimal-structures]]
