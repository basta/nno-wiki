---
title: Clarke subdifferential
---

For a locally Lipschitz $f$, by [[concepts/rademacher-theorem|Rademacher's theorem]] $f$ is differentiable a.e. on every neighborhood of $x$. The **Clarke subdifferential** is
$$\partial^\circ f(x) = \operatorname{conv}\Big\{\lim_{k \to \infty} \nabla f(x_k) : x_k \to x,\ f\ \text{differentiable at}\ x_k\Big\}.$$

> **Notation.** $\operatorname{conv}(S)$ denotes the **convex hull** of $S$ — the smallest convex set containing $S$, i.e.
> $$\operatorname{conv}(S) = \Big\{ \textstyle\sum_{i=1}^k \lambda_i s_i : s_i \in S,\ \lambda_i \ge 0,\ \sum_i \lambda_i = 1 \Big\}.$$
> Without it, the set of limiting gradients can be a finite collection of isolated points (e.g. $\{-1, +1\}$ for $|x|$ at $0$), which is too sparse for first-order optimality conditions. Taking the convex hull fills it into $[-1, +1]$, so that $0 \in \partial^\circ |\cdot|(0)$ correctly flags the minimum. Convexity + compactness are also what make the sum/chain rules work as inclusions.

## Reading the definition

The notation $\lim_{k \to \infty} \nabla f(x_k)$ packs three quantifiers together. A vector $g \in \mathbb{R}^n$ belongs to the set inside $\operatorname{conv}\{\dots\}$ iff there **exists some sequence** $(x_k)$ with:

1. $x_k \to x$ — the sequence converges to the point of interest,
2. $f$ is differentiable at every $x_k$ — so $\nabla f(x_k)$ is well-defined (guaranteed to exist by [[concepts/rademacher-theorem|Rademacher's theorem]] on a dense set),
3. $\nabla f(x_k) \to g$ — those gradients themselves converge.

So:

> $\partial^\circ f(x)$ is the **convex hull of all gradient-limits achievable by sneaking up on $x$ through points where the gradient exists.**

Different sequences can yield different limits. For $|x|$ at $0$: approaching from the right gives $+1$; approaching from the left gives $-1$; an oscillating sequence gives no limit (it does not contribute). The achievable limits are $\{-1, +1\}$, and the convex hull is $[-1, +1]$.

**Intuition for tame functions.** For piecewise-smooth or [[concepts/definable-functions|definable]] $f$, "sequence" can be replaced by "approach from a smooth region adjacent to $x$" — one limit per region. Strictly the definition allows arbitrary sequences (along curves, erratic, …), and pathological non-tame examples like $x^2 \sin(1/x)$ near $0$ show that "direction" is too coarse a notion. In the deep-learning setting (ReLU, max-pooling, $\ell_1$, hinge loss, …), the region-by-region picture is exact.

For [[concepts/definable-functions|definable]] locally Lipschitz $f$, $\partial^\circ f$ admits **projection formulas** onto the active stratum of any [[concepts/whitney-stratifications|Whitney stratification]] of the graph.

## Basic properties

- $\partial^\circ f(x)$ is a **nonempty, convex, compact** subset of $\mathbb{R}^n$.
- If $f$ is **$C^1$ at $x$**, then $\partial^\circ f(x) = \{\nabla f(x)\}$.
- If $f$ is **convex**, $\partial^\circ f(x)$ equals the convex-analytic subdifferential.
- **Sum rule (inclusion)**: $\partial^\circ (f + g)(x) \subseteq \partial^\circ f(x) + \partial^\circ g(x)$, with equality if one summand is $C^1$ or both are *regular* at $x$.
- **Chain rule (inclusion)**: $\partial^\circ (f \circ g)(x) \subseteq \partial^\circ f(g(x)) \cdot \partial^\circ g(x)$ — generally not an equality, which is exactly what motivates [[concepts/conservative-fields|conservative fields]] for autodiff.

## Examples

### 1. Absolute value $f(x) = |x|$
$f$ is $C^1$ everywhere except at $0$, where $\nabla f = +1$ on the right and $-1$ on the left.
$$\partial^\circ |x| = \begin{cases} \{+1\} & x > 0 \\ [-1, +1] & x = 0 \\ \{-1\} & x < 0 \end{cases}$$
Note $0 \in \partial^\circ |\cdot|(0)$, so $0$ is **Clarke-stationary** — consistent with it being the minimizer.

<svg viewBox="0 0 640 240" xmlns="http://www.w3.org/2000/svg" style="max-width:100%;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .ax { stroke: currentColor; stroke-opacity: 0.35; stroke-width: 1; fill: none; }
      .fn { stroke: #3b82f6; stroke-width: 2.5; fill: none; stroke-linecap: round; stroke-linejoin: round; }
      .sb { stroke: #ef4444; stroke-width: 2.5; fill: none; stroke-linecap: round; }
      .sbt { stroke: #ef4444; stroke-width: 5; stroke-linecap: round; }
      .dot { fill: #ef4444; }
      .lbl { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.7; }
      .ttl { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 13px; }
    </style>
  </defs>
  <g>
    <text x="160" y="20" text-anchor="middle" class="ttl">f(x) = |x|</text>
    <line x1="40" y1="200" x2="290" y2="200" class="ax"/>
    <line x1="160" y1="25" x2="160" y2="215" class="ax"/>
    <text x="293" y="204" class="lbl">x</text>
    <text x="164" y="33" class="lbl">f</text>
    <polyline points="40,30 160,200 280,30" class="fn"/>
  </g>
  <g>
    <text x="500" y="20" text-anchor="middle" class="ttl">∂°|x|</text>
    <line x1="380" y1="115" x2="630" y2="115" class="ax"/>
    <line x1="500" y1="25" x2="500" y2="215" class="ax"/>
    <text x="633" y="119" class="lbl">x</text>
    <text x="504" y="33" class="lbl">v</text>
    <text x="495" y="62" class="lbl" text-anchor="end">+1</text>
    <text x="495" y="176" class="lbl" text-anchor="end">−1</text>
    <line x1="380" y1="172" x2="500" y2="172" class="sb"/>
    <line x1="500" y1="58" x2="620" y2="58" class="sb"/>
    <line x1="500" y1="58" x2="500" y2="172" class="sbt"/>
    <circle cx="500" cy="58" r="3.5" class="dot"/>
    <circle cx="500" cy="172" r="3.5" class="dot"/>
  </g>
</svg>

### 2. ReLU $\sigma(x) = \max(0, x)$
$$\partial^\circ \sigma(x) = \begin{cases} \{1\} & x > 0 \\ [0, 1] & x = 0 \\ \{0\} & x < 0 \end{cases}$$
PyTorch and TensorFlow each pick a *different* element of $[0,1]$ at $x = 0$ (typically $0$). Both choices give an element of a [[concepts/conservative-fields|conservative field]], even though only one element equals the "true" derivative-by-convention.

<svg viewBox="0 0 640 240" xmlns="http://www.w3.org/2000/svg" style="max-width:100%;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .ax2 { stroke: currentColor; stroke-opacity: 0.35; stroke-width: 1; fill: none; }
      .fn2 { stroke: #3b82f6; stroke-width: 2.5; fill: none; stroke-linecap: round; stroke-linejoin: round; }
      .sb2 { stroke: #ef4444; stroke-width: 2.5; fill: none; stroke-linecap: round; }
      .sbt2 { stroke: #ef4444; stroke-width: 5; stroke-linecap: round; }
      .dot2 { fill: #ef4444; }
      .lbl2 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.7; }
      .ttl2 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 13px; }
    </style>
  </defs>
  <g>
    <text x="160" y="20" text-anchor="middle" class="ttl2">σ(x) = max(0, x)</text>
    <line x1="40" y1="200" x2="290" y2="200" class="ax2"/>
    <line x1="160" y1="25" x2="160" y2="215" class="ax2"/>
    <text x="293" y="204" class="lbl2">x</text>
    <text x="164" y="33" class="lbl2">σ</text>
    <polyline points="40,200 160,200 280,30" class="fn2"/>
  </g>
  <g>
    <text x="500" y="20" text-anchor="middle" class="ttl2">∂°σ(x)</text>
    <line x1="380" y1="200" x2="630" y2="200" class="ax2"/>
    <line x1="500" y1="25" x2="500" y2="215" class="ax2"/>
    <text x="633" y="204" class="lbl2">x</text>
    <text x="504" y="33" class="lbl2">v</text>
    <text x="495" y="62" class="lbl2" text-anchor="end">+1</text>
    <text x="495" y="204" class="lbl2" text-anchor="end">0</text>
    <line x1="380" y1="200" x2="500" y2="200" class="sb2"/>
    <line x1="500" y1="58" x2="620" y2="58" class="sb2"/>
    <line x1="500" y1="58" x2="500" y2="200" class="sbt2"/>
    <circle cx="500" cy="58" r="3.5" class="dot2"/>
    <circle cx="500" cy="200" r="3.5" class="dot2"/>
  </g>
</svg>

### 3. $f(x, y) = \max(x, y)$
On the diagonal $x = y$, both coordinates "win":
$$\partial^\circ f(x, x) = \operatorname{conv}\{(1,0), (0,1)\} = \{(\lambda, 1-\lambda) : \lambda \in [0,1]\}.$$
Off-diagonal it is a singleton $(1,0)$ or $(0,1)$.

### 4. Euclidean norm $f(x) = \|x\|_2$
$$\partial^\circ \|x\|_2 = \begin{cases} \{x / \|x\|_2\} & x \ne 0 \\ \{v : \|v\|_2 \le 1\} & x = 0 \end{cases}$$
At the kink $x = 0$ the Clarke subdifferential is the **entire closed unit ball**.

### 5. $\ell_1$ norm $f(x) = \|x\|_1 = \sum_i |x_i|$
Componentwise:
$$\partial^\circ \|x\|_1 = \{v : v_i = \operatorname{sign}(x_i) \text{ if } x_i \ne 0,\ v_i \in [-1, 1] \text{ if } x_i = 0\}.$$
This is the standard subdifferential underlying soft-thresholding / LASSO updates.

<svg viewBox="0 0 320 320" xmlns="http://www.w3.org/2000/svg" style="max-width:320px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .ax5 { stroke: currentColor; stroke-opacity: 0.35; stroke-width: 1; fill: none; }
      .lv { stroke: #3b82f6; stroke-width: 2; fill: none; stroke-linejoin: round; }
      .lvf { fill: #3b82f6; fill-opacity: 0.08; stroke: none; }
      .kink { stroke: #ef4444; stroke-width: 3; stroke-linecap: round; }
      .dot5 { fill: #ef4444; }
      .lbl5 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.7; }
      .ttl5 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 13px; }
      .leg { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 10px; opacity: 0.85; }
    </style>
  </defs>
  <text x="160" y="18" text-anchor="middle" class="ttl5">Level sets of ‖x‖₁ in ℝ²</text>
  <!-- axes -->
  <line x1="20" y1="160" x2="300" y2="160" class="ax5"/>
  <line x1="160" y1="30" x2="160" y2="290" class="ax5"/>
  <text x="303" y="164" class="lbl5">x₁</text>
  <text x="164" y="38" class="lbl5">x₂</text>
  <!-- level diamonds c = 0.5, 1.0, 1.5 (scale 50px/unit) -->
  <polygon points="210,160 160,110 110,160 160,210" class="lvf"/>
  <polygon points="210,160 160,110 110,160 160,210" class="lv"/>
  <polygon points="185,160 160,135 135,160 160,185" class="lv"/>
  <polygon points="235,160 160,85 85,160 160,235" class="lv"/>
  <text x="213" y="155" class="lbl5">c=1</text>
  <!-- kink set: coordinate axes within plot -->
  <line x1="50" y1="160" x2="270" y2="160" class="kink"/>
  <line x1="160" y1="50" x2="160" y2="270" class="kink"/>
  <circle cx="160" cy="160" r="4" class="dot5"/>
  <!-- legend -->
  <g transform="translate(20, 280)">
    <line x1="0" y1="6" x2="18" y2="6" class="lv"/>
    <text x="24" y="10" class="leg">level set</text>
    <line x1="100" y1="6" x2="118" y2="6" class="kink"/>
    <text x="124" y="10" class="leg">non-differentiability</text>
  </g>
</svg>

*Red lines: the kink set where $\partial^\circ \|x\|_1$ is set-valued (any $x_i = 0$). At the red dot (origin), the subdifferential is the full hypercube $[-1, 1]^2$.*

### 6. A non-regular example: $f(x) = -|x|$
Even though $|x|$ is convex and regular at $0$, its negative is **not** regular:
$$\partial^\circ (-|x|)(0) = [-1, +1]$$
but the limiting subdifferential is only $\{-1, +1\}$ (two points). The Clarke version is the **convex hull**, hiding the actual asymptotic behavior — illustrating why Clarke is "loose" without regularity.

<svg viewBox="0 0 640 240" xmlns="http://www.w3.org/2000/svg" style="max-width:100%;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .ax6 { stroke: currentColor; stroke-opacity: 0.35; stroke-width: 1; fill: none; }
      .fn6 { stroke: #3b82f6; stroke-width: 2.5; fill: none; stroke-linecap: round; stroke-linejoin: round; }
      .sb6 { stroke: #ef4444; stroke-width: 2.5; fill: none; stroke-linecap: round; }
      .clk { stroke: #ef4444; stroke-width: 5; stroke-linecap: round; stroke-opacity: 0.35; }
      .dot6 { fill: #ef4444; }
      .lbl6 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.7; }
      .ttl6 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 13px; }
      .leg6 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 10px; opacity: 0.85; }
    </style>
  </defs>
  <g>
    <text x="160" y="20" text-anchor="middle" class="ttl6">f(x) = −|x|</text>
    <line x1="40" y1="40" x2="290" y2="40" class="ax6"/>
    <line x1="160" y1="30" x2="160" y2="215" class="ax6"/>
    <text x="293" y="44" class="lbl6">x</text>
    <text x="164" y="38" class="lbl6">f</text>
    <polyline points="40,200 160,40 280,200" class="fn6"/>
  </g>
  <g>
    <text x="500" y="20" text-anchor="middle" class="ttl6">∂°(−|x|)  vs  limiting ∂(−|x|)</text>
    <line x1="380" y1="115" x2="630" y2="115" class="ax6"/>
    <line x1="500" y1="30" x2="500" y2="215" class="ax6"/>
    <text x="633" y="119" class="lbl6">x</text>
    <text x="504" y="38" class="lbl6">v</text>
    <text x="495" y="62" class="lbl6" text-anchor="end">+1</text>
    <text x="495" y="176" class="lbl6" text-anchor="end">−1</text>
    <!-- v = +1 for x < 0, v = -1 for x > 0 -->
    <line x1="380" y1="58" x2="500" y2="58" class="sb6"/>
    <line x1="500" y1="172" x2="620" y2="172" class="sb6"/>
    <!-- Clarke at x=0: full [-1, +1] in pale red -->
    <line x1="500" y1="58" x2="500" y2="172" class="clk"/>
    <!-- Limiting at x=0: only two endpoints -->
    <circle cx="500" cy="58" r="4.5" class="dot6"/>
    <circle cx="500" cy="172" r="4.5" class="dot6"/>
    <!-- legend -->
    <g transform="translate(385, 195)">
      <line x1="0" y1="6" x2="18" y2="6" class="clk"/>
      <text x="24" y="10" class="leg6">∂°(−|x|) = [−1, +1]</text>
      <circle cx="135" cy="6" r="3.5" class="dot6"/>
      <text x="143" y="10" class="leg6">limiting ∂ = {−1, +1}</text>
    </g>
  </g>
</svg>

*The Clarke set (pale red bar) is the **convex hull** of the limiting subdifferential (two red dots). For convex/regular functions these coincide; here they don't — exactly the failure mode that motivates [[concepts/conservative-fields|conservative fields]].*

### 7. A ReLU network at a kink
For $f(x) = \sigma(w_2 \sigma(w_1 x))$ with $w_1, w_2 > 0$ at $x = 0$:
applying the chain-rule **inclusion** gives
$$\partial^\circ f(0) \subseteq w_2 \cdot [0, 1] \cdot w_1 \cdot [0, 1] = [0, w_1 w_2],$$
and the actual Clarke set is the same interval $[0, w_1 w_2]$. Backprop picks **one specific element** of this interval depending on tie-breaking conventions.

## See also

- [[concepts/rademacher-theorem]]
- [[concepts/subgradients]]
- [[concepts/conservative-fields]]
