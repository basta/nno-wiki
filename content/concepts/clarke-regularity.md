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

The [[concepts/clarke-subdifferential|Clarke subdifferential]] is always the convex hull of the limiting (Bouligand) subdifferential, $\partial^\circ f(x) = \operatorname{conv}\,\partial_B f(x)$. Then

$$
f \text{ regular at } x \iff \partial_B f(x) \text{ is already convex, i.e. } \partial_B f(x) = \partial^\circ f(x),
$$

and moreover $f^{\circ}(x;d) = \max_{v \in \partial^\circ f(x)} \langle v, d\rangle$ is the genuine directional derivative in every direction. Regularity means **the convex hull threw nothing away** — no asymptotic gradient information was lost in passing from $\partial_B$ to $\partial^\circ$.

## The canonical non-regular example: $-|x|$

This is example 6 on the [[concepts/clarke-subdifferential|Clarke subdifferential]] page. At $x = 0$:

- $\partial_B(-|x|)(0) = \{-1, +1\}$ — two isolated points;
- $\partial^\circ(-|x|)(0) = \operatorname{conv}\{-1,+1\} = [-1, +1]$.

These differ, so $-|x|$ is **not** regular at $0$. Concretely $f'(0; 1) = -1$ (the true downhill slope to the right), but $f^{\circ}(0;1) = +1$ (the $\limsup$ finds nearby base-points where moving right *increases* $f$). The two disagree, and $\partial^\circ$ reports the whole interval $[-1,+1]$ — "loose."

By contrast $+|x|$ **is** regular at $0$: it is convex, $\partial_B = \partial^\circ = [-1,+1]$, and $f^\circ(0;d) = |d| = f'(0;d)$.

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
