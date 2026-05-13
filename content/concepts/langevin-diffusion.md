---
title: Langevin diffusion
---

The SDE
$$dX_t = -\nabla f(X_t)\, dt + \sqrt{2/\beta}\, dW_t$$
with invariant measure $\propto e^{-\beta f}$. Discretizations (ULA, SGLD) inject noise into gradient descent, helping escape saddle points and concentrate around minima of $f$.

For non-smooth $f$, $\nabla f$ is replaced by a [[concepts/subgradients|subgradient]] or [[concepts/conservative-fields|conservative-field]] element.

## See also

- [[concepts/stochastic-subgradient]]
