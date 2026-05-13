---
title: Stochastic subgradient method
---

$$x_{k+1} = x_k - \alpha_k v_k, \quad v_k \in \partial f(x_k, \xi_k)$$

with $\{\xi_k\}$ a stochastic sample stream and step sizes $\alpha_k \to 0$, $\sum \alpha_k = \infty$.

**Davis–Drusvyatskiy–Kakade–Lee (2020):** for a Lipschitz, [[concepts/definable-functions|definable]] objective, stochastic subgradient with diminishing step sizes converges a.s. to the set of Clarke-stationary points.

## See also

- [[concepts/clarke-subdifferential]]
- [[concepts/conservative-fields]]
- [[references|Davis et al. — Stochastic subgradient method converges on tame functions]]
