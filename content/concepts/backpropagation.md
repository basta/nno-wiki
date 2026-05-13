---
title: Backpropagation
---

Reverse-mode [[concepts/automated-differentiation|automated differentiation]] applied to the loss of a neural network. Composes elementary "vector–Jacobian products" backward through the computation graph.

For [[concepts/definable-functions|definable]] activations, backpropagation produces an element of a [[concepts/conservative-fields|conservative field]] for the loss — even at non-differentiable points where the chain rule for the [[concepts/clarke-subdifferential|Clarke subdifferential]] would fail.

## See also

- [[concepts/automated-differentiation]]
- [[concepts/conservative-fields]]
