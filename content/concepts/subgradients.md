---
title: Subgradients & subdifferentials
---

For $f: \mathbb{R}^n \to \mathbb{R} \cup \{+\infty\}$ at $x$ where $f(x)$ is finite:

- **Fréchet (regular) subdifferential** $\hat{\partial} f(x)$: vectors $v$ with $f(y) \ge f(x) + \langle v, y - x\rangle + o(\|y - x\|)$.
- **Limiting subdifferential** $\partial f(x)$: limits of $v_k \in \hat\partial f(x_k)$ with $x_k \to x$, $f(x_k) \to f(x)$.
- **[[concepts/clarke-subdifferential|Clarke subdifferential]]** $\partial^\circ f(x)$: convex hull of the limiting subdifferential (for locally Lipschitz $f$).

## See also

- [[concepts/clarke-subdifferential]]
- [[concepts/conservative-fields]]
- [[concepts/semismooth]]
