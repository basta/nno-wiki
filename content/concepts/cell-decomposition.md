---
title: Cell decomposition
---

**Theorem (cell decomposition).** Every definable subset of $\mathbb{R}^n$ admits a finite partition into [[concepts/cells|cells]]. Moreover, for any finite collection of definable functions, the partition can be chosen so each function is $C^r$ on each cell.

This is the structural backbone of [[concepts/tame-geometry|tame geometry]] — it makes [[concepts/dimension-theorem|dimension]] well-defined and supports [[concepts/stratifications|stratifications]].

## Examples

### 1. Closed triangle in $\mathbb{R}^2$ — 7 cells

A closed triangle $T \subseteq \mathbb{R}^2$ (interior + boundary) partitions into:
- **3 vertices** (0-cells),
- **3 open edges** (1-cells),
- **1 open interior** (2-cell).

<svg viewBox="0 0 400 280" xmlns="http://www.w3.org/2000/svg" style="max-width:400px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .interior { fill: #3b82f6; fill-opacity: 0.18; stroke: none; }
      .edge { stroke: #ef4444; stroke-width: 2.5; fill: none; stroke-linecap: butt; }
      .vert { fill: #ef4444; }
      .lbl { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.8; }
      .leg { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.85; }
      .ttl { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 12px; }
    </style>
  </defs>
  <!-- 2-cell: interior -->
  <polygon points="100,220 300,220 200,60" class="interior"/>
  <!-- 1-cells: edges (recessed 12px from vertices to visually separate from 0-cells) -->
  <!-- edge AB (bottom): from (100,220) to (300,220) -->
  <line x1="112" y1="220" x2="288" y2="220" class="edge"/>
  <!-- edge AC: from (100,220) to (200,60). vector (100,-160), length ≈188.7, unit ≈(0.530,-0.848). Recess 12. -->
  <line x1="106.4" y1="209.8" x2="193.6" y2="70.2" class="edge"/>
  <!-- edge BC: from (300,220) to (200,60). vector (-100,-160). Recess 12. -->
  <line x1="293.6" y1="209.8" x2="206.4" y2="70.2" class="edge"/>
  <!-- 0-cells: vertices -->
  <circle cx="100" cy="220" r="5.5" class="vert"/>
  <circle cx="300" cy="220" r="5.5" class="vert"/>
  <circle cx="200" cy="60" r="5.5" class="vert"/>
  <!-- vertex labels -->
  <text x="92" y="240" text-anchor="end" class="lbl">A</text>
  <text x="308" y="240" class="lbl">B</text>
  <text x="200" y="48" text-anchor="middle" class="lbl">C</text>
  <!-- inline label for interior -->
  <text x="200" y="180" text-anchor="middle" class="ttl">open interior (2-cell)</text>
  <!-- legend -->
  <g transform="translate(20, 260)">
    <circle cx="6" cy="0" r="4.5" class="vert"/>
    <text x="16" y="3" class="leg">0-cells: 3</text>
    <line x1="90" y1="0" x2="120" y2="0" class="edge"/>
    <text x="128" y="3" class="leg">1-cells: 3</text>
    <rect x="180" y="-5" width="22" height="10" class="interior"/>
    <text x="208" y="3" class="leg">2-cell: 1</text>
  </g>
</svg>

If we wanted a decomposition of the **whole plane** adapted to $T$, we would refine further: each of the unbounded "outside" regions and the lines extending the edges become additional cells.

### 2. Graph of $|x|$ — 3 cells

The set $\Gamma = \{(x, |x|) : x \in \mathbb{R}\} \subseteq \mathbb{R}^2$ decomposes into:
- **1 vertex** at the origin (0-cell),
- **2 open rays** $\{(x, x) : x > 0\}$ and $\{(x, -x) : x < 0\}$ (1-cells).

<svg viewBox="0 0 320 240" xmlns="http://www.w3.org/2000/svg" style="max-width:320px;height:auto;display:block;margin:1em auto;">
  <defs>
    <style>
      .ax3 { stroke: currentColor; stroke-opacity: 0.35; stroke-width: 1; fill: none; }
      .ray { stroke: #3b82f6; stroke-width: 2.5; fill: none; stroke-linecap: butt; }
      .vrt { fill: #ef4444; }
      .lbl3 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.8; }
      .leg3 { fill: currentColor; font-family: ui-sans-serif, system-ui, sans-serif; font-size: 11px; opacity: 0.85; }
    </style>
  </defs>
  <!-- axes -->
  <line x1="20" y1="200" x2="300" y2="200" class="ax3"/>
  <line x1="160" y1="20" x2="160" y2="220" class="ax3"/>
  <text x="303" y="204" class="lbl3">x</text>
  <text x="164" y="28" class="lbl3">y</text>
  <!-- left ray (1-cell): recessed from vertex; from (40,80) toward vertex at (160,200), stop at ~ (153, 193) -->
  <line x1="40" y1="80" x2="153" y2="193" class="ray"/>
  <!-- right ray (1-cell): from (167,193) to (280,80) -->
  <line x1="167" y1="193" x2="280" y2="80" class="ray"/>
  <!-- 0-cell: vertex at origin -->
  <circle cx="160" cy="200" r="5.5" class="vrt"/>
  <!-- inline labels -->
  <text x="80" y="68" class="lbl3">{(x, −x) : x &lt; 0}</text>
  <text x="240" y="68" text-anchor="end" class="lbl3">{(x, x) : x &gt; 0}</text>
  <text x="172" y="216" class="lbl3">(0, 0)</text>
  <!-- legend -->
  <g transform="translate(20, 232)">
    <circle cx="6" cy="0" r="4.5" class="vrt"/>
    <text x="16" y="3" class="leg3">0-cell: 1</text>
    <line x1="90" y1="0" x2="120" y2="0" class="ray"/>
    <text x="128" y="3" class="leg3">1-cells: 2</text>
  </g>
</svg>

Same structure for **ReLU**'s graph $\{(x, \sigma(x))\}$: vertex at origin + horizontal ray $\{(x, 0) : x < 0\}$ + diagonal ray $\{(x, x) : x > 0\}$. The kink lives in the 0-cell; the smooth pieces are the two 1-cells. This is precisely why the [[concepts/clarke-subdifferential|Clarke subdifferential]] is set-valued only on a lower-dimensional (here 0-dimensional) "active stratum".

### 3. The refinement clause

The "moreover" part of the theorem says: given any finite list of definable functions $f_1, \dots, f_m$, we can choose the decomposition so each $f_i$ is $C^r$ on every cell. Concretely, for a ReLU network's loss, the parameter space $\mathbb{R}^d$ admits a finite cell decomposition such that the loss is a polynomial (in fact, $C^\infty$) on each cell. The kinks live in the lower-dimensional cells where some neuron pre-activation hits zero.

This is the structural reason "definable everywhere, smooth almost everywhere" works: the bad set has lower dimension by [[concepts/dimension-theorem|the dimension theorem]].

## See also

- [[concepts/dimension-theorem]]
- [[concepts/stratifications]]
