---
title: Automated differentiation
---

Algorithmic computation of derivatives by composing elementary derivatives through a program's computation graph.

- **Forward mode**: propagates tangents (efficient for $\mathbb{R}^n \to \mathbb{R}^m$ with $n$ small).
- **Reverse mode** (= [[concepts/backpropagation|backpropagation]]): propagates cotangents (efficient for scalar losses).

For non-smooth definable programs, autodiff returns a value in a [[concepts/conservative-fields|conservative field]], not necessarily the [[concepts/clarke-subdifferential|Clarke subdifferential]]. PyTorch vs. TensorFlow differ in how they pick representatives at non-smooth points.

## See also

- [[concepts/backpropagation]]
- [[concepts/conservative-fields]]
