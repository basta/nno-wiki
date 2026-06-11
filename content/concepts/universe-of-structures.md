---
title: The universe of structures on ℝ
---

This page draws and annotates the "universe" of [[concepts/structures|structures]] on $\mathbb{R}$ that appear in NNO (Exercise 0.3). It collects the named structures, the inclusions between them, the three growth **dividing lines** (o-minimal / polynomially bounded / exponentially bounded), the **field of exponents** of each, and which activation and loss functions are definable where.

It synthesizes Figure 4 and §3.2 of the course paper (Bareilles–Gehret–Aspman–Lepšová–Mareček, [[references|Deep Learning as the Disciplined Construction of Tame Objects]]). Where that paper writes $\mathbb{R}_{\mathrm{arctan}}, \mathbb{R}_{G}, \mathbb{R}^{\mathbb{R}}_{\mathrm{alg}}$, the exercise's list uses a slightly different roster; the structures common to both are reproduced faithfully below.

## The picture

<svg viewBox="0 0 760 560" xmlns="http://www.w3.org/2000/svg" style="max-width:100%;height:auto;display:block;margin:1em auto;font-family:ui-sans-serif, system-ui, sans-serif">
  <defs>
    <marker id="arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse">
      <path d="M0,0 L10,5 L0,10 z" fill="currentColor"/>
    </marker>
  </defs>
  <!-- growth bands (o-minimal column only: x 0..545) -->
  <rect x="0" y="345" width="545" height="215" fill="green" opacity="0.07"/>
  <rect x="0" y="120" width="545" height="225" fill="orange" opacity="0.07"/>
  <rect x="0" y="0"   width="545" height="120" fill="red" opacity="0.07"/>
  <!-- dashed dividing lines -->
  <line x1="0" y1="345" x2="545" y2="345" stroke="green" stroke-width="1.5" stroke-dasharray="7 5"/>
  <line x1="0" y1="120" x2="545" y2="120" stroke="red"   stroke-width="1.5" stroke-dasharray="7 5"/>
  <text x="8" y="538" font-size="11" font-style="italic" fill="currentColor" opacity="0.8">polynomially bounded · field of exponents ℚ</text>
  <text x="8" y="338" font-size="11" font-style="italic" fill="currentColor" opacity="0.8">exponentially bounded (defines exp) · field of exponents ℝ</text>
  <text x="8" y="20"  font-size="11" font-style="italic" fill="currentColor" opacity="0.8">transexponential — none known (open)</text>
  <!-- separator + non-o-minimal panel -->
  <line x1="555" y1="0" x2="555" y2="560" stroke="currentColor" stroke-width="1" opacity="0.3"/>
  <rect x="565" y="40" width="185" height="500" fill="currentColor" opacity="0.04"/>
  <text x="657" y="30" font-size="12" font-style="italic" text-anchor="middle" fill="currentColor" opacity="0.85">outside o-minimality</text>
  <!-- edges (o-minimal): R1 -> R2 means R1 ⊆ R2 -->
  <g stroke="currentColor" stroke-width="1.5" fill="none" opacity="0.65" marker-end="url(#arrow)">
    <line x1="150" y1="485" x2="150" y2="445"/>            <!-- alg -> RE -->
    <line x1="150" y1="415" x2="150" y2="380"/>            <!-- RE -> an -->
    <line x1="185" y1="490" x2="325" y2="445"/>            <!-- alg -> exp -->
    <line x1="160" y1="352" x2="245" y2="282"/>            <!-- an -> an,exp -->
    <line x1="335" y1="417" x2="285" y2="282"/>            <!-- exp -> an,exp -->
    <line x1="375" y1="417" x2="455" y2="347"/>            <!-- exp -> Pfaff(alg) -->
    <line x1="285" y1="250" x2="360" y2="192"/>            <!-- an,exp -> Pfaff(an) -->
    <line x1="455" y1="315" x2="392" y2="192"/>            <!-- Pfaff(alg) -> Pfaff(an) -->
  </g>
  <!-- open / dashed edge to transexponential -->
  <line x1="375" y1="160" x2="375" y2="88" stroke="currentColor" stroke-width="1.5" stroke-dasharray="5 5" opacity="0.5" marker-end="url(#arrow)"/>
  <!-- non-o-minimal edges -->
  <g stroke="currentColor" stroke-width="1.3" fill="none" opacity="0.5" marker-end="url(#arrow)">
    <line x1="657" y1="415" x2="657" y2="350"/>            <!-- (alg,2^Z) -> R_PH -->
    <line x1="657" y1="320" x2="657" y2="255"/>            <!-- R_PH -> top -->
  </g>
  <!-- faint anchor: R_alg feeds the non-o-minimal column -->
  <path d="M195,500 C400,520 560,500 612,440" stroke="currentColor" stroke-width="1.2" fill="none" stroke-dasharray="3 5" opacity="0.4" marker-end="url(#arrow)"/>
  <!-- node helper boxes -->
  <g font-size="12" text-anchor="middle">
    <!-- o-minimal nodes -->
    <g>
      <rect x="106" y="485" width="88" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="150" y="504" fill="currentColor">ℝ<tspan baseline-shift="sub" font-size="9">alg</tspan></text>
    </g>
    <g>
      <rect x="100" y="415" width="100" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="150" y="434" fill="currentColor">ℝ<tspan baseline-shift="super" font-size="9">RE</tspan></text>
    </g>
    <g>
      <rect x="108" y="350" width="84" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="150" y="369" fill="currentColor">ℝ<tspan baseline-shift="sub" font-size="9">an</tspan></text>
    </g>
    <g>
      <rect x="306" y="415" width="88" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="350" y="434" fill="currentColor">ℝ<tspan baseline-shift="sub" font-size="9">exp</tspan></text>
    </g>
    <g>
      <rect x="212" y="250" width="106" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="265" y="269" fill="currentColor">ℝ<tspan baseline-shift="sub" font-size="9">an,exp</tspan></text>
    </g>
    <g>
      <rect x="418" y="315" width="106" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="471" y="334" fill="currentColor">Pfaff(ℝ<tspan baseline-shift="sub" font-size="9">alg</tspan>)</text>
    </g>
    <g>
      <rect x="322" y="160" width="106" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="375" y="179" fill="currentColor">Pfaff(ℝ<tspan baseline-shift="sub" font-size="9">an</tspan>)</text>
    </g>
    <text x="375" y="74" fill="currentColor" font-style="italic" opacity="0.7">??? (transexp.)</text>
    <!-- non-o-minimal nodes -->
    <g>
      <rect x="600" y="415" width="114" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="657" y="434" fill="currentColor" font-size="11">(ℝ<tspan baseline-shift="sub" font-size="8">alg</tspan>, 2<tspan baseline-shift="super" font-size="8">ℤ</tspan>)</text>
    </g>
    <g>
      <rect x="595" y="320" width="124" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="657" y="339" fill="currentColor" font-size="11">ℝ<tspan baseline-shift="sub" font-size="8">PH</tspan> = (ℝ<tspan baseline-shift="sub" font-size="8">alg</tspan>, ℤ)</text>
    </g>
    <g>
      <rect x="617" y="225" width="80" height="30" rx="6" fill="currentColor" opacity="0.10"/>
      <text x="657" y="244" fill="currentColor">ℝ<tspan baseline-shift="super" font-size="9">⊤</tspan></text>
    </g>
    <text x="657" y="290" fill="currentColor" font-size="10" opacity="0.7">all subsets definable</text>
    <text x="657" y="475" fill="currentColor" font-size="10" opacity="0.7">2<tspan baseline-shift="super" font-size="8">ℤ</tspan> infinite discrete</text>
    <text x="657" y="380" fill="currentColor" font-size="10" opacity="0.7">defines all of arithmetic</text>
  </g>
  <text x="272" y="552" font-size="10" fill="currentColor" opacity="0.6" text-anchor="middle">arrow R₁ → R₂ means R₁ ⊆ R₂</text>
</svg>

The left column is the **o-minimal** world, stratified by growth; the right column holds the **non-o-minimal** structures from the exercise, where the growth dividing lines no longer apply.

## The structures

| Structure | Definition | o-minimal? | Field of exponents |
|---|---|---|---|
| $\mathcal{R}_{\mathrm{alg}}$ | the [[concepts/semialgebraic\|semialgebraic]] sets — the smallest structure satisfying (S1)–(S6). Generated by $<, +, \cdot$. | ✓ | $\mathbb{Q}$ |
| $\mathbb{R}^{\mathrm{RE}}$ | the **restricted-exponential** structure $\langle \mathcal{R}_{\mathrm{alg}}, \exp\!\mid_{[0,1]}\rangle$ — adds the exponential restricted to a compact interval, but **not** global $\exp$. Sits between $\mathcal{R}_{\mathrm{alg}}$ and $\mathcal{R}_{\mathrm{an}}$. *(Notation not in the published paper — see note below.)* | ✓ | $\mathbb{Q}$ |
| $\mathcal{R}_{\mathrm{an}}$ | generated by all **restricted real-analytic** functions: $f$ real-analytic on a neighbourhood of $[-1,1]^n$, zero outside. o-minimal by Gabrielov / van den Dries. | ✓ | $\mathbb{Q}$ |
| $\mathcal{R}_{\exp}$ | the smallest structure containing **global** $\exp : \mathbb{R} \to \mathbb{R}$. o-minimal by **Wilkie's theorem** (geometric Tarski problem). | ✓ | $\mathbb{R}$ |
| $\mathcal{R}_{\mathrm{an,exp}}$ | the smallest structure expanding **both** $\mathcal{R}_{\mathrm{an}}$ and $\mathcal{R}_{\exp}$. o-minimal by van den Dries–Miller. | ✓ | $\mathbb{R}$ |
| $\mathrm{Pfaff}(\mathcal{R}_{\mathrm{alg}}) =: \mathcal{R}_{\mathrm{Pfaff}}$ | the **[[concepts/pfaffian-functions\|Pfaffian closure]]** of $\mathcal{R}_{\mathrm{alg}}$ (Speissegger): the smallest o-minimal expansion closed under solutions of Pfaffian equations / antiderivatives of definable functions. Contains $\mathcal{R}_{\exp}$. | ✓ | $\mathbb{R}$ |
| $\mathrm{Pfaff}(\mathcal{R}_{\mathrm{an}})$ | the Pfaffian closure of $\mathcal{R}_{\mathrm{an}}$ — contains both $\mathcal{R}_{\mathrm{an,exp}}$ and $\mathcal{R}_{\mathrm{Pfaff}}$. | ✓ | $\mathbb{R}$ |
| $(\mathcal{R}_{\mathrm{alg}}, 2^{\mathbb{Z}})$ | $\mathcal{R}_{\mathrm{alg}}$ with a predicate for the powers of two $\{2^k : k \in \mathbb{Z}\}$. **Not** o-minimal: $2^{\mathbb{Z}}$ is an infinite discrete subset of $\mathbb{R}$. (Model-theoretically *tame* in a weaker sense, but outside o-minimality.) | ✗ | — |
| $\mathcal{R}_{\mathrm{PH}} = (\mathcal{R}_{\mathrm{alg}}, \mathbb{Z})$ | $\mathcal{R}_{\mathrm{alg}}$ with a predicate for $\mathbb{Z}$. **Not** o-minimal (Non-example 3.4) — and far worse: it defines full integer arithmetic, hence all projective sets. Maximally wild short of $\mathcal{R}_\top$. | ✗ | — |
| $\mathcal{R}_\top$ | the **top** structure: every subset of every $\mathbb{R}^n$ is definable. Trivially closed under everything; useless for tame geometry. | ✗ | — |

## The three dividing lines

These are properties of **o-minimal** structures, ordered by strictly increasing growth (Definitions 3.30, 3.32, Open Question 3.33):

1. **Polynomially bounded** — every definable $f : \mathbb{R} \to \mathbb{R}$ satisfies $|f(t)| \le t^N$ eventually, for some $N \in \mathbb{N}$. Equivalently every eventually-nonzero definable $f$ has $f(t) \sim C t^\gamma$ for some real exponent $\gamma$. Examples: $\mathcal{R}_{\mathrm{alg}}, \mathbb{R}^{\mathrm{RE}}, \mathcal{R}_{\mathrm{an}}$.
2. **Exponentially bounded** — bounded by some finite iterate $\exp_n = \exp \circ \cdots \circ \exp$. Strictly larger class; contains everything that *defines* $\exp$: $\mathcal{R}_{\exp}, \mathcal{R}_{\mathrm{an,exp}}, \mathcal{R}_{\mathrm{Pfaff}}, \mathrm{Pfaff}(\mathcal{R}_{\mathrm{an}})$.
3. **Transexponential** — grows faster than every $\exp_n$. **Open question (3.33):** no o-minimal structure is known to define a transexponential function; the top band of the diagram is conjecturally empty.

The line between (1) and (2) is sharp:

> **Exponential dichotomy (Miller, 3.32).** Every o-minimal structure is *either* polynomially bounded *or* defines $\exp : \mathbb{R} \to \mathbb{R}$ — never neither, never both-without-exp.

This is why the green dashed line in the diagram is exactly "does it define $\exp$?": crossing it *forces* the exponential to appear.

## Field of exponents

The **field of exponents** of an o-minimal $\mathcal{R}$ is $\{\gamma \in \mathbb{R} : t^\gamma \text{ is definable on } (0,\infty)\}$ — it is genuinely a subfield of $\mathbb{R}$.

- $\mathbb{Q}$ for the polynomially bounded structures $\mathcal{R}_{\mathrm{alg}}, \mathbb{R}^{\mathrm{RE}}, \mathcal{R}_{\mathrm{an}}$ — only rational power functions are definable.
- $\mathbb{R}$ for everything containing $\exp$ ($\mathcal{R}_{\exp}, \mathcal{R}_{\mathrm{an,exp}}, \mathcal{R}_{\mathrm{Pfaff}}, \dots$): once you have $\exp$ and $\log$, $t^\gamma = \exp(\gamma \log t)$ is definable for *every* real $\gamma$.

(The non-o-minimal structures have no field of exponents — the notion is defined only inside o-minimality.)

The field of exponents is not a curiosity: it controls convergence rates in tame optimization — e.g. the superlinear rate $O(2^{-(1+\gamma)^k})$ of nonsmooth Newton, and the [[concepts/kl-inequality|KL]] exponent (Remark 3.31).

## Where activation and loss functions live

The point of the whole hierarchy, for NNO: pin each activation/loss to the **smallest** structure that defines it.

| Function(s) | Smallest structure | Why |
|---|---|---|
| ReLU, leaky ReLU, hard-tanh, abs, max-pooling, hinge / $L^1$ / $L^2$ loss | $\mathcal{R}_{\mathrm{alg}}$ | piecewise-polynomial → [[concepts/semialgebraic\|semialgebraic]] |
| bump functions, $\exp\!\mid_{[0,1]}$, $\sin\!\mid_{[0,2\pi]}$ | $\mathbb{R}^{\mathrm{RE}}$ / $\mathcal{R}_{\mathrm{an}}$ | restricted analytic, but not global growth |
| sigmoid, tanh, softplus, ELU, SiLU/swish, Gaussian, cross-entropy/log-loss | $\mathcal{R}_{\exp}$ | all of the paper's Table 1 **except** GELU and arctan (Lemma 3.12) |
| GELU, arctan, erf | $\mathcal{R}_{\mathrm{Pfaff}}$ | definable as antiderivatives via the [[concepts/pfaffian-functions\|Pfaffian closure]] (Cor. 3.18) — **not** definable in $\mathcal{R}_{\mathrm{an,exp}}$ (erf: Lemma 3.14) |
| (everything in Table 1) | $\mathcal{R}_{\mathrm{Pfaff}}$ | Corollary 3.18: a single o-minimal structure defining every common activation/loss |

So $\mathcal{R}_{\mathrm{Pfaff}}$ is the practical "home" structure for deep learning: all standard activations and losses are definable in it, hence tame.

## Separating functions (Remark 3.20)

Witnesses that the inclusions are **strict**:

- $\arctan$ — in $\mathcal{R}_{\mathrm{arctan}} = (\mathcal{R}_{\mathrm{alg}}, \arctan) \subseteq \mathcal{R}_{\mathrm{Pfaff}}$, **not** in $\mathcal{R}_{\exp}$.
- $\exp\!\mid_{[0,1]}$ — in $\mathcal{R}_{\mathrm{an}}$, **not** in $\mathcal{R}_{\mathrm{arctan}}$.
- $\sin\!\mid_{[0,2\pi]}$ — in $\mathcal{R}_{\mathrm{an}}$, **not** in $\mathcal{R}_{\exp}$.
- $\mathrm{erf}$ — in $\mathcal{R}_{\mathrm{Pfaff}}$, **not** in $\mathcal{R}_{\mathrm{an,exp}}$.
- the Gamma function $\Gamma$ — definable in $\mathcal{R}_{G,\exp}$, **not** in $\mathcal{R}_{\mathrm{an,exp}}$, and (notably) **not** in $\mathcal{R}_{\mathrm{Pfaff}}$ either.

## A note on $\mathbb{R}^{\mathrm{RE}}$

The symbol $\mathbb{R}^{\mathrm{RE}}$ in the exercise does not appear in the published paper's Figure 4 (which instead lists $\mathcal{R}_{\mathrm{arctan}}, \mathcal{R}_G, \mathbb{R}^{\mathbb{R}}_{\mathrm{alg}}$ in that "between $\mathcal{R}_{\mathrm{alg}}$ and $\mathcal{R}_{\mathrm{an}}$" band). The reading above — **R**estricted **E**xponential, $\langle\mathcal{R}_{\mathrm{alg}}, \exp\!\mid_{[0,1]}\rangle$ — is the most natural fit (polynomially bounded, field of exponents $\mathbb{Q}$, strictly between $\mathcal{R}_{\mathrm{alg}}$ and $\mathcal{R}_{\mathrm{an}}$), but **confirm it against the lecture's own definition** before relying on it.

## See also

- [[concepts/structures]] — the (S1)–(S6) axioms and the §7 catalogue
- [[concepts/o-minimal-structures]]
- [[concepts/semialgebraic]]
- [[concepts/kl-inequality]] — where the field of exponents shows up
- [[references|Bareilles–Gehret et al. — Deep Learning as the Disciplined Construction of Tame Objects]]
