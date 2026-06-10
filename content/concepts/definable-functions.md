---
title: Definable functions
---

A function $f: A \to \mathbb{R}^m$ is **definable** in $\mathcal{R}$ if its graph is a [[concepts/definable-sets|definable subset]] of $\mathbb{R}^{n+m}$.

In [[concepts/o-minimal-structures|o-minimal structures]], definable functions are extremely well-behaved: they are piecewise $C^r$, satisfy [[concepts/curve-selection|curve selection]], admit [[concepts/cell-decomposition|cell decompositions]] of their domain, and (for compositions) inherit definability.

## Operations preserving definability

- Composition, sum, product.
- Inverses (on the domain where they exist).
- Sup/inf over a definable family.
- Sard's theorem applies in definable form.

## Strategies for proving definability

Since "$f$ definable" *means* "graph of $f$ is a [[concepts/definable-sets|definable set]]", every question about a definable function is secretly a question about a definable set. In practice you rarely reason about the graph directly — you use one of:

1. **Graph by formula.** Write $\{(x,y) : y = f(x)\}$ as a first-order formula. The model example is ReLU: $\{(x,y) : (x \le 0 \wedge y = 0) \vee (x \ge 0 \wedge y = x)\}$.
2. **Closure under operations (the practical default).** Composition, sum, product, quotient, inverse (where defined), and sup/inf over a definable family all preserve definability. So once a few primitives are known definable, everything built from them is too — e.g. softplus $\log(1 + e^x)$ is definable in $\mathcal{R}_{\exp}$ because $\exp$, $+$, $\log$ (an inverse), and composition all are.
3. **Piecewise definition.** A function defined piecewise on definable pieces, with each piece definable, is definable: its graph is the finite union of the pieces' graphs. This is how activations with kinks are handled.
   *Example:* absolute value, with graph $\{(x,y) : (x \ge 0 \wedge y = x) \vee (x < 0 \wedge y = -x)\}$ — a union of two definable half-graphs.
4. **Implicit / sup-inf characterization.** When there is no closed form, $f(x) = \sup\{t : \psi(x,t)\}$ is definable whenever $\psi$ is — useful when you only have a characterizing property.
   *Example:* square root on $[0,\infty)$ as $\sqrt{x} = \sup\{t \ge 0 : t^2 \le x\}$ — a sup over the definable family $\{(x,t) : t \ge 0 \wedge t^2 \le x\}$, so $\sqrt{\cdot}$ is definable in $\mathcal{R}_{\mathrm{alg}}$.

For the dual problem (showing a function is **not** definable) you appeal to an invariant of definable sets that its graph violates — e.g. the graph of $\exp$ or $\sin$ is non-definable in $\mathcal{R}_{\mathrm{alg}}$ because semialgebraic asymptotics cannot match their growth/oscillation. See the asymmetry discussion in [[concepts/definable-sets]].

## See also

- [[concepts/definable-sets]]
- [[concepts/structures]]
- [[concepts/tame-geometry]]
