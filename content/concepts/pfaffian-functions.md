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

## A worked example: GELU

It helps to separate the two nested objects in the definition. The **chain** $f_1, \dots, f_r$ is scaffolding — helper functions whose derivatives are polynomial in $x$ and *earlier* chain members. The **Pfaffian function** is the thing you actually want, built as a single polynomial $Q$ on top of that scaffolding. Let us grow GELU.

GELU is $\mathrm{GELU}(x) = x\,\Phi(x)$, where $\Phi$ is the Gaussian CDF and $\Phi(x) = \tfrac12\big(1 + \mathrm{erf}(x/\sqrt2)\big)$. Take $n = 1$, so each $\partial/\partial x_j$ is just $\tfrac{d}{dx}$, and build a chain of length $r = 2$:

$$
f_1(x) = e^{-x^2/2}, \qquad f_2(x) = \mathrm{erf}(x/\sqrt2).
$$

Check each member against the rule $\dfrac{\partial f_i}{\partial x_j} = P_{ij}(x, f_1, \dots, f_i)$.

For $f_1$ (the $i = 1$ row, so $P$ may reference only $f_1$):

$$
f_1'(x) = -x\,e^{-x^2/2} = \underbrace{-x \cdot f_1}_{P_{11}(x,\, f_1)}.
$$

The derivative of $e^{-x^2/2}$ is no simpler than itself — but it **is** a polynomial in $x$ and $f_1$, and that is all the definition demands. We never need a chain member's derivative to be elementary, only polynomial in data we already hold.

For $f_2$ (the $i = 2$ row, so $P$ may reference $f_1$ and $f_2$):

$$
f_2'(x) = \tfrac{d}{dx}\,\mathrm{erf}(x/\sqrt2) = \sqrt{\tfrac{2}{\pi}}\;e^{-x^2/2} = \underbrace{\sqrt{\tfrac{2}{\pi}} \cdot f_1}_{P_{21}(x,\, f_1,\, f_2)}.
$$

This is **triangularity** at work: $f_2'$ reaches *back* to $f_1$, which is allowed because $f_1$ was introduced first. What it may not do is reference a later member. The ordering is essential — note $f_1'$ leans on $f_1$ alone, never on $f_2$ — and if the dependencies pointed forward no valid ordering would exist.

Finally, GELU itself is a Pfaffian *function*: a plain polynomial $Q$ in $x$ and the chain, with no derivatives or integrals left:

$$
\mathrm{GELU}(x) = x\,\Phi(x) = \tfrac{x}{2}\big(1 + f_2\big) = \underbrace{\tfrac{x}{2} + \tfrac{x}{2}\,f_2}_{Q(x,\, f_1,\, f_2)}.
$$

(It uses only $f_2$ directly; $f_1$ existed solely to *grow* $f_2$.) Mapping the definition's symbols to this instance:

| Definition symbol | In this example |
|---|---|
| $n$ (variables) | $1$ |
| $r$ (chain length) | $2$ |
| $f_1, \dots, f_r$ | $e^{-x^2/2},\ \mathrm{erf}(x/\sqrt2)$ |
| $P_{11}(x, f_1)$ | $-x\,f_1$ |
| $P_{21}(x, f_1, f_2)$ | $\sqrt{2/\pi}\,f_1$ |
| $Q(x, f_1, f_2)$ | $\tfrac{x}{2} + \tfrac{x}{2}\,f_2 = \mathrm{GELU}$ |

The Gaussian is rescaled to $e^{-x^2/2}$ (versus the bare $e^{-x^2}$ used below) precisely so that GELU drops out as a clean polynomial in the chain. The one-sentence intuition: a function is Pfaffian when you can reach it by a **finite ladder of antiderivatives**, each rung's derivative being polynomial in $x$ and the rungs beneath it.

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
