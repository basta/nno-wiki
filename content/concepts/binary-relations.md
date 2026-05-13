---
title: Binary relations, composition, and transitive closure
---

A **binary relation** on $\mathbb{R}$ (or any set) is a subset $A \subseteq \mathbb{R}^2$. We write $x A y$ to mean $(x, y) \in A$.

## Symmetry and reflexivity

Let $\Delta_{\mathbb{R}} = \{(x, x) : x \in \mathbb{R}\} \subseteq \mathbb{R}^2$ be the diagonal.

- **Reflexive.** $A$ is reflexive iff $\Delta_{\mathbb{R}} \subseteq A$, i.e. $xAx$ for every $x$.
- **Symmetric.** $A$ is symmetric iff $A = A^{-1}$, where $A^{-1} = \{(y, x) : (x, y) \in A\}$.
- **Transitive.** $A$ is transitive iff $A \circ A \subseteq A$.

Both reflexivity and symmetry are mild: they each cost one [[concepts/structures|definable]] condition. The interesting question is whether they help *force* additional structure (in particular, transitive closure being definable).

## Composition

The **composition** of $A, B \subseteq \mathbb{R}^2$ is

$$
A \circ B = \{(x, z) : \exists y\ (x, y) \in A \text{ and } (y, z) \in B\} \subseteq \mathbb{R}^2.
$$

In any [[concepts/structures|structure]] $\mathcal{R}$, the composition of two definable relations is definable: write $A \circ B$ as the projection of

$$
\{(x, y, z) : (x, y) \in A,\ (y, z) \in B\} = (A \times \mathbb{R}) \cap (\mathbb{R} \times B)
$$

onto the $(x, z)$ coordinates. The intersection is definable by (S1)+(S2), the projection by (S3) (this is essentially Lemma 7.24 / Cor. 7.27).

Iterated compositions are denoted

$$
A^{\circ n} = \underbrace{A \circ A \circ \cdots \circ A}_{n \text{ times}}, \qquad n \ge 1.
$$

Each $A^{\circ n}$ is definable when $A$ is, by induction.

## Transitive closure

The **transitive closure** of $A \subseteq \mathbb{R}^2$ is, equivalently,

1. The smallest transitive relation containing $A$.
2. The union $\displaystyle A^{\mathrm{tr}} = \bigcup_{n \ge 1} A^{\circ n}$.
3. The set of pairs $(x, y)$ such that there exists a finite chain $x = x_0, x_1, \dots, x_n = y$ with each $(x_{i-1}, x_i) \in A$.

The phrase **"some finite chain"** hides an existential quantifier over $\mathbb{N}$ — and that is precisely the source of trouble for definability.

## Warning: infinite unions are not definable in general

Each $A^{\circ n}$ is definable, but the [[concepts/structures|axioms (S1)–(S4)]] only guarantee closure under *finite* Boolean operations, not arbitrary countable unions. The canonical cautionary example (in the spirit of Lemma 7.24's warning):

> In $\mathcal{R}_{\mathrm{alg}}$, every singleton $\{k\}$ for $k \in \mathbb{Z}$ is definable (it's a zero of a polynomial), yet
> $$\mathbb{Z} = \bigcup_{k \in \mathbb{Z}} \{k\}$$
> is **not** definable — $\mathbb{Z}$ is an infinite discrete subset of $\mathbb{R}$, but [[concepts/semialgebraic|semialgebraic subsets of $\mathbb{R}$]] are finite unions of points and intervals, so an infinite discrete set cannot occur.

So an infinite union of [[concepts/definable-sets|definable sets]] is in general not definable. For $A^{\mathrm{tr}} = \bigcup_n A^{\circ n}$ to be definable, the union must be **uniformly** expressible by some single first-order formula — and "$\exists n \in \mathbb{N}$" is *not* a first-order quantifier over $\mathbb{R}$.

## Strategy for definability questions about $A^{\mathrm{tr}}$

- **To show $A^{\mathrm{tr}}$ is definable** in a specific $\mathcal{R}$: find a *uniform* first-order formula — usually one that bypasses the union, e.g. by appealing to a closed-form structural description of $A^{\mathrm{tr}}$ that doesn't mention $n$.
- **To show $A^{\mathrm{tr}}$ is not definable**: produce a specific structure $\mathcal{R}$ and a specific definable $A$ such that $A^{\mathrm{tr}}$ would have to be an infinite Boolean object incompatible with the catalogue of $\mathcal{R}$-definable sets — e.g., an infinite discrete subset in a context where definable subsets of $\mathbb{R}$ are finite unions of points and intervals.

## See also

- [[concepts/structures]]
- [[concepts/semialgebraic]]
- [[concepts/o-minimal-structures]]
