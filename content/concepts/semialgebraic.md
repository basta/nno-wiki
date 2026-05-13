---
title: Semialgebraic sets and functions
---

A subset $S \subseteq \mathbb{R}^n$ is **semialgebraic** if it is a finite Boolean combination (union, intersection, complement) of sets of the form
$$\{x \in \mathbb{R}^n : p(x) = 0\} \quad \text{or} \quad \{x \in \mathbb{R}^n : p(x) > 0\}$$
for polynomials $p \in \mathbb{R}[x_1, \dots, x_n]$.

A function $f: A \to \mathbb{R}^m$ is **semialgebraic** if its graph is a semialgebraic subset of $\mathbb{R}^{n+m}$.

## Key properties

- **Tarski–Seidenberg theorem**: the projection of a semialgebraic set is semialgebraic. Equivalently, the class is closed under quantifier elimination over the real-closed field.
- Semialgebraic sets are exactly the [[concepts/definable-sets|definable sets]] in the [[concepts/o-minimal-structures|o-minimal structure]] $\mathbb{R}_{\mathrm{alg}} = (\mathbb{R}, <, +, \cdot, 0, 1)$.
- Closed under finite unions/intersections, complements, projections, composition, and continuous semialgebraic inverses.
- Every semialgebraic set admits a finite [[concepts/cell-decomposition|cell decomposition]] into semialgebraic cells.

## Examples relevant to deep learning

- $\max(0, x)$ (ReLU), $|x|$, $\min$, $\max$.
- Indicator of a polyhedron, hinge loss, $\ell_1$- and $\ell_\infty$-norms.
- Piecewise-polynomial functions on semialgebraic pieces.
- Max-pooling, sorting-based layers (top-$k$).

## Relation to algebraic functions

[[concepts/algebraic-functions|Algebraic functions]] are a strict subclass: an algebraic function is a (multi-)function $y$ implicitly defined by $P(x, y) = 0$ for some polynomial $P$. Every algebraic function is semialgebraic, but ReLU is semialgebraic and **not** algebraic (its graph is not a real variety).

## Structural facts (§6)

### 1-variable classification (Lemma 6.5)

Every semialgebraic subset of $\mathbb{R}$ is a **finite union of points and open intervals**. This is the base case for cell decomposition in higher dimensions, and the cleanest statement of o-minimality for $\mathbb{R}_{\mathrm{alg}}$ in one variable.

### SOS compression (Lemma 6.12)

A finite system of polynomial equalities can be compressed into a single equality:

$$
f_1 = \cdots = f_r = 0 \iff f_1^2 + \cdots + f_r^2 = 0.
$$

Consequence: every semialgebraic set is a finite union of *basic* pieces of the form

$$
\{x : f(x) = 0,\ g_1(x) < 0,\ \ldots,\ g_s(x) < 0\}
$$

with a **single** equality. This is the normal form used in most proofs about semialgebraic sets.

*Example.* The two points on the unit circle with $x + y = 0$ are cut out by the system

$$
x^2 + y^2 - 1 = 0, \qquad x + y = 0.
$$

Compress to a single equality:

$$
(x^2 + y^2 - 1)^2 + (x + y)^2 = 0,
$$

which over $\mathbb{R}$ holds iff both summands vanish — recovering the original system. The set is now in basic form with $f(x,y) = (x^2+y^2-1)^2 + (x+y)^2$ and no inequalities.

### Semialgebraic asymptotics (6.9 + Cor. 6.10)

Every semialgebraic function $f : \mathbb{R} \to \mathbb{R}$ has a power-law tail: there exist $c \in \mathbb{R}$ and $q \in \mathbb{Q}$ such that

$$
f(t) \sim c\,t^q \quad \text{as } t \to \infty.
$$

Since $\exp$ grows faster than every polynomial (and so faster than every $c t^q$), $\exp$ **cannot be semialgebraic**. This is the moral engine behind exercise 0.4 and the reason genuinely smooth activations like $\tanh$ and sigmoid need a richer [[concepts/o-minimal-structures|o-minimal structure]] (e.g. $\mathbb{R}_{\exp}$) than $\mathbb{R}_{\mathrm{alg}}$.

## See also

- [[concepts/algebraic-functions]]
- [[concepts/o-minimal-structures]]
- [[concepts/definable-functions]]
