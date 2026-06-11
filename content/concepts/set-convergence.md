---
title: Set convergence — outer, inner & Painlevé–Kuratowski limits
---

For a **set-valued map** $C : (0, \infty) \rightrightarrows \mathbb{R}^n$ (each $t$ assigns a set $C_t \subseteq \mathbb{R}^n$), there are two natural notions of "limit" as $t \downarrow 0$, differing only in a quantifier. They are the foundation of variational analysis — [[concepts/subgradients|subdifferentials]], tangent cones (HW2 Ex 0.8), and [[concepts/conservative-fields|conservative fields]] are all defined as set limits. (HW2, stated; Rockafellar–Wets Ch. 4.)

## Outer limit

$$
\limsup_{t \downarrow 0} C_t := \Big\{ x \in \mathbb{R}^n : \text{for every neighbourhood } U \text{ of } x \text{ and every } t' > 0, \ \exists\, 0 < t'' < t' \text{ with } C_{t''} \cap U \ne \emptyset \Big\}.
$$

A point $x$ is in the outer limit iff $C_t$ gets near $x$ **arbitrarily late** — for every $t'$ there is a smaller $t''$ whose set meets every neighbourhood of $x$. These are the points approached *along some sequence* $t_k \downarrow 0$.

**Example.** Take $C_t = \{0,\ \sin(1/t)\} \subset \mathbb{R}$. As $t \downarrow 0$ the point $\sin(1/t)$ oscillates ever faster, hitting every value of $[-1,1]$ along some sequence $t_k \downarrow 0$. So the outer limit captures the whole range of the oscillation:

$$
\limsup_{t\downarrow 0} \{0,\ \sin(1/t)\} = [-1,1].
$$

## Inner limit

$$
\liminf_{t \downarrow 0} C_t := \Big\{ x \in \mathbb{R}^n : \text{for every neighbourhood } U \text{ of } x, \ \exists\, t' > 0 \text{ with } C_{t''} \cap U \ne \emptyset \text{ for all } 0 < t'' < t' \Big\}.
$$

A point $x$ is in the inner limit iff $C_t$ gets near $x$ **eventually and stays** — there is a threshold $t'$ below which *every* $C_{t''}$ meets every neighbourhood of $x$. These are the points approached *along every sequence* $t_k \downarrow 0$.

**Example.** For the same map $C_t = \{0,\ \sin(1/t)\}$, only $0$ survives: it lies in every $C_t$, so it is approached (trivially) along every sequence. Any other $x \in [-1,1]$ fails — along $t_k = 1/(k\pi)$ we have $\sin(1/t_k) = 0$, so $C_{t_k} = \{0\}$ offers nothing near $x$. Hence

$$
\liminf_{t\downarrow 0} \{0,\ \sin(1/t)\} = \{0\}.
$$

Here the two limits disagree, $\{0\} \subsetneq [-1,1]$, so no Painlevé–Kuratowski limit exists — exactly the intermittent-approach situation the figure below depicts.

## The quantifier difference

The only change is the order of $\forall t'' / \exists t'$:

- **Outer** ("$\limsup$"): for all $t'$, *there exists* a smaller $t''$ that hits $U$ — $C_t$ is near $x$ **frequently** (cofinally often).
- **Inner** ("$\liminf$"): *there exists* $t'$ such that all smaller $t''$ hit $U$ — $C_t$ is near $x$ **eventually** (for all small $t$).

Equivalently, in sequential form (Rockafellar–Wets 4.1):

$$
\limsup_{t\downarrow 0} C_t = \{\, x : \exists\, t_k \downarrow 0,\ x_k \in C_{t_k},\ x_k \to x \,\}, \qquad
\liminf_{t\downarrow 0} C_t = \{\, x : \forall\, t_k \downarrow 0,\ \exists\, x_k \in C_{t_k},\ x_k \to x \,\}.
$$

Both limits are **closed** sets, and always

$$
\liminf_{t \downarrow 0} C_t \ \subseteq \ \limsup_{t \downarrow 0} C_t .
$$

## Painlevé–Kuratowski limit

When the two agree, their common value is the **Painlevé–Kuratowski limit**:

$$
\lim_{t \downarrow 0} C_t := \limsup_{t \downarrow 0} C_t = \liminf_{t \downarrow 0} C_t .
$$

This is the "right" notion of convergence for sets, and the one under which set-valued maps behave well. The inclusion above is strict exactly when $C_t$ approaches some points only intermittently.

<svg viewBox="0 0 560 320" xmlns="http://www.w3.org/2000/svg" style="max-width:560px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .axis5 { stroke: currentColor; stroke-opacity: 0.45; stroke-width: 1.2; fill: none; }
      .inner5{ stroke: #10b981; stroke-width: 1.6; fill: none; stroke-dasharray: 6,4; }
      .outer5{ stroke: #ef4444; stroke-width: 1.6; fill: none; stroke-dasharray: 6,4; }
      .dotI  { fill: #10b981; }
      .dotO  { fill: #ef4444; }
      .lbl5  { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 12px; opacity: 0.85; }
      .leg5  { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.8; }
      .ital  { font-style: italic; }
    </style>
    <marker id="t0" viewBox="0 0 10 10" refX="1" refY="5" markerWidth="7" markerHeight="7" orient="auto">
      <path d="M10,0 L0,5 L10,10 z" fill="currentColor" fill-opacity="0.5"/>
    </marker>
  </defs>
  <!-- value axis (vertical) and t axis (horizontal, t=0 at left) -->
  <line x1="80" y1="40" x2="80" y2="250" class="axis5"/>
  <line x1="80" y1="250" x2="525" y2="250" class="axis5" marker-start="url(#t0)"/>
  <text x="528" y="254" class="lbl5 ital">t</text>
  <text x="60" y="46" class="lbl5 ital" text-anchor="end">ℝⁿ</text>
  <text x="92" y="268" class="leg5">t → 0</text>
  <!-- inner-limit branch: value a, present at EVERY t column -->
  <line x1="80" y1="120" x2="520" y2="120" class="inner5"/>
  <text x="528" y="124" class="lbl5 ital">a</text>
  <circle cx="120" cy="121" r="4" class="dotI"/>
  <circle cx="165" cy="118" r="4" class="dotI"/>
  <circle cx="220" cy="123" r="4" class="dotI"/>
  <circle cx="285" cy="117" r="4" class="dotI"/>
  <circle cx="360" cy="122" r="4" class="dotI"/>
  <circle cx="445" cy="118" r="4" class="dotI"/>
  <!-- outer-only branch: value b, present only at ALTERNATING columns -->
  <line x1="80" y1="195" x2="520" y2="195" class="outer5"/>
  <text x="528" y="199" class="lbl5 ital">b</text>
  <circle cx="120" cy="196" r="4" class="dotO"/>
  <circle cx="220" cy="193" r="4" class="dotO"/>
  <circle cx="360" cy="197" r="4" class="dotO"/>
  <!-- legend -->
  <g transform="translate(80, 292)">
    <circle cx="6" cy="0" r="4" class="dotI"/>
    <text x="16" y="4" class="leg5">a: hit for all small t → inner & outer limit</text>
    <circle cx="296" cy="0" r="4" class="dotO"/>
    <text x="306" y="4" class="leg5">b: hit only intermittently → outer only</text>
  </g>
</svg>

Reading the picture: as $t \downarrow 0$ (moving **left** toward the value axis), the value $a$ (**green**) lies in some $C_t$ for *every* small $t$, so $a \in \liminf$ (hence also in $\limsup$). The value $b$ (**red**) appears only along a subsequence of $t$'s, so $b \in \limsup$ but $b \notin \liminf$. Here the limits disagree, so no Painlevé–Kuratowski limit exists; collapsing the red points to "every small $t$" is exactly what the o-minimal hypothesis buys in HW2 Ex 0.7.

## See also

- [[concepts/subgradients]]
- [[concepts/conservative-fields]]
- [[concepts/c1-manifolds]]
- [[concepts/dimension-theorem]]
