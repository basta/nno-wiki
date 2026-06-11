---
title: Clarke regularity
---

A locally Lipschitz function $f$ is **(Clarke) regular** — also *subdifferentially regular* — at a point $x$ if its one-sided directional behavior at $x$ is not "loose": the ordinary directional derivative exists in every direction and already captures everything the [[concepts/clarke-subdifferential|Clarke generalized derivative]] sees. It is the condition under which the Clarke **sum and chain rules hold with equality** rather than mere inclusion.

## The definition

Two directional derivatives live side by side at $x$:

- the **ordinary one-sided directional derivative**, which need not exist in general,

$$
f'(x; d) = \lim_{t \downarrow 0} \frac{f(x + td) - f(x)}{t},
$$

- the **Clarke generalized directional derivative**, which always exists (the $\limsup$ is over nearby base-points $y$, not just $x$ — that is what makes it robust),

$$
f^{\circ}(x; d) = \limsup_{\substack{y \to x \\ t \downarrow 0}} \frac{f(y + td) - f(y)}{t}.
$$

Always $f'(x;d) \le f^{\circ}(x;d)$.

> $f$ is **Clarke regular at $x$** if $f'(x;d)$ exists for every direction $d$ **and** equals $f^{\circ}(x;d)$.

Regularity is exactly the case where the looser generalized derivative gains nothing — the function's behavior at $x$ already determines its behavior at nearby base-points.

## Equivalent subdifferential statement

Three subdifferentials are nested at every point of a locally Lipschitz $f$:

$$
\underbrace{\partial_B f(x)}_{\text{gradient limits}} \;\subseteq\; \underbrace{\partial_L f(x)}_{\text{limiting (Mordukhovich)}} \;\subseteq\; \underbrace{\partial^\circ f(x)}_{\text{Clarke}} \;=\; \operatorname{conv}\,\partial_B f(x).
$$

- $\partial_B f(x)$ — the **Bouligand** (gradient-limit) subdifferential: limits $\lim_k \nabla f(x_k)$ over differentiability points $x_k \to x$. This is the set *inside* the $\operatorname{conv}\{\dots\}$ of the [[concepts/clarke-subdifferential|Clarke definition]].
- $\partial_L f(x)$ — the **limiting (Mordukhovich)** subdifferential: limits of *regular (Fréchet) subgradients* at nearby points. Unlike $\partial_B$, it can also pick up subgradients **at the kink itself** (supporting slopes), so it is generally strictly larger than $\partial_B$.
- $\partial^\circ f(x)$ — the **Clarke** subdifferential, the convex hull of either.

Regularity is a statement about the **middle** object:

$$
f \text{ regular at } x \iff \partial_L f(x) = \partial^\circ f(x) \iff \partial_L f(x) \text{ is already convex},
$$

with $f^{\circ}(x;d) = \max_{v \in \partial^\circ f(x)} \langle v, d\rangle$ then the genuine directional derivative in every direction. Regularity means **the convex hull threw nothing away** in passing from $\partial_L$ to $\partial^\circ$.

> **Caution.** It is *not* the gradient-limit set $\partial_B$ whose convexity decides regularity. As the contrast below shows, $\partial_B$ is *identical* for $|x|$ and $-|x|$, yet only $|x|$ is regular — the discriminating information lives in $\partial_L$, not $\partial_B$.

## Why $|x|$ is regular but $-|x|$ is not

Both functions have the **same** Bouligand set at $0$: approaching through differentiability points collects the two side-gradients $\pm 1$, so

$$
\partial_B(|x|)(0) = \partial_B(-|x|)(0) = \{-1, +1\}.
$$

Gradient limits alone cannot tell them apart. What differs is the limiting subdifferential $\partial_L$, and the difference is geometric: does the kink admit a **supporting slope** — a line through the kink lying *below* the graph?

- **$|x|$ (a "V", convex).** Every line $y = vx$ with $|v| \le 1$ stays below the V and touches at $0$. These are regular subgradients *at the kink*, so $\partial_L(|x|)(0) = [-1, +1]$ — the whole interval. The interval is **not** built from gradient limits; it comes entirely from supporting slopes. Since $\partial_L = \partial^\circ$, $|x|$ is **regular**.
- **$-|x|$ (a "∧", concave kink).** No line through $0$ stays below the ∧: the graph drops on *both* sides, so a supporting line would need slope $\ge 1$ and $\le -1$ at once — impossible. The kink contributes nothing, and $\partial_L(-|x|)(0) = \{-1, +1\}$ is just the two side-limits. This is not convex, $\partial_L \ne \partial^\circ = [-1,+1]$, so $-|x|$ is **not regular**.

The directional-derivative test agrees: for $-|x|$, $f'(0;1) = -1$ (the true downhill slope to the right) but $f^{\circ}(0;1) = +1$ (the $\limsup$ finds nearby base-points where moving right *increases* $f$); for $|x|$, $f'(0;d) = f^{\circ}(0;d) = |d|$ in every direction. This is example 6 on the [[concepts/clarke-subdifferential|Clarke subdifferential]] page.

| | $\partial_B$ (gradient limits) | supporting slopes at kink | $\partial_L$ (limiting) | regular? |
|---|---|---|---|---|
| $\lvert x\rvert$ | $\{-1,+1\}$ | all of $[-1,+1]$ | $[-1,+1]$ | yes |
| $-\lvert x\rvert$ | $\{-1,+1\}$ | none | $\{-1,+1\}$ | no |

## What is regular

- **$C^1$ functions** — trivially; both directional derivatives equal $\langle \nabla f(x), d\rangle$.
- **Convex functions** — always regular; this is why the Clarke subdifferential coincides with the convex-analytic subdifferential.
- **Max of finitely many $C^1$ functions** — regular. This covers ReLU, hinge loss, and max-pooling, which is why the deep-learning kink functions behave well under the Clarke calculus.
- **Negatives of convex functions, $-\max$ / saddle-type kinks** — typically **not** regular.

Regularity is not preserved under negation: $f$ regular does **not** imply $-f$ regular (the $|x|$ vs $-|x|$ contrast). It is preserved under nonnegative combinations and under composition with $C^1$ maps.

## Why it matters

Regularity is the hypothesis that upgrades the Clarke calculus from inclusions to equalities:

- **Sum rule.** $\partial^\circ(f+g)(x) = \partial^\circ f(x) + \partial^\circ g(x)$ when both summands are regular at $x$ (or one is $C^1$).
- **Chain rule.** The inclusion $\partial^\circ(f \circ g) \subseteq \partial^\circ f \cdot \partial^\circ g$ becomes equality under regularity.

The gap when regularity **fails** is exactly the slack the convex hull introduced — and that slack is the failure mode motivating [[concepts/conservative-fields|conservative fields]] for autodiff: backprop on a non-regular composition can return an element of $\partial^\circ$ that is not a true (sub)gradient, yet is still a valid element of a conservative field.

## See also

- [[concepts/clarke-subdifferential]]
- [[concepts/subgradients]]
- [[concepts/conservative-fields]]
- [[concepts/partly-smooth]]
