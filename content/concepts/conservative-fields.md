---
title: Conservative fields
---

A **conservative field** for $f$ is a set-valued map $D: \mathbb{R}^n \rightrightarrows \mathbb{R}^n$ such that for any absolutely continuous curve $\gamma$,
$$(f \circ \gamma)'(t) = \langle v, \dot\gamma(t)\rangle \quad \forall v \in D(\gamma(t)) \text{ for a.e. } t.$$

Conservative fields are the right abstraction for what **autodiff** computes: backpropagation on a definable network yields a conservative field for the loss, which need not coincide with the [[concepts/clarke-subdifferential|Clarke subdifferential]] but suffices for convergence guarantees.

## See also

- [[concepts/automated-differentiation]]
- [[concepts/clarke-subdifferential]]
