---
title: Definable sets
---

A **definable set** is a subset of $\mathbb{R}^n$ that belongs to your chosen [[concepts/structures|structure]] $\mathcal{R}$ — equivalently, one that can be cut out by a first-order formula in the language of $\mathcal{R}$.

"Definable" is **always relative to a structure**. Saying "$A$ is definable" with no $\mathcal{R}$ specified is meaningless: $\mathbb{Z}$ is not definable in $\mathcal{R}_{\mathrm{alg}}$ but is trivially definable in $(\mathcal{R}_{\mathrm{alg}}, \mathbb{Z})$, the structure you get by adding $\mathbb{Z}$ as a basic set.

## Two equivalent views

**Set-theoretic view (membership).** Fix a structure $\mathcal{R} = (\mathcal{R}_n)_n$. A set $A \subseteq \mathbb{R}^n$ is definable iff $A \in \mathcal{R}_n$. The axioms [[concepts/structures|(S1)–(S4)]] specify which collections of sets can serve as $\mathcal{R}_n$, and any specific $\mathcal{R}$ then declares which subsets are "allowed in."

**Logical view (formula).** $A$ is definable iff there is a first-order formula $\varphi(x_1, \dots, x_n)$ in the language of $\mathcal{R}$ such that

$$
A = \{(x_1, \dots, x_n) \in \mathbb{R}^n : \varphi(x_1, \dots, x_n) \text{ holds}\}.
$$

The available logical operations are $=$, the basic predicates and functions of $\mathcal{R}$, the Boolean connectives $\wedge, \vee, \neg$, and the quantifiers $\exists, \forall$ ranging over $\mathbb{R}$.

The two views are equivalent — that is the content of Informal Thm. 7.32 in [[concepts/structures]].

## Examples in $\mathcal{R}_{\mathrm{alg}}$

Definable:

- $\{x \in \mathbb{R} : x^2 - 1 > 0\} = (-\infty, -1) \cup (1, \infty)$.
- The unit circle $\{(x, y) : x^2 + y^2 = 1\}$.
- The graph of ReLU, $\{(x, y) : (x \le 0 \wedge y = 0) \vee (x \ge 0 \wedge y = x)\}$.
- Any [[concepts/semialgebraic|semialgebraic set]] — that's literally what $\mathcal{R}_{\mathrm{alg}}$-definable means.

Not definable:

- $\mathbb{Z} \subseteq \mathbb{R}$ — an infinite discrete subset of $\mathbb{R}$, but [[concepts/semialgebraic|semialgebraic subsets of $\mathbb{R}$]] are finite unions of points and intervals.
- The graph of $\exp$ — its asymptotic growth defeats any polynomial bound (see [[concepts/real-analytic|the identity theorem argument]] and the semialgebraic asymptotics lemma).
- $\{(x, y) : y = \sin(x)\}$ — same reason.

## Why two views?

Each gives a different proof strategy.

- **To show definable**: easiest via the formula view — write a formula, done.
- **To show non-definable**: easiest via the set-theoretic view — appeal to a structural property *all* definable sets must satisfy (finiteness, dimension, cell decomposition, …) and exhibit your candidate set as violating it.

This duality powers most arguments in tame geometry, including exercise 0.5 on the [[concepts/binary-relations|transitive closure]].

## Definable functions

A function $f : A \to \mathbb{R}^m$ is **definable** iff its graph is a definable subset of $\mathbb{R}^{n+m}$. See [[concepts/definable-functions]] for properties.

## See also

- [[concepts/structures]]
- [[concepts/definable-functions]]
- [[concepts/o-minimal-structures]]
- [[concepts/semialgebraic]]
