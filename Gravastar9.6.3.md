## 1.1 Motivation and scope

Scientific claims, safety decisions, and model deployments are too often adjudicated by **narrative** rather than by a uniform, audit-ready calculus. Two failure modes recur:

1. **Context drift** — small changes in wording, encodings, locale, or time base flip a result.
2. **Temporal fragility** — streaming vs. batch, clock skew, or replay order alters the decision.

**Gravastar** responds with a **microphysics-agnostic, ends-first (teleomorphic)** validation standard that decides *admissible outcomes* the same way everywhere, under open audit.

**Principle.** Gravastar operationalizes the **Principle of Superposition (PoS)** — “Do only that, which would be acceptable to all.” Here, *acceptable to all* means **universally admissible under open-join audit**: any observer admissible under the declared observer-equivalence group $G$ who follows the public method reproduces the decision within preregistered budgets; any compliant counterexample defeats the claim. The calculus is value-neutral about content; it encodes **how** claims must be warranted to **count**.

**Framework (at a glance).**

* **Ternary gate and TST.** A **Timeline Selection Theorem (TST)** governs a ternary decision gate $\delta \in \{-1,0,+1\}$: $\delta=+1$ admits and actualizes a candidate timeline; $\delta=0$ preserves superposition; $\delta=-1$ vetoes.
* **Acceptability field and moral geometry.** Decisions use an **acceptability field** $\Phi(x,t)$ with preregistered bands $\Phi_{\text{neutral}}$ (indifference) and $\Phi_{\min}$ (strict pass). Orientation is set by

  $$
  x \;=\; 2\bigl(\Phi/\Phi_{\max}\bigr) - 1,
  $$

  with $\Phi_{\max}$ preregistered, and the moral state $y=\arctanh(x)$ exposes a **repair vector** via $dy/dx = 1/(1-x^{2})$ whenever $\delta \in \{-1,0\}$.
* **Pinned manifest and comparisons.** A pinned `III.json` declares budgets, thresholds, rounding, and tie policy; all comparisons obey **round-before-compare** at the declared precisions.
* **Floors dominate $\Phi$.** Fail-closed floors are prerequisites: **G-floor** (gauge invariance under admissible re-descriptions), **PoS Screen** (neutrality-only ops), **WITNESS** (asynchronous $W(n)$ vs. separability bounds $B(n)$), **CAUSALITY/ISO** (near-isotropy $A^\star$ and front-speed cap $\hat c \le 1$), **CAPTION$\to$RECEIPT** (byte-equality), and **DETERMINISM** (RNG freeze, platform parity). If a floor fails, $\delta$ cannot pass on the basis of $\Phi$.
* **Temporal governance and receipts.** **TTDA** supplies the time spine: a UTC-anchored **Clock Disclosure Badge**, a **Right-to-Temporal-Resolution** budget, and an explicitly preregistered **streaming/batch parity** bound. Evidence is packaged as **Receipt v2** (code/data/SBOM hashes, thresholds, energy) and audited by **REPLAY-RFD** (Replay-to-First-Divergence).

**Scope — what this paper does and does not claim.**
Gravastar is a **validation calculus**, not a dynamics proposal. It specifies the warrant and audit conditions under which claims **count**; it remains agnostic to content so long as the method is public, observers are admissible under $G$, and compliant counterexamples defeat the claim.

**Intended users and artifacts.**
Experimentalists, ML/AI deployment teams, standards bodies, and auditors seeking a gauge-invariant, time-stable, auditable standard for **admissible outcomes** under open-join audit.

## 1.2 The Principle of Superposition (PoS): “acceptable to all”

Only **neutrality-preserving** operations are permitted while $\delta=0$; **repairs must not tilt the gate**.

**Law (plain language).** *Do only that, which would be acceptable to all.*
“Acceptable to all” means **universally admissible under open-join audit**: any observer admissible under the declared observer-equivalence group $G$ who follows the public method reproduces the decision within preregistered budgets; **one compliant counterexample defeats** the claim.

**Who is “all”?** “All” is **not** a survey panel, a coverage metric, a popularity vote, or any other selection-dependent notion. “All” means **every observer admissible under $G$**—including admissible re-descriptions (tokenization, units/encodings, paraphrase/order, locale)—who follows the method and budgets (time governance, scan protocol) and can reproduce or defeat the decision.

**Operational form (acceptability).**
Let $\tau$ be a candidate timeline and $M$ the declared method (models, data, thresholds, budgets, scan protocol). For any admissible observer $o$,

$$
\delta_o(\tau; M) \in \{-1,0,+1\}.
$$

PoS is satisfied for $\tau$ iff

$$
\begin{aligned}
\textbf{(i) Floors)}\ &\forall o:\ \text{all floors pass and \emph{dominate} }\Phi;\\[2pt]
\textbf{(ii) Reproducibility)}\ &\forall o:\ \delta_o(\tau;M)=+1\ \text{within preregistered budgets};\\[2pt]
\textbf{(iii) Invariance)}\ &\forall g\in G,\ \forall o:\ \delta_o\!\bigl(g\!\cdot\!\tau;\, g\!\cdot\!M\bigr)=\delta_o(\tau;M);\\[2pt]
\textbf{(iv) Time stability)}\ &\text{streaming/batch parity and other TTDA time constraints hold as preregistered};\\[2pt]
\textbf{(v) Defeat)}\ &\text{if a compliant counterexample exists, then }\delta\neq+1\ (\text{claim loses standing}).\\
\end{aligned}
$$

**Acceptability field and moral geometry.**
Decisions use an **acceptability field** $\Phi(x,t)$ with preregistered bands $\Phi_{\text{neutral}}$ (indifference) and $\Phi_{\min}$ (strict pass). Orientation is set by

$$
x \;=\; 2\bigl(\Phi/\Phi_{\max}\bigr)-1,\qquad y=\arctanh(x),\qquad \frac{dy}{dx}=\frac{1}{1-x^{2}},
$$

with $\Phi_{\max}$ preregistered in `III.json`. When $\delta\in\{-1,0\}$, the **repair vector** is read off from $dy/dx$ (how to change inputs to reach $\Phi_{\min}$ under the floors).

**Floors (fail-closed; dominate $\Phi$).**
**G-floor** (gauge invariance under admissible re-descriptions), **PoS Screen** (neutrality-only ops), **WITNESS** (asynchronous $W(n)$ vs.\ separability bounds $B(n)$), **CAUSALITY/ISO** (near-isotropy $A^\star$ and front-speed cap $\hat c\le 1$), **CAPTION$\to$RECEIPT** (byte-equality), **DETERMINISM** (RNG freeze, platform parity). **If any floor fails, $\delta$ cannot pass on the basis of $\Phi$.**

**Temporal governance (TTDA) and receipts.**
TTDA provides the **time spine**: UTC-anchored **Clock Disclosure Badge**, **Right-to-Temporal-Resolution** budget, and a preregistered **streaming/batch parity** bound. Evidence is packaged as **Receipt v2** (hashes, thresholds, energy) and audited by **REPLAY-RFD** (Replay-to-First-Divergence).

**Decision rule (sketch).**

1. **Verify floors.** If any floor fails → $\delta=-1$ (report failure + repair vector).
2. **Compute effective field.** Apply budgets (TTDA, etc.), then compare to $\Phi_{\min}$ and $\Phi_{\text{neutral}}$ using **round-before-compare** at precisions declared in `III.json`.
3. **Gate.** If $\Phi \ge \Phi_{\min}$ and floors pass → $\delta=+1$; if $\Phi \in \Phi_{\text{neutral}}$ → $\delta=0$; else $\delta=-1$.
4. **Audit.** Publish **Receipt v2** and a **REPLAY-RFD** trace; run $G$-tests and TTDA parity checks; invite open-join reproduction.
5. **Supersession.** Any **compliant counterexample** (floor violation or first divergence) **defeats** the standing and triggers supersession.

**What PoS guarantees (and what it doesn’t).**
PoS guarantees a **gauge-invariant, time-stable, open-audit** standard for a claim to **count** under the universal quantifier “all.” It does **not** guarantee truth beyond the declared method/budgets; it guarantees that **standing** is earned only by meeting floors, invariance, time stability, and defeat-by-counterexample.

## 1.3 Contributions and summary of results

**Problem.** Across science, engineering, and AI deployment, admissibility of claims is too often decided by narrative, tuning, or panel heuristics that fail under re-description (paraphrase, units/encodings, tokenization), timing changes (streaming vs. batch), or replay. **Gravastar** supplies a portable, audit-ready calculus that makes *"acceptable to all"* operational, falsifiable, and reproducible.

**Contributions.**

**Summary of results.** The paper delivers: (i) a **provable decision kernel** (TST + $\delta$ calculus) with floors that guarantee **gauge invariance and time stability**; (ii) an **operational geometry** that yields **repair vectors** for non-admissible proposals; (iii) a **time spine** (TTDA) and **receipt stack** (Receipt v2 + REPLAY-RFD) that make outcomes **replayable to first divergence**; (iv) a **standardized methods layer** (ScanProtocol v1, DII-4) for portable measurement; (v) a **witness program** including an agentless limit that aligns with quantum predictions; and (vi) a **quarantined dynamics** option (DNT) for soliton engineering that preserves auditability and causality caps. Collectively, these components constitute a **submission-ready, microphysics-agnostic standard** for **admissible outcomes** under the universal law *"acceptable to all."*


