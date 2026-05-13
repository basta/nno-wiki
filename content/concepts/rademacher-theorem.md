---
title: Rademacher's theorem
---

**Theorem (Rademacher, 1919).** Let $f: U \to \mathbb{R}^m$ be a locally Lipschitz function on an open set $U \subseteq \mathbb{R}^n$. Then $f$ is **differentiable almost everywhere** in $U$ with respect to Lebesgue measure.

That is, the set $\{x \in U : Df(x) \text{ does not exist}\}$ has Lebesgue measure zero.

## Why it matters for NNO

Rademacher is what makes the [[concepts/clarke-subdifferential|Clarke subdifferential]] well-defined: for a locally Lipschitz $f$,
$$\partial^\circ f(x) = \operatorname{conv}\Big\{ \lim_{k \to \infty} \nabla f(x_k) : x_k \to x,\ f\ \text{differentiable at } x_k \Big\}$$
only makes sense because Rademacher guarantees a *dense* set of differentiability points near $x$.

In the tame setting it gets sharpened: for [[concepts/definable-functions|definable]] locally Lipschitz functions, the non-differentiability set is not merely measure zero — it is a [[concepts/definable-sets|**definable set** of dimension $< n$]], contained in a finite union of lower-dimensional [[concepts/cells|cells]]. This is why [[concepts/automated-differentiation|autodiff]] hits a non-smooth point with probability zero in generic settings.

## Intuition

A Lipschitz function cannot oscillate too wildly: its difference quotients are bounded. "Bounded slope" + Lebesgue differentiation ⇒ derivative exists except on a thin (measure-zero) bad set — corners, kinks, ridges.

## Caveats

- "A.e. differentiable" is weaker than "differentiable on a dense open set" — it gives no topological control of the bad set.
- The theorem fails without Lipschitz: continuous functions can be nowhere differentiable (Weierstrass).
- The bad set can still be uncountable and dense (think fractal kinks).

## References

- Federer, *Geometric Measure Theory*, §3.1.6.
- Rademacher, H. (1919), original German paper.

## See also

- [[concepts/clarke-subdifferential]]
- [[concepts/subgradients]]
- [[concepts/definable-functions]]
