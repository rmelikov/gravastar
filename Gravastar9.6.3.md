## 1.1 Motivation and scope

Scientific claims, safety decisions, and model deployments are too often adjudicated by **narrative** rather than by a uniform, audit-ready calculus. Two failure modes recur:

1. **Context drift** — small changes in wording, encodings, locale, or time base flip a result.
2. **Temporal fragility** — streaming vs. batch, clock skew, or replay order alters the decision.

**Gravastar** responds with a **microphysics-agnostic, ends-first (teleomorphic)** validation standard that decides *admissible outcomes* the same way everywhere, under open audit.

**Principle.** Gravastar operationalizes the **Principle of Superposition (PoS)** — “Do only that, which would be acceptable to all.” Here, *acceptable to all* means **universally admissible under open-join audit**: any observer admissible under the declared observer-equivalence group $G$ who follows the public method reproduces the decision within preregistered budgets; any compliant counterexample defeats the claim. The calculus is value-neutral about content; it encodes **how** claims must be warranted to **count**.

**Framework (at a glance).**

* **Ternary gate and TST.** A **Timeline Selection Theorem (TST)** governs a ternary decision gate $\delta \in {-1,0,+1}$: $\delta=+1$ admits and actualizes a candidate timeline; $\delta=0$ preserves superposition; $\delta=-1$ vetoes.
* **Acceptability field and moral geometry.** Decisions use an **acceptability field** $\Phi(x,t)$ with preregistered bands $\Phi_{\mathrm{neutral}}$ (indifference) and $\Phi_{\min}$ (strict pass). Orientation is set by
  $x = 2(\Phi/\Phi_{\max}) - 1,$
  with $\Phi_{\max}$ preregistered, and the moral state $y=\mathrm{arctanh}(x)$ exposes a **repair vector** via $dy/dx = 1/(1-x^{2})$ whenever $\delta \in {-1,0}$.
* **Pinned manifest and comparisons.** A pinned `III.json` declares budgets, thresholds, rounding, and tie policy; all comparisons obey **round-before-compare** at the declared precisions.
* **Floors dominate $\Phi$.** Fail-closed floors are prerequisites: **G-floor** (gauge invariance under admissible re-descriptions), **PoS Screen** (neutrality-only ops), **WITNESS** (asynchronous $W(n)$ vs. separability bounds B(n)), **CAUSALITY/ISO** (near-isotropy $A^\star$ and front-speed cap $\hat{c} \le 1$), **CAPTION $\to$ RECEIPT** (byte-equality), and **DETERMINISM** (RNG freeze, platform parity). If a floor fails, $\delta$ cannot pass on the basis of $\Phi$.
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
Let $\tau$ be a candidate timeline and $M$ the declared method (models, data, thresholds, budgets, scan protocol). For any admissible observer $o$:
$\delta_o(\tau; M) \in {-1,0,+1}$.

PoS is satisfied for $\tau$ iff:

* **(i) Floors)** $\forall o$: all floors pass and **dominate** $\Phi$.
* **(ii) Reproducibility)** $\forall o$: $\delta_o(\tau;M)=+1$ within preregistered budgets.
* **(iii) Invariance)** $\forall g\in G,\ \forall o$: $\delta_o(g\cdot \tau;, g\cdot M)=\delta_o(\tau;M)$.
* **(iv) Time stability)** streaming/batch parity and other TTDA time constraints hold as preregistered.
* **(v) Defeat)** if a compliant counterexample exists, then $\delta\neq+1$ (claim loses standing).

**Acceptability field and moral geometry.**
Decisions use an **acceptability field** $\Phi(x,t)$ with preregistered bands $\Phi_{\mathrm{neutral}}$ (indifference) and $\Phi_{\min}$ (strict pass). Orientation is set by
$x = 2(\Phi/\Phi_{\max}) - 1,\quad y=\mathrm{arctanh}(x),\quad \frac{dy}{dx}=\frac{1}{1-x^{2}},$
with $\Phi_{\max}$ preregistered in `III.json`. When $\delta\in{-1,0}$, the **repair vector** is read off from $dy/dx$ (how to change inputs to reach $\Phi_{\min}$ under the floors).

**Floors (fail-closed; dominate $\Phi$).**
**G-floor** (gauge invariance under admissible re-descriptions), **PoS Screen** (neutrality-only ops), **WITNESS** (asynchronous $W(n)$ vs. separability bounds B(n)), **CAUSALITY/ISO** (near-isotropy $A^\star$ and front-speed cap $\hat{c}\le 1$), **CAPTION $\to$ RECEIPT** (byte-equality), **DETERMINISM** (RNG freeze, platform parity). **If any floor fails, $\delta$ cannot pass on the basis of $\Phi$.**

**Temporal governance (TTDA) and receipts.**
TTDA provides the **time spine**: UTC-anchored **Clock Disclosure Badge**, **Right-to-Temporal-Resolution** budget, and a preregistered **streaming/batch parity** bound. Evidence is packaged as **Receipt v2** (hashes, thresholds, energy) and audited by **REPLAY-RFD** (Replay-to-First-Divergence).

**Decision rule (sketch).**

1. **Verify floors.** If any floor fails → $\delta=-1$ (report failure + repair vector).
2. **Compute effective field.** Apply budgets (TTDA, etc.), then compare to $\Phi_{\min}$ and $\Phi_{\mathrm{neutral}}$ using **round-before-compare** at precisions declared in `III.json`.
3. **Gate.** If $\Phi \ge \Phi_{\min}$ and floors pass → $\delta=+1$; if $\Phi \in \Phi_{\mathrm{neutral}}$ → $\delta=0$; else $\delta=-1$.
4. **Audit.** Publish **Receipt v2** and a **REPLAY-RFD** trace; run $G$-tests and TTDA parity checks; invite open-join reproduction.
5. **Supersession.** Any **compliant counterexample** (floor violation or first divergence) **defeats** the standing and triggers supersession.

**What PoS guarantees (and what it doesn’t).**
PoS guarantees a **gauge-invariant, time-stable, open-audit** standard for a claim to **count** under the universal quantifier “all.” It does **not** guarantee truth beyond the declared method/budgets; it guarantees that **standing** is earned only by meeting floors, invariance, time stability, and defeat-by-counterexample.

## 1.3 Contributions and summary of results

**Problem.** Across science, engineering, and AI deployment, admissibility is too often decided by narrative and selection effects. Small re-descriptions (paraphrase, units/encodings, locale, tokenization, ordering) or timebase changes (streaming vs. batch, clock skew, replay order) can flip outcomes. We require a gauge-invariant, time-stable, open-audit calculus that makes *“acceptable to all”* operational, falsifiable, and reproducible.

**Contributions.**

* **Law → calculus.** We formalize the Principle of Superposition (PoS)—“Do only that, which would be acceptable to all”—into a validation calculus that is **universally admissible under open-join audit**: any observer admissible under the declared observer-equivalence group $G$ who follows the public method reproduces the decision within preregistered budgets; any compliant counterexample defeats a claim.
* **Timeline Selection Theorem (TST) & ternary gate.** We define a ternary decision gate $\delta \in {-1,0,+1}$ governed by TST: $\delta=+1$ **admits** and actualizes a candidate timeline; $\delta=0$ **preserves superposition**; $\delta=-1$ **vetoes**. Defeat by compliant counterexample triggers **supersession**.
* **Acceptability field and moral geometry with repairs.** We introduce an **acceptability field** $\Phi(x,t)$ with preregistered bands $\Phi_{\mathrm{neutral}}$ (indifference) and $\Phi_{\min}$ (strict pass), orientation
  $x = 2(\Phi/\Phi_{\max}) - 1,\quad y=\mathrm{arctanh}(x),\quad \frac{dy}{dx}=\frac{1}{1-x^{2}},$
  and an explicit **repair vector** for $\delta \in {-1,0}$ that prescribes minimal adjustments toward admissibility **without breaking floors**.
* **Floors that dominate $\Phi$.** We specify **fail-closed invariants** that must pass before $\Phi$ can decide: **G-floor** (gauge invariance under admissible re-descriptions), **PoS Screen** (neutrality-only ops), **WITNESS** (asynchronous $W(n)$ vs. separability bounds B(n)), **CAUSALITY/ISO** (near-isotropy $A^\star$ and front-speed cap $\hat{c} \le 1$), **CAPTION $\to$ RECEIPT** (byte-equality), and **DETERMINISM** (RNG freeze, platform parity). **Floors $\gg \Phi$:** no amount of score mass can rescue a floor failure.
* **Temporal governance (TTDA).** We define a UTC-anchored **Clock Disclosure Badge**, a **Right-to-Temporal-Resolution** budget, and preregistered **streaming/batch parity** constraints; temporal budgets are integrated directly into the decision calculus with **round-before-compare**, pinned in the **III.json** manifest.
* **Receipts and auditability.** We provide **Receipt v2** (code/data/SBOM hashes, thresholds, energy, explain_url) and **REPLAY-RFD** (Replay-to-First-Divergence) for byte-equality binding and auditor-grade reproducibility (first divergence is the stopping rule).
* **Methods standardization.** We publish **ScanProtocol v1** (bidirectional scans, dark-window readout, waits of $\ge 3\cdot\tau_{\mathrm{reset}}$, three-grid alias refuter; basis disclosure when interference or phase matters) and a default invariant set **DII-4** $\bigl(R(u), A^\star, \hat{c}, W(n)!:!B(n)\bigr)$.
* **Witness program and agentless limit.** We define CHSH-style witnesses and an **agentless** limit that recovers standard quantum predictions and cleanly explains why **panels/coverage are evidence but never define “all.”**
* **Quarantined dynamics (optional).** We include an **engineered $\Phi$** layer (discrete nonlinear transport) that is quarantined from the decision kernel, cannot relax floors, and must publish a measured causality cap $\hat{c}$.
* **Portability demonstration (Adamas-1D).** We provide a physical testbed (e.g., CNT strain/spectroscopy runs with $\delta$-windows, byte-equality receipts, and end-to-end REPLAY-RFD) showing that the calculus is microphysics-agnostic; Adamas-1D serves as a concrete instantiation.
* **Governance and supersession.** We define an **open-join audit** and **supersession** regime whereby a compliant counterexample or first divergence removes standing and replaces prior decisions with a receipt-backed update.

**Summary of results.**
The paper delivers: (i) a **provable decision kernel** (TST + ternary gate) with defeat/supersession; (ii) a **moral-geometry repair calculus** $y=\mathrm{arctanh}(x)$ with a usable gradient $dy/dx=1/(1-x^{2})$; (iii) a **floor system that dominates $\Phi$** (G-floor, PoS Screen, WITNESS, CAUSALITY/ISO, CAPTION $\to$ RECEIPT, DETERMINISM); (iv) a **pinned manifest** with **round-before-compare**; (v) a **TTDA time spine** (Clock Badge, RTR budget, streaming/batch parity); (vi) **Receipt v2 + REPLAY-RFD**; (vii) **ScanProtocol v1** and **DII-4**; (viii) portability to **Adamas-1D** and recovery of **CHSH** predictions in the agentless witness program. Together these components yield a gauge-invariant, time-stable, auditable standard for **admissible outcomes** under the universal law *“acceptable to all.”*

## 1.4 Paper organization

**Section 2 — Preliminaries & notation.** Symbols and conventions; admissible observers and the observer-equivalence group $G$; the pinned `III.json` manifest (budgets, thresholds, rounding, tie policy) and the **round-before-compare** rule.

**Section 3 — Moral geometry & acceptability field.** Definition of the acceptability field $\Phi(x,t)$ with bands $\Phi_{\min}$ and $\Phi_{\mathrm{neutral}}$; mapping $\Phi \mapsto x$ via $x = 2(\Phi/\Phi_{\max})-1$ (with $\Phi_{\max}$ preregistered); moral state $y=\mathrm{arctanh}(x)$ and the construction of the **repair vector** from $dy/dx=1/(1-x^{2})$.

**Section 4 — Timeline Selection Theorem (TST) & ternary validation.** Decision gate $\delta \in {-1,0,+1}$ (admit, superposition, veto); TST statement and operational consequences; defeat by compliant counterexample and public **supersession**.

**Section 5 — Floors (fail-closed invariants).** Formal specification and proofs for **G-floor** (gauge-invariance under admissible re-descriptions), **PoS Screen** (neutrality-only ops), **WITNESS** (asynchronous $W(n)$ vs. separability bounds B(n)), **CAUSALITY/ISO** (near-isotropy $A^\star$ and front-speed cap $\hat{c}\le 1$), **CAPTION $\to$ RECEIPT** (byte-equality), and **DETERMINISM** (RNG freeze, platform parity); procedures ensuring **floors dominate $\Phi$**.

**Section 6 — Temporal governance (TTDA).** UTC-anchored **Clock Disclosure Badge**, **Right-to-Temporal-Resolution** budget, and preregistered **streaming/batch parity** constraints; integration of temporal budgets directly into comparisons and audits.

**Section 7 — Receipts & auditability.** **Receipt v2** schema (code/data/SBOM hashes, thresholds, energy, explain_url) and **REPLAY-RFD** (Replay-to-First-Divergence); auditor workflow and outputs.

**Section 8 — ScanProtocol v1 (methods standardization).** Bidirectional scans, dark-window readout, waits of $\ge 3\cdot\tau_{\mathrm{reset}}$, three-grid alias refuter; basis disclosure when interference or phase matters.

**Section 9 — Witness program and agentless limit.** CHSH-style witnesses; an agentless limit that recovers standard quantum predictions; why panels/coverage are evidence but never define “all.”

**Section 10 — Engineered $\Phi$ (quarantined dynamics).** Discrete nonlinear transport as an optional engineered-$\Phi$ layer that cannot relax floors and must publish a measured causality cap $\hat{c}$.

**Section 11 — Adamas-1D physical testbed.** CNT strain/spectroscopy runs with $\delta$-windows, byte-equality receipts, and end-to-end REPLAY-RFD demonstrating portability and microphysics-agnostic operation.

**Section 12 — Falsification, threat models, and governance.** Adversarial scenarios, defeat conditions, governance defaults, and supersession procedures under open-join audit.

**Section 13 — Related work.** Connections to standards, reproducibility frameworks, and theory relevant to gauge invariance, time governance, and auditability.

**Section 14 — Discussion & limitations.** What Gravastar does and does not guarantee; assumptions, scope limits, and ethical notes on PoS and universal admissibility.

**Section 15 — Future work.** Expanded witness suites, cross-domain testbeds, extensions to temporal budgets and receipts, and implementation pathways (including Gravastar-TVLM / LLM integrations).

**Section 16 — Acknowledgments.**

**Section 17 — Data, code & receipt availability.** Identifiers, links, explain_url, and distribution of Receipt v2 bundles and audit traces.

**Section 18 — References.**

**Appendices (A–L).** Formal TST statement and lemmas (A); G-floor formalities and tests; TTDA details and parity proofs; receipt schemas and replay traces; III.json examples; rounding/ties and repair-vector worked examples; glossary.

