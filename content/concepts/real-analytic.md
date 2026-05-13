---
title: Real-analytic functions
---

A function $f : U \to \mathbb{R}$ on an open set $U \subseteq \mathbb{R}$ is **real-analytic** if it is locally given by a convergent power series: for every $x_0 \in U$ there is some $r > 0$ such that

$$
f(x) = \sum_{n=0}^{\infty} a_n (x - x_0)^n
$$

for all $x$ with $|x - x_0| < r$. Polynomials, $\exp$, $\sin$, $\cos$, and $\log$ (on its domain) are real-analytic; piecewise-defined functions like ReLU and $|x|$ are not.

## Identity theorem (the one fact we use)

> **Accumulation point.** $x_0$ is an *accumulation point* of a set $S \subseteq \mathbb{R}$ if every open interval around $x_0$ contains a point of $S$ other than $x_0$ itself. Equivalently, there is a sequence $(x_n)$ in $S \setminus \{x_0\}$ with $x_n \to x_0$. Intuition: $S$ "clusters" at $x_0$. Examples:
> - The set $\{1/n : n \in \mathbb{N}\}$ has $0$ as its only accumulation point (and $0$ is not in the set).
> - Any open interval $(a, b)$ has every point of $[a, b]$ as an accumulation point.
> - A finite set has **no** accumulation points — every point is isolated.

**Theorem.** Let $f : I \to \mathbb{R}$ be real-analytic on an open connected interval $I \subseteq \mathbb{R}$. If the zero set $\{x \in I : f(x) = 0\}$ has an accumulation point in $I$, then $f \equiv 0$ on $I$.

Equivalently: a non-zero real-analytic function has **isolated** zeros (finite set on every compact subinterval). Equivalently: two real-analytic functions that agree on a set with an accumulation point agree everywhere.

*Why it's true (sketch).* At an accumulation point $x_0$ of the zero set, every Taylor coefficient $a_n = f^{(n)}(x_0)/n!$ must vanish (by an easy induction using continuity of $f^{(n)}$ and Rolle's theorem applied to nearby zeros). So the power series at $x_0$ is identically zero, hence $f$ vanishes on a neighborhood of $x_0$. The set of points where $f$ vanishes on a neighborhood is then both open (by the series argument) and closed (by continuity), so by connectedness it is all of $I$.

## How this is used

The identity theorem is the basic finiteness mechanism for analytic functions: it lets you upgrade "vanishes on a small set" to "vanishes everywhere", which is why **restricted** analytic functions (analytic functions on a compact box) behave well in [[concepts/o-minimal-structures|o-minimal]] settings — the structure $\mathbb{R}_{\mathrm{an}}$. It's also the reason transcendental functions like $\exp$ are not [[concepts/semialgebraic|semialgebraic]]: a polynomial that agreed with $\exp$ on an infinite set would, by the identity theorem applied to the difference, have to equal $\exp$ identically, which is impossible.

> Folklore from undergraduate complex/real analysis; §5.3 of the course notes sets the language.

## See also

- [[concepts/semialgebraic]]
- [[concepts/o-minimal-structures]]
