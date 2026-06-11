---
title: Pfaffian functions
---

A **Pfaffian function** (Khovanskii) is one that satisfies a *triangular* system of first-order differential equations with polynomial right-hand sides. "Triangular" is the load-bearing word: each function's derivative is a polynomial in the coordinates and in the functions **already introduced** — never in functions defined later. This is the closure-under-antiderivatives condition that produces the $\mathrm{Pfaff}(\cdot)$ structures in the [[concepts/universe-of-structures|universe of structures]], and it is the mechanism by which $\arctan$, $\mathrm{erf}$, and GELU become [[concepts/definable-functions|definable]] and tame.

## The definition

A **Pfaffian chain** on an open domain $U \subseteq \mathbb{R}^n$ is a sequence of functions $f_1, \dots, f_r : U \to \mathbb{R}$ such that

$$
\frac{\partial f_i}{\partial x_j}(x) = P_{ij}\big(x,\, f_1(x), \dots, f_i(x)\big)
$$

for all $i \le r$, $j \le n$, where each $P_{ij}$ is a polynomial. The right-hand side references only $f_1, \dots, f_i$ — this is the triangularity.

A **Pfaffian function** is any polynomial $Q\big(x, f_1(x), \dots, f_r(x)\big)$ in the coordinates and the chain. The pair $(r, \text{degrees})$ is the *complexity* of the chain; Khovanskii's theory bounds geometric quantities (number of zeros, connected components) purely in terms of it.

## Why this is the right notion for tameness

The defining feature is **closure under antidifferentiation**: if $g$ is already in your chain and $f' = P(x, g, f)$ for a polynomial $P$, then $f$ extends the chain. So "solve a first-order ODE whose data you already have" keeps you inside the Pfaffian world.

> **Khovanskii's finiteness theorem.** A system of $n$ Pfaffian equations in $n$ variables, of complexity $C$, has at most $N(C)$ non-degenerate solutions, with $N$ an explicit bound depending only on $C$ — not on the particular functions.

This uniform finiteness is the geometric engine behind [[concepts/o-minimal-structures|o-minimality]]: it forbids the infinitely-oscillating behavior (like $\sin$ on all of $\mathbb{R}$) that o-minimality rules out.

> **Speissegger's theorem (1999).** The *Pfaffian closure* of any o-minimal structure — the smallest expansion closed under taking solutions of Pfaffian equations / antiderivatives of definable functions — is again o-minimal.

Applied to the [[concepts/semialgebraic|semialgebraic]] structure $\mathcal{R}_{\mathrm{alg}}$ this gives $\mathrm{Pfaff}(\mathcal{R}_{\mathrm{alg}}) =: \mathcal{R}_{\mathrm{Pfaff}}$, the practical "home structure" for deep learning in NNO.

## The examples that matter

Most missing activations are Pfaffian via very short chains:

- **$\exp$** — chain of length $1$: $\exp' = \exp$, i.e. $P(x, f_1) = f_1$. Hence $\mathcal{R}_{\exp} \subseteq \mathcal{R}_{\mathrm{Pfaff}}$.
- **$\arctan$** — length $1$: $\arctan'(x) = \dfrac{1}{1 + x^2}$, already a rational/polynomial datum (write $f_1 = \arctan$ with $f_1' = (1+x^2)^{-1}$, a Pfaffian datum on the chain $g = (1+x^2)^{-1}$).
- **$\mathrm{erf}$, GELU** — length $2$: take $f_1 = e^{-x^2}$ with $f_1' = -2x\, f_1$ (polynomial in $x, f_1$), then $f_2 = \mathrm{erf}$ with $f_2' = \tfrac{2}{\sqrt\pi} f_1$. GELU is then polynomial in $x$ and $\mathrm{erf}$.

These are exactly the activations that land in $\mathcal{R}_{\mathrm{Pfaff}}$ but **not** in $\mathcal{R}_{\mathrm{an,exp}}$ — the antiderivative-of-a-Gaussian functions.

## What is *not* Pfaffian

The boundary is sharp and useful:

- **The Gamma function $\Gamma$** is the standard witness that $\mathcal{R}_{\mathrm{Pfaff}}$ is not everything: $\Gamma$ is definable in $\mathcal{R}_{G,\exp}$ but **not** in $\mathcal{R}_{\mathrm{Pfaff}}$. Its functional equation $\Gamma(x+1) = x\,\Gamma(x)$ is not a polynomial ODE system, and no finite Pfaffian chain produces it.
- **$\sin$ on all of $\mathbb{R}$** is excluded for the o-minimal reason: although $\sin$ satisfies $\sin' = \cos,\ \cos' = -\sin$ (a triangular system), it has infinitely many zeros, violating Khovanskii finiteness — Pfaffian chains are required on domains where the finiteness bound holds, so the *global* sine is outside the theory while $\sin\!\mid_{[0,2\pi]}$ is fine.

## See also

- [[concepts/universe-of-structures]] — where $\mathrm{Pfaff}(\mathcal{R}_{\mathrm{alg}})$ and $\mathrm{Pfaff}(\mathcal{R}_{\mathrm{an}})$ sit
- [[concepts/o-minimal-structures]]
- [[concepts/semialgebraic]]
- [[concepts/definable-functions]]
- [[concepts/real-analytic]]
