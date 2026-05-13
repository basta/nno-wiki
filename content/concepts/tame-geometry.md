---
title: Tame geometry
---

The umbrella term for the geometry of [[concepts/definable-functions|definable]] sets and functions in [[concepts/o-minimal-structures|o-minimal structures]]. Tame geometry rules out pathological phenomena (Cantor sets, oscillation à la $\sin(1/x)$) while remaining rich enough to cover all common deep-learning objects.

## Why it matters for deep learning

- All standard activations are definable in some o-minimal structure.
- Compositions, products, and integrals stay tame ⇒ neural-network loss landscapes are tame.
- Tameness ⇒ chain rule for generalized derivatives, a.e. differentiability, [[concepts/stratifications|stratifications]], no chaotic SGD behavior.

## See also

- [[concepts/o-minimal-structures]]
- [[concepts/kl-inequality]]
- [[references|Ioffe — An invitation to tame optimization]]
