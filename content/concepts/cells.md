---
title: Cells
---

A **cell** in $\mathbb{R}^n$ is built inductively:
- A cell in $\mathbb{R}^1$ is a point or an open interval.
- A cell in $\mathbb{R}^{n+1}$ is either the graph of a definable continuous function on a cell $C \subseteq \mathbb{R}^n$, or a "band" $\{(x, y) : x \in C,\ f(x) < y < g(x)\}$ with $f < g$ definable continuous (allowing $\pm\infty$).

Cells are definably homeomorphic to open boxes; $C^r$-cells additionally satisfy smoothness of the defining functions.

## Cells in $\mathbb{R}^1$

Three points $a < b < c$ partition $\mathbb{R}$ into three 0-cells and four open 1-cells:

<svg viewBox="0 0 540 150" xmlns="http://www.w3.org/2000/svg" style="max-width:540px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .ax { stroke: currentColor; stroke-opacity: 0.4; stroke-width: 1; fill: none; }
      .pt { fill: #ef4444; }
      .iv { stroke: #3b82f6; stroke-width: 2.5; fill: none; stroke-linecap: round; }
      .op { fill: none; stroke: #3b82f6; stroke-width: 2; }
      .lbl { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.8; }
      .leg { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 10px; opacity: 0.85; }
    </style>
    <marker id="lend" viewBox="0 0 10 10" refX="1" refY="5" markerWidth="7" markerHeight="7" orient="auto">
      <path d="M10,0 L0,5 L10,10 z" fill="#3b82f6"/>
    </marker>
    <marker id="rend" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto">
      <path d="M0,0 L10,5 L0,10 z" fill="#3b82f6"/>
    </marker>
  </defs>
  <!-- the real line -->
  <line x1="10" y1="85" x2="525" y2="85" class="ax"/>
  <text x="528" y="89" class="lbl">ℝ</text>
  <!-- 1-cells (open intervals) above the line -->
  <line x1="40" y1="55" x2="118" y2="55" class="iv" marker-start="url(#lend)"/>
  <circle cx="121" cy="55" r="3.5" class="op"/>
  <circle cx="139" cy="55" r="3.5" class="op"/>
  <line x1="142" y1="55" x2="237" y2="55" class="iv"/>
  <circle cx="240" cy="55" r="3.5" class="op"/>
  <circle cx="258" cy="55" r="3.5" class="op"/>
  <line x1="261" y1="55" x2="356" y2="55" class="iv"/>
  <circle cx="359" cy="55" r="3.5" class="op"/>
  <circle cx="377" cy="55" r="3.5" class="op"/>
  <line x1="380" y1="55" x2="500" y2="55" class="iv" marker-end="url(#rend)"/>
  <!-- interval labels -->
  <text x="80" y="44" text-anchor="middle" class="leg">(−∞, a)</text>
  <text x="189" y="44" text-anchor="middle" class="leg">(a, b)</text>
  <text x="308" y="44" text-anchor="middle" class="leg">(b, c)</text>
  <text x="440" y="44" text-anchor="middle" class="leg">(c, +∞)</text>
  <!-- 0-cells on the line -->
  <circle cx="130" cy="85" r="4.5" class="pt"/>
  <circle cx="249" cy="85" r="4.5" class="pt"/>
  <circle cx="368" cy="85" r="4.5" class="pt"/>
  <text x="130" y="104" class="lbl" text-anchor="middle">a</text>
  <text x="249" y="104" class="lbl" text-anchor="middle">b</text>
  <text x="368" y="104" class="lbl" text-anchor="middle">c</text>
  <!-- legend -->
  <g transform="translate(20, 134)">
    <circle cx="6" cy="0" r="4" class="pt"/>
    <text x="16" y="3" class="leg">0-cell (point)</text>
    <line x1="140" y1="0" x2="180" y2="0" class="iv"/>
    <circle cx="140" cy="0" r="3" class="op"/>
    <circle cx="180" cy="0" r="3" class="op"/>
    <text x="190" y="3" class="leg">1-cell (open interval)</text>
  </g>
</svg>

Unbounded intervals are still 1-cells — the defining functions are allowed to take values $\pm\infty$.

## Cells in $\mathbb{R}^2$: the inductive step

Over a 1-cell base $(a, b) \subseteq \mathbb{R}$, the inductive construction yields two cell types in $\mathbb{R}^2$:

<svg viewBox="0 0 640 270" xmlns="http://www.w3.org/2000/svg" style="max-width:640px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .ax2 { stroke: currentColor; stroke-opacity: 0.35; stroke-width: 1; fill: none; }
      .base { stroke: #ef4444; stroke-width: 3; fill: none; stroke-linecap: round; }
      .op2 { fill: none; stroke: #ef4444; stroke-width: 2; }
      .gr { stroke: #3b82f6; stroke-width: 2.5; fill: none; stroke-linecap: round; }
      .opg { fill: none; stroke: #3b82f6; stroke-width: 2; }
      .band { fill: #3b82f6; fill-opacity: 0.18; stroke: none; }
      .dash { stroke: currentColor; stroke-opacity: 0.35; stroke-width: 1; stroke-dasharray: 3,3; fill: none; }
      .lbl2 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.8; }
      .ttl2 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 12px; }
    </style>
  </defs>
  <!-- Panel A: graph cell -->
  <g>
    <text x="160" y="18" text-anchor="middle" class="ttl2">1-cell: graph of f over (a, b)</text>
    <line x1="30" y1="210" x2="300" y2="210" class="ax2"/>
    <line x1="50" y1="35" x2="50" y2="220" class="ax2"/>
    <text x="303" y="214" class="lbl2">x</text>
    <text x="54" y="42" class="lbl2">y</text>
    <!-- base interval (a, b) on x-axis -->
    <line x1="93" y1="210" x2="247" y2="210" class="base"/>
    <circle cx="90" cy="210" r="4" class="op2"/>
    <circle cx="250" cy="210" r="4" class="op2"/>
    <text x="90" y="228" text-anchor="middle" class="lbl2">a</text>
    <text x="250" y="228" text-anchor="middle" class="lbl2">b</text>
    <!-- graph y = f(x): a smooth curve over (a, b) -->
    <path d="M 93,130 Q 170,60 247,110" class="gr"/>
    <circle cx="90" cy="130" r="4" class="opg"/>
    <circle cx="250" cy="110" r="4" class="opg"/>
    <!-- dashed verticals -->
    <line x1="90" y1="130" x2="90" y2="210" class="dash"/>
    <line x1="250" y1="110" x2="250" y2="210" class="dash"/>
    <text x="172" y="80" class="lbl2">y = f(x)</text>
  </g>
  <!-- Panel B: band cell -->
  <g>
    <text x="480" y="18" text-anchor="middle" class="ttl2">2-cell: band f(x) &lt; y &lt; g(x)</text>
    <line x1="350" y1="210" x2="620" y2="210" class="ax2"/>
    <line x1="370" y1="35" x2="370" y2="220" class="ax2"/>
    <text x="623" y="214" class="lbl2">x</text>
    <text x="374" y="42" class="lbl2">y</text>
    <!-- base interval (a, b) -->
    <line x1="413" y1="210" x2="567" y2="210" class="base"/>
    <circle cx="410" cy="210" r="4" class="op2"/>
    <circle cx="570" cy="210" r="4" class="op2"/>
    <text x="410" y="228" text-anchor="middle" class="lbl2">a</text>
    <text x="570" y="228" text-anchor="middle" class="lbl2">b</text>
    <!-- band: fill between g (upper) and f (lower) -->
    <path d="M 413,150 Q 490,170 567,140 L 567,80 Q 490,50 413,75 Z" class="band"/>
    <!-- f: lower curve -->
    <path d="M 413,150 Q 490,170 567,140" class="gr"/>
    <circle cx="410" cy="150" r="4" class="opg"/>
    <circle cx="570" cy="140" r="4" class="opg"/>
    <!-- g: upper curve -->
    <path d="M 413,75 Q 490,50 567,80" class="gr"/>
    <circle cx="410" cy="75" r="4" class="opg"/>
    <circle cx="570" cy="80" r="4" class="opg"/>
    <!-- dashed verticals -->
    <line x1="410" y1="75" x2="410" y2="210" class="dash"/>
    <line x1="570" y1="80" x2="570" y2="210" class="dash"/>
    <text x="585" y="80" class="lbl2">g(x)</text>
    <text x="585" y="150" class="lbl2">f(x)</text>
  </g>
</svg>

The **red** segment is the base 1-cell $(a, b) \subseteq \mathbb{R}$. The **blue** curve / shaded region is the resulting cell in $\mathbb{R}^2$. Open circles mark excluded boundary — cells are always relatively open in their containing stratum. Iterating this construction one coordinate at a time produces cells in $\mathbb{R}^n$ for any $n$.

## See also

- [[concepts/cell-decomposition]]
- [[concepts/stratifications]]
