---
title: C¹-manifolds and definable homeomorphisms
---

These two definitions sit underneath the dimension statements of HW3/4 (Ex 0.9–0.10): a $C^1$-manifold is the smooth object whose dimension we want to match against the [[concepts/dimension-theorem|o-minimal dimension]], and a definable homeomorphism onto its image is the map that transports definable structure (and dimension) from a domain onto a manifold.

## $C^1$-manifold of dimension $d$

A set $M \subseteq \mathbb{R}^n$ is a **$C^1$-manifold of dimension $d$** if every point has a neighborhood in which $M$ looks like the graph of a continuously differentiable map. Concretely: for each $x \in M$ there is an open $U \ni x$ in $\mathbb{R}^n$ and a $C^1$-diffeomorphism (a chart) $\varphi : U \to V \subseteq \mathbb{R}^n$ with

$$
\varphi(M \cap U) = (\mathbb{R}^d \times \{0\}) \cap V .
$$

Equivalently, $M \cap U$ is the graph of a $C^1$-map from an open subset of a $d$-dimensional coordinate subspace into the complementary $(n-d)$ coordinates.

### The tangent space $T_M(x)$

At a point $x \in M$, the **tangent space** $T_M(x)$ is the set of velocities of $C^1$-curves through $x$ that stay in $M$:

$$
T_M(x) = \{\, \gamma'(0) : \gamma : (-\varepsilon, \varepsilon) \to M \text{ is } C^1,\ \gamma(0) = x \,\}.
$$

<svg viewBox="0 0 640 270" xmlns="http://www.w3.org/2000/svg" style="max-width:640px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .mani { stroke: #3b82f6; stroke-width: 2.5; fill: none; }
      .surf { stroke: #3b82f6; stroke-width: 1.5; fill: #3b82f6; fill-opacity: 0.12; }
      .tan  { stroke: #f59e0b; stroke-width: 2; fill: none; stroke-dasharray: 5,4; }
      .plane{ stroke: #f59e0b; stroke-width: 1.5; fill: #f59e0b; fill-opacity: 0.15; }
      .vec  { stroke: #ef4444; stroke-width: 2.5; fill: none; }
      .pt3  { fill: #ef4444; }
      .lbl3 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 12px; opacity: 0.85; }
      .ttl3 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 13px; }
      .ital { font-style: italic; }
    </style>
    <marker id="vend" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="7" markerHeight="7" orient="auto">
      <path d="M0,0 L10,5 L0,10 z" fill="#ef4444"/>
    </marker>
  </defs>
  <!-- Panel A: d = 1, tangent line -->
  <text x="160" y="26" text-anchor="middle" class="ttl3">d = 1: tangent line</text>
  <path d="M 40,210 Q 160,60 280,210" class="mani"/>
  <text x="266" y="198" class="lbl3 ital">M</text>
  <line x1="32" y1="187" x2="222" y2="92" class="tan"/>
  <text x="226" y="92" class="lbl3">T<tspan baseline-shift="sub" font-size="9">M</tspan>(x)</text>
  <line x1="112" y1="147" x2="197" y2="104" class="vec" marker-end="url(#vend)"/>
  <text x="150" y="98" class="lbl3 ital">γ′(0)</text>
  <circle cx="112" cy="147" r="4.5" class="pt3"/>
  <text x="100" y="165" class="lbl3 ital" text-anchor="end">x</text>
  <!-- Panel B: d = 2, tangent plane -->
  <text x="480" y="26" text-anchor="middle" class="ttl3">d = 2: tangent plane</text>
  <path d="M 360,150 Q 480,118 600,150 Q 560,202 480,207 Q 400,202 360,150 Z" class="surf"/>
  <text x="585" y="186" class="lbl3 ital">M</text>
  <polygon points="400,138 558,123 542,184 384,199" class="plane"/>
  <text x="498" y="138" class="lbl3">T<tspan baseline-shift="sub" font-size="9">M</tspan>(x)</text>
  <line x1="470" y1="162" x2="548" y2="150" class="vec" marker-end="url(#vend)"/>
  <text x="553" y="148" class="lbl3 ital">v₁</text>
  <line x1="470" y1="162" x2="441" y2="197" class="vec" marker-end="url(#vend)"/>
  <text x="426" y="205" class="lbl3 ital">v₂</text>
  <circle cx="470" cy="162" r="4.5" class="pt3"/>
  <text x="458" y="160" class="lbl3 ital" text-anchor="end">x</text>
</svg>

The tangent space $T_M(x)$ (**amber**) is the set of velocities $\gamma'(0)$ (**red**) of $C^1$-curves $\gamma$ running through $x$ inside $M$ (**blue**). It is a $d$-dimensional linear subspace — a line when $d=1$, spanned by two independent velocities $v_1, v_2$ when $d=2$.

For a $C^1$-manifold this is a **linear subspace** of $\mathbb{R}^n$, and its linear dimension is constant on $M$. This gives the clean, chart-free characterization used in Ex 0.9:

$$
M \text{ is a } C^1\text{-manifold of dimension } d
\iff
d = \dim_{\mathbb{R}} T_M(x) \quad \text{for every } x \in M .
$$

So the manifold dimension $d$ is, pointwise, the linear-algebra dimension of the tangent space. The content of Ex 0.9 is that when $M$ is also **definable** in an o-minimal structure $\mathcal{R}$, this $d$ agrees with the o-minimal [[concepts/dimension-theorem|dimension function]] $\mathrm{d}(M)$:

$$
d = \mathrm{d}(M).
$$

(Without o-minimality the two notions can come apart — definable dimension theory is exactly what forces them to coincide.)

## Definable homeomorphism onto its image

Let $F : \mathbb{R}^n \to \mathbb{R}^m$ be a [[concepts/definable-functions|definable function]] and $C \subseteq \mathbb{R}^n$ a definable set. The restriction

$$
F|_{C} : C \to \mathbb{R}^m
$$

is a **definable homeomorphism onto its image** if:

1. $F|_C$ is **injective**, so it is a bijection $C \to F(C)$;
2. $F|_C$ and its inverse $(F|_C)^{-1} : F(C) \to C$ are both **continuous** (i.e. $F|_C$ is a homeomorphism onto $F(C)$ with its subspace topology); and
3. it is **definable** — automatic here, since $F$, $C$, the image $F(C)$, and the graph of the inverse are all definable in $\mathcal{R}$.

The point of definability is that the homeomorphism then preserves all o-minimal invariants: in particular $\mathrm{d}(C) = \mathrm{d}(F(C))$, because definable bijections preserve [[concepts/dimension-theorem|dimension]].

This is the object produced in Ex 0.10: for a definable $F : \mathbb{R}^n \to \mathbb{R}^n$ and any nonempty definable open $C \subseteq \mathbb{R}^n$, there is a nonempty definable open $C' \subseteq C$ on which **either**

$$
F|_{C'} : C' \to \mathbb{R}^n \text{ is a homeomorphism onto its image,}
\qquad \text{or} \qquad
\dim F[C'] < n .
$$

<svg viewBox="0 0 640 360" xmlns="http://www.w3.org/2000/svg" style="max-width:640px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .amb  { stroke: currentColor; stroke-opacity: 0.5; stroke-width: 1.3; fill: none; stroke-dasharray: 5,4; }
      .dom  { stroke: #3b82f6; stroke-width: 1.8; fill: #3b82f6; fill-opacity: 0.16; }
      .img2 { stroke: #10b981; stroke-width: 1.8; fill: #10b981; fill-opacity: 0.16; }
      .img1 { stroke: #10b981; stroke-width: 2.5; fill: none; }
      .arr  { stroke: currentColor; stroke-opacity: 0.7; stroke-width: 1.6; fill: none; }
      .lbl4 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 12px; opacity: 0.85; }
      .cap4 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 12px; opacity: 0.7; }
      .ital { font-style: italic; }
    </style>
    <marker id="aend" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="8" markerHeight="8" orient="auto">
      <path d="M0,0 L10,5 L0,10 z" fill="currentColor" fill-opacity="0.7"/>
    </marker>
  </defs>
  <!-- Row A: homeomorphism onto image -->
  <ellipse cx="108" cy="95" rx="92" ry="58" class="amb"/>
  <text x="185" y="48" class="lbl4 ital">C</text>
  <ellipse cx="92" cy="100" rx="44" ry="31" class="dom"/>
  <text x="92" y="104" text-anchor="middle" class="lbl4 ital">C′</text>
  <line x1="222" y1="95" x2="356" y2="95" class="arr" marker-end="url(#aend)"/>
  <text x="289" y="83" text-anchor="middle" class="lbl4 ital">F|<tspan baseline-shift="sub" font-size="9">C′</tspan></text>
  <path d="M 432,92 Q 452,52 502,68 Q 542,82 530,116 Q 514,142 468,133 Q 424,124 432,92 Z" class="img2"/>
  <text x="480" y="98" text-anchor="middle" class="lbl4 ital">F(C′)</text>
  <text x="615" y="99" text-anchor="end" class="cap4">homeomorphism — dim F[C′] = n</text>
  <!-- Row B: dimension drop -->
  <ellipse cx="92" cy="270" rx="44" ry="31" class="dom"/>
  <text x="92" y="274" text-anchor="middle" class="lbl4 ital">C′</text>
  <line x1="222" y1="270" x2="356" y2="270" class="arr" marker-end="url(#aend)"/>
  <text x="289" y="258" text-anchor="middle" class="lbl4 ital">F|<tspan baseline-shift="sub" font-size="9">C′</tspan></text>
  <path d="M 420,300 Q 470,232 525,255 Q 565,272 595,242" class="img1"/>
  <text x="505" y="312" text-anchor="middle" class="lbl4 ital">F[C′]</text>
  <text x="615" y="225" text-anchor="end" class="cap4">collapse — dim F[C′] &lt; n</text>
</svg>

After restricting to a suitable definable open $C' \subseteq C$, the map lands in exactly one of two regimes: it is a homeomorphism onto a full-dimensional image (**top**), or it crushes $C'$ onto a lower-dimensional set (**bottom**, here a curve in the plane). There is no middle case — that is the force of the dichotomy.

The dichotomy is a definable analogue of the constant-rank / generic-rank theorem: shrinking to a definable open piece, $F$ is either a local homeomorphism or drops dimension. [[concepts/cell-decomposition|Cell decomposition]] and the [[concepts/monotonicity-theorem|monotonicity theorem]] are the standard tools for producing the good piece $C'$.

## See also

- [[concepts/dimension-theorem]]
- [[concepts/definable-functions]]
- [[concepts/cell-decomposition]]
- [[concepts/monotonicity-theorem]]
