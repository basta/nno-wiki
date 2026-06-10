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

## Strategies for proving definability

To show a set **is** definable, you either build a formula or build the set from pieces already known to be definable. Four concrete routes:

1. **Exhibit a first-order formula.** Write $A = \{x : \varphi(x)\}$ using only the basic predicates/functions of $\mathcal{R}$, the connectives $\wedge, \vee, \neg$, and quantifiers $\exists, \forall$ over $\mathbb{R}$. The discipline that makes this rigorous is **fixed, finite quantifier depth**: $\varphi$ must be a single finite formula. This is exactly what rules out cheats like "$\exists n \in \mathbb{N}$" over an external $\mathbb{N}$, or an infinite union $\bigcup_n A_n$ — neither is first-order over $\mathbb{R}$ (the obstruction in the [[concepts/binary-relations|transitive closure]] exercise).
   *Example:* $[0, \infty) = \{x : \exists y\ (y \cdot y = x)\}$ — "$x$ has a real square root" — using only $\cdot, =, \exists$.
2. **Closure under (S1)–(S4).** Write $A$ as a finite combination of known-definable sets: Boolean ops (S1), product $A \times B$ (S2), projection / "$\exists y$" (S3), coordinate equality $x_i = x_j$ (S4). [[concepts/structures|Projection]] is the powerful-and-dangerous one — it is the set-side of $\exists$, so most "there exists a witness" statements are projections in disguise.
   *Example:* the closed annulus $\{1 \le x^2 + y^2 \le 4\}$ is the closed disk of radius $2$ minus the open disk of radius $1$ — an intersection-with-complement (S1) of two sets already known definable. The unit square $[0,1] \times [0,1]$ is a product (S2) of two definable intervals.
3. **Reduce to a known definable class.** In $\mathcal{R}_{\mathrm{alg}}$, every [[concepts/semialgebraic|semialgebraic set]] is definable by definition, so it suffices to write $A$ as a finite Boolean combination of polynomial sign conditions $\{p > 0\}, \{p = 0\}$. In larger structures, cite the generators ($\exp$, restricted analytic functions, …).
   *Example:* the region above the parabola, $\{(x, y) : y \ge x^2\}$, is the single sign condition $\{y - x^2 \ge 0\}$ — manifestly semialgebraic, hence definable, with no formula-wrangling needed.
4. **Image / preimage under a definable map.** If $f$ and $A$ are definable, so are $f(A)$ and $f^{-1}(A)$ — preimage is substitution into a formula, image is a projection of the graph. Often the cleanest route.
   *Example:* for the definable $f(x) = x^2 - 1$, the set $\{x : x^2 - 1 > 0\}$ is just the preimage $f^{-1}\big((0, \infty)\big)$; and the projection of the unit disk onto the $x$-axis (an image under the coordinate map) is $[-1, 1]$.

The asymmetry is worth internalizing: **to show definable, *construct*** (one witness — a formula or a build-up — suffices); **to show non-definable, argue about *all* would-be formulas at once** via a structural invariant they must all satisfy (o-minimal finiteness, finite VC dimension, cell decomposition, dimension bounds) and show $A$ violates it. E.g. $\mathbb{Z}$ is infinite and discrete, so not a finite union of points and intervals, hence not definable in any o-minimal structure.

## Definable functions

A function $f : A \to \mathbb{R}^m$ is **definable** iff its graph is a definable subset of $\mathbb{R}^{n+m}$. See [[concepts/definable-functions]] for properties.

## See also

- [[concepts/structures]]
- [[concepts/definable-functions]]
- [[concepts/o-minimal-structures]]
- [[concepts/semialgebraic]]
