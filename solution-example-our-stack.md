---
name: "Enterprise Brain: solution-architecture example on our stack"
description: The concrete reference implementation of the tech-agnostic enterprise-brain logical reference architecture on one named stack (koine-memory, markdown SSOT, git, bge-m3, BM25, the agentic-build-cycle, the eval tiers, Restate planned). Maps all 43 logical capabilities to real components, BUILT/PARTIAL/PLANNED honest and reconciled cell-for-cell against the verified maturity scorecard, including the experience flywheel mapped to its BUILT/PARTIAL components and where the three determinism departures (retrieval, trained, generative) physically live on the stack. Includes a living solution diagram (rendered d2 to SVG) and doubles as the realisability proof plus the n=1 maturity instance. Public-generic; names products, never organisations.
type: solution-architecture
created: 2026-06-03
valid_from: 2026-06-03
tags:
  - type/solution-architecture
  - scope/architecture
  - topic/enterprise-brain
  - topic/reference-architecture
  - topic/applied-ai-systems-thesis
  - topic/diagrams-as-code
aliases:
  - Enterprise brain solution example
  - EBRA solution architecture
  - Enterprise brain reference implementation
  - Solution example our stack
---

# Enterprise Brain: solution-architecture example (our stack)

## 1. Framing

This is the **concrete solution-architecture example** for the [enterprise-brain logical reference architecture](logical-reference-architecture.md). The logical layer names *what an enterprise brain must be able to do*: forty-three capabilities, each a logical contract, naming no product. This document is one substitutable proof that the logical layer is realisable. It takes that same forty-three-capability map and **maps every capability to a real, named component on one concrete stack, ours.**

It does three jobs at once:

1. **The realisability proof (anti-abstraction).** If every logical capability maps to a real component, built or credibly planned with a named intended component, then the logical layer is not a paper abstraction. The mapping table in §2 is that proof, capability by capability.
2. **The n=1 instance.** This stack is itself a running enterprise brain at single-author scale, the n=1 reference instance. The count of capabilities that are **BUILT and passing** is the honest current maturity of that instance, not an aspiration.
3. **The bridge to the eval scorecard.** Every BUILT claim here is **reconciled cell-for-cell against the verified maturity scorecard** (the three-role blind-audit run). Where the scorecard grades a layer Partial or Emerging, the component is PARTIAL or PLANNED, never an optimistic BUILT. That reconciliation is what keeps this honest rather than a wish-list.

**The stack, named.** The reasoning channel is Claude Code and Claude Desktop over a **frontier orchestrator** (Claude, deliberately never fine-tuned, so it stays swappable). The memory-and-retrieval substrate is **koine-memory** (parser → chunker → extractor → indexer; **bge-m3** embeddings into a **sqlite-vec** vector store, a **BM25** FTS store, a graph store, and a provenance store; a hybrid retriever with rerank, query-expansion, an intent classifier/gate/router, and a two-layer composition + retrieval **policy engine**). The corpus is **markdown SSOT** (≈830 files with YAML frontmatter) under **git**. The trust spine is the **contradiction gate** (`guarded_write_back` + `policy/contradiction.py`) and the **write-back human gate** (`/memory-writeback`). The build discipline is the **agentic-build-cycle** (three-role separation, blind re-audit). The eval substrate is three tiers: **ground-truth** retrieval eval, the **company-brain maturity** scorecard, and the **activation** eval. The **specialist inventory** and the **Restate** durable-execution substrate are PLANNED for the vault (Restate is the named intended durable substrate, already adopted in sibling solutions per their ADRs).

**Org-specific mappings are held separately.** This document maps the logical layer onto *this* stack only. A different organisation realising the same logical layer on its own technology (its own cloud, its own model providers, its own stores) holds that as a **separate, private** solution-architecture artefact. It is not written here, and it does not edit the logical layer (see §5).

> **Diagram convention (living-architecture discipline):** the §3 solution diagram is authored in **d2** and **rendered to SVG** via the pinned binary. A diagram is done when it *renders*, not when its source parses. **Solid = BUILT** (reconciled against the verified scorecard). **Dashed = PLANNED** (contract declared, component not built).

---

## 2. The capability → component mapping

Every one of the forty-three logical capabilities, by ID and name, mapped to the concrete component(s) on this stack, with an honest **BUILT / PARTIAL / PLANNED** status. The status column is reconciled against the verified maturity scorecard: where the scorecard grades the owning layer below Strong, the status is held down to PARTIAL or PLANNED regardless of how complete the component *looks*.

**Status key.** **BUILT** = exists, works, and (where the scorecard covers it) is verified at Strong. **PARTIAL** = real component exists but a load-bearing piece is unimplemented or the scorecard grades it Partial/Emerging. **PLANNED** = contract declared, named intended component, not yet built (typically a structurally-deferred-at-n=1 capability).

### G1: Knowledge Ingress & Lifecycle

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-G1.1 | Capture proprietary knowledge | Markdown SSOT + YAML frontmatter under git; `/capture`, `/ingest-source`, `/vault-compile` skills; koine-memory indexer | **PARTIAL:** capture is documented but under-enforced (scorecard: Capture = Partial); provenance-at-capture exists in-record but ingress is not yet breadth-systematic |
| C-G1.2 | Maintain corpus freshness | `valid_from` / bi-temporal frontmatter; vault-lint STUB/DRAFT-rot check | **PARTIAL:** last-verified vs last-edited distinction declared in the ontology, but corpus-wide freshness/coverage-drift is not yet a trended figure |
| C-G1.3 | Sweep contradiction stock | `policy/contradiction.py` conflict logic, applied corpus-wide | **PLANNED:** the write-time conflict policy is BUILT; the periodic full-corpus *sweep* for latent stock is not yet scheduled |
| C-G1.4 | Conform to ontology under evolution | `ontology/` (types · relations · rules); index-coverage pre-commit hook | **PARTIAL:** schema is declared and validated; pre-change impact count + post-change conformance rate are not yet computed automatically |
| C-G1.5 | Govern knowledge lifecycle | Archive-not-delete convention; `/memory-writeback` human gate; supersession frontmatter | **PARTIAL:** supersession + archival are real and provenance-bearing, but the enforced scheduled lifecycle loop and the trended knowledge-debt ratio are not yet running |

### G2: Retrieval & Context Composition

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-G2.1 | Retrieve relevant context | koine-memory hybrid retrieval (`query` + `graph_retrieval` + `hybrid_scorer` + `rerank` + `query_expansion` over sqlite-vec + BM25 + graph); ground-truth eval | **BUILT:** scorecard: Retrieval = Strong; blends semantic + lexical + relational, measured on a fixed question set (single-fact + multi-hop), mechanically real and tested |
| C-G2.2 | Compose context for reasoning | `composition_engine` + L3A composition policy + token budget | **BUILT:** deterministic, budgeted, named slots; part of the Strong retrieval layer (the access filter it *should* honour is the PARTIAL piece, owned by C-G4.1) |

### G3: Trust & Provenance (the moat)

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-G3.1 | Resolve source of truth | `decay_scorer` (recency nudge) + authority/source fields; trust rule | **PARTIAL:** scorecard: Source-truth = Partial; `valid_from` autofill is **unimplemented**, so most files lack the recency anchor and decay fires on ~1-2% of queries as a soft nudge, not "recency wins by rule" |
| C-G3.2 | Hold contradiction-unsafe writes | `guarded_write_back` (sole gated write path) + `policy/contradiction.py` | **BUILT:** scorecard: Contradiction-safety = Strong; gate is structurally non-bypassable (private executor, sole gated entry, behavioural contract test passes, real held writes; the override branch is itself gated) |
| C-G3.3 | Bind provenance into the record | In-record `provenance` + `contradiction_override` frontmatter blocks; code stamps unconditionally | **BUILT:** scorecard: Provenance = Strong; blocks are materially present in the real written files and stamped unconditionally; origin + override + validity reconstructable from the artefact alone |

### GX: Reasoning & Orchestration (cross-cutting, the two-tier thesis)

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-X1 | Orchestrate and route reasoning | Claude (frontier orchestrator) + the intent `classifier` / `gate` / `router`; routing reason recorded | **PARTIAL:** frontier-only routing is honest and BUILT at n=1 (the intent router exists); the *multi-tier* specialist-vs-frontier router is structurally deferred (the routing interface + escalation contract are declared, the second tier is not built) |
| C-X2 | Maintain the specialist inventory | Model/corpus/eval card schema + eval-before-deploy gate (the discipline); small models tuned on corpus slices | **PLANNED:** the moat is an *accumulated* asset (frontier-first is the honest n=1 stance); the cards schema + blind-eval-before-deploy gate are declared now, the populated inventory is later-stage |

### G4: Security & Access Control

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-G4.1 | Mediate access by need-to-know | `retrieval_filter` + per-agent access-scope declarations | **PARTIAL:** scorecard: Permissions = Emerging; `filter_candidates` is a **stub** (returns a trace, applies no scope filter; candidate mutation deferred to Phase 7); access scope is declared-only |
| C-G4.2 | Resist prompt injection | Untrusted-content handling on retrieval/tool paths; adversarial harness (planned suite) | **PLANNED:** treated-as-attacker-controlled is the design stance, but a measured guarded-vs-unguarded attack-success rate is not yet run |
| C-G4.3 | Resist knowledge poisoning | The contradiction gate under *adversarial* (not just honest) writes; poison test set | **PLANNED:** the gate (C-G3.2) is BUILT against honest conflict; stress-testing it against malicious writes + a poison-retrieval rate is not yet done |
| C-G4.4 | Contain sensitive-data egress | sanitisation scanner (pre-commit deny-list); runtime egress scan + privacy gate | **PARTIAL:** commit-boundary deny-list scanner is BUILT; runtime egress scanning across retrieval outputs + write artefacts + tool payloads (with a planted-secret leak rate) is not yet in place |
| C-G4.5 | Attest the supply chain | Skill / tool-server / dependency inventory; signature/pin signals | **PLANNED:** extensions are loaded without a tracked provenance/attestation proportion; the tamper-evident registry is a light declare-now |
| C-G4.6 | Constrain tool agency | Tool gateway + least-privilege + confused-deputy check per tool | **PLANNED:** tool calls are not yet uniformly gateway-checked with a per-tool confused-deputy test and a tool-abuse attack-success rate |
| C-G4.7 | Exercise adversarial assurance | Scheduled adversarial harness mapped to the attack-category taxonomy | **PLANNED:** no scheduled adversarial scorecard yet (supplies the suites for C-G4.2/.3/.4) |

### G5: Governance & Compliance

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-G5.1 | Operate the AI management system | The maturity scorecard + healthcheck + lint as monitoring signals; breach→corrective-action policy | **PARTIAL:** scorecard: Evaluation = Emerging; signals exist and a halt-on-breach norm is declared, but there is **no enforced cadence** (no scheduled task fires the loop), so it fails its own forcing-function bar |
| C-G5.2 | Assure human oversight | `/memory-writeback` approve/reject gate on the write path | **BUILT** (write-path): the maker-checker gate on contradiction-held writes is real and exercised; read-path decision oversight + automation-bias measurement are PLANNED (the mixed-band split is honest) |
| C-G5.3 | Reconstruct the decision record | In-record provenance (C-G3.3) + git history; decision-class taxonomy | **PARTIAL:** write-path reconstruction is strong; the **retrieval/read-path access log** does not yet exist, so audit-completeness coverage is not yet measured |
| C-G5.4 | Enforce erasure and retention | Archive-not-delete + retention-class frontmatter; multi-store erasure across source + vectors + bm25 + graph + caches | **PLANNED:** archive-not-delete is in real tension with storage-limitation today; propagated, provable multi-store erasure within an SLA is not yet built |
| C-G5.5 | Validate the brain as a model | The three-role blind-audit (validator role separate from builder); model/specialist inventory | **PARTIAL:** independent blind verification is BUILT *as a discipline* (the verified scorecard is exactly this); the formal risk-tiered model inventory with dated re-validation triggers is declare-now |
| C-G5.6 | Honour residency and op-resilience obligations | Residency policy + incident runbook + third-party/provider register (single-model-provider concentration) | **PLANNED:** these bind an organisation, not a private instance; runbook/register/jurisdiction declared so a regulated instance is not a retrofit |
| C-G5.7 | Bound cross-user promotion by consent and de-identification | `/operational-data-mine` propose-only pipe (privacy-gated, provenance) is the *distil→propose* arc; consent record + de-identification gate on cross-user promotion | **PLANNED:** single-learner today (the flywheel's cross-user scale is structurally deferred); the propose-only mining pipe exists, but the cross-user consent/de-identification boundary with a measured residual-identifier leak rate is not yet built |

### G6: Runtime & Operations

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-G6.1 | Meet service-level objectives | Availability indicators for retrieve + write; error-budget policy | **PLANNED:** targets declarable now; the consequence (unseen consumers) bites at scale, structurally deferred at n=1 |
| C-G6.2 | Detect silent failure | koine-memory healthcheck (weekly Scheduled Task running a real query, the embedder smoke test); `last-status.txt` OK/FAIL | **BUILT:** a firing-cadence tripwire on the critical embedder dependency, recording OK/FAIL (built precisely because a ~5-week silent embedder break had previously sat undetected) |
| C-G6.3 | Recover from store | Rebuild-from-markdown-SSOT (`cli rebuild`); derived indexes rebuildable from the authoritative corpus | **PARTIAL:** rebuild-from-source is real and run; a *dated, timed* drill with a verified post-rebuild eval score (RT/RP proof) is not yet recorded |
| C-G6.4 | Detect quality drift | Ground-truth golden set re-run vs a rolling baseline | **PARTIAL:** the golden set + macro maturity run exist, but the scheduled drift re-run with a regression alert is not yet automated (ties to the Evaluation = Emerging cadence gap) |
| C-G6.5 | Degrade gracefully | Named degraded-mode catalogue (lexical-only when embedder down; read-only; refuse-and-say-so) | **PLANNED:** the healthcheck *detects* the embedder break; the named-mode transition with a labelled degraded answer is not yet wired |
| C-G6.6 | Rehearse failure | Engineered fault-injection drill (break embedder / corrupt index / stall write queue) | **PLANNED:** no dated fault-injection drill against a steady-state hypothesis yet |
| C-G6.7 | Account for unit cost and budget | Token/API budget enforced before the call; cost-per-answer capture; breach action | **PARTIAL:** runaway-spend awareness bites a single author and is partly handled at the harness level; a pre-call enforced budget with a recorded breach event + queryable cost-per-answer is not yet a first-class component |
| C-G6.8 | Meet latency objectives | Per-request percentile latency (TTFT / end-to-end) + goodput | **PLANNED:** structurally deferred at n=1 (one human, infrequent interactive queries); an enterprise gate kept so an enterprise instance cannot skip it |
| C-G6.9 | Exploit caching | Prefix / semantic cache with a measured hit-rate | **PLANNED:** prompt-caching is used at the orchestrator level in sibling solutions; a measured-hit-rate cache layer for the vault brain is deferred (pays off under repetitive multi-user load) |
| C-G6.10 | Account for sustainability | Energy/carbon-per-answer figure (token→energy proxy) | **PLANNED:** structurally deferred at n=1; an enterprise/ESG gate kept in the map |
| C-G6.11 | Observe the running system | git history + run logs + eval results; the **eval-in-production** pillar via the activation eval | **PARTIAL:** logs/metrics/traces are thin and the read-path access log is missing, but the most-often-missing fourth pillar (eval-in-production) is real via the activation eval, so the layer is partly BUILT where it matters most at n=1 |
| C-G6.12 | Scale with tenant isolation | Per-tenant isolation model (dedicated or pooled-with-engine-filter); zero cross-tenant leak by construction | **PLANNED:** single-user today; the isolation-by-construction gate is a design property declared now so multi-tenant is not bolted on |

### G7: Value & Feedback

| ID | Capability | Component(s) on our stack | Status |
|---|---|---|---|
| C-G7.1 | Measure decision quality | Within-subject decision-quality substitute + a high-confidence-wrong counter; North-Star (provenanced answers that changed a real decision) | **PARTIAL:** the counter-metric discipline bites at n=1 and is tracked qualitatively; the instrumented delta vs a no-brain baseline (counterfactual) is not yet a measured figure |
| C-G7.2 | Instrument adoption | A retrieval-access log (queries → results → use); invoked-vs-bypassed + abandoned-query rate | **PLANNED:** the keystone retrieval-access log does **not yet exist** (its absence is why C-G7.1/.5 and the read-path of C-G5.3 are unmeasurable); named and prioritised |
| C-G7.3 | Calibrate appropriate reliance | Seeded right/wrong outputs + two-step decide-cold→consult→revise protocol; trust self-report | **PLANNED:** the reliance protocol is not yet run (over-/under-reliance rates + reported-vs-measured trust gap) |
| C-G7.4 | Explain to the acting user | Answer + trust/uncertainty signals a non-expert can act on; a contest path | **PARTIAL:** answers carry trust signals (provenance/heat) the author uses, but a blind comprehension test + a recorded contest path are not yet exercised |
| C-G7.5 | Close the feedback-to-improvement loop | Activation eval (`eval/activation`, activate-rate / follow-rate) + pre-dispatch recall ritual surfacing learnings during a build | **BUILT** (at build-cycle grain): the activation eval just shipped and the pre-dispatch recall ritual surfaces the right learning at the right moment; this is the fix to the scorecard's deepest finding (Feedback was *documentary, not adaptive*, graded Partial, because nothing queried learnings during a build). The build-cycle-grain loop is BUILT; the corpus-wide measured feedback-to-improvement latency is the PARTIAL remainder |

### 2a. The experience flywheel on our stack (evidence, not aspiration)

The logical layer expresses the experience flywheel as one always-on loop (*capture → distil → eval-gate → promote → improve*). On this stack the loop's mechanism is **substantially BUILT**, which is what lets the solution example show it as evidence rather than a plan. Each stage maps to a real component with an honest status:

| Flywheel stage | Component(s) on our stack | Status |
|---|---|---|
| **capture** | In-record `provenance` frontmatter + git history (the proprietary record); the retrieval-access log keystone (`C-G7.2`) is still PLANNED | **PARTIAL:** provenance-complete capture of *written* artefacts is BUILT; the interaction/access log that would make capture complete is PLANNED |
| **distil** | `/operational-data-mine` (`mine_paideia_audit.py`) mines a running solution's `audit.db` into **propose-only** candidate learnings, privacy-gated, with provenance | **BUILT:** the distil→propose pipe exists and runs (the one concrete operational-data → vault-learning pipe) |
| **eval-gate** | The **activation eval** (`eval/activation`, activate-/follow-rate, held-out) + the ground-truth and maturity tiers as the held-out gate | **PARTIAL/BUILT:** the activation eval is BUILT; a calibrated held-out gate *on promotions specifically* is the discipline being hardened |
| **promote** | `guarded_write_back` contradiction gate (sole, non-bypassable write path) + `/memory-writeback` human gate; cross-user de-identification (`C-G5.7`) PLANNED | **BUILT** (same-user, contradiction-safe + human-gated); cross-user promotion PLANNED |
| **improve** | The pre-dispatch recall ritual surfaces promoted learnings *during a build* (`C-G7.5`); the specialist inventory (`C-X2`) is the PLANNED inventory-form improvement | **BUILT** at build-cycle grain; inventory-form PLANNED |
| *promotion discipline* | The **agentic-build-cycle** (three-role separation: builder ≠ blind-verifier ≠ adjudicator) applied to runtime learning | **BUILT** as a discipline (this very document was three-role blind-verified) |
| *contradiction-safety* | The Phase-6 contradiction gate (`policy/contradiction.py`) holds a conflicting promotion for a human | **BUILT** |

The honest reading: *capture everything, promote nothing unaudited* is realised today for the **single-learner / same-user** scales, and the distil→eval-gate→promote→improve arc is built end-to-end at build-cycle grain. The **cross-user scale** (and its consent/de-identification boundary, `C-G5.7`) is the PLANNED remainder, the flywheel's next turn, deferred until the brain has a population.

### 2b. Where the three determinism departures live on this stack

The per-capability determinism classification is owned by the [logical layer](logical-reference-architecture.md) (40 of 43 capabilities are `deterministic-claim`); this document does not duplicate it. What it adds is *where the three deliberate departures physically sit* on our stack, the concrete proof that the spine dominates and the model is admitted only surgically:

- **`retrieval` (`C-G2.1`):** the koine-memory hybrid retriever (sqlite-vec + BM25 + graph + rerank). The one place statistical surfacing is the right tool.
- **`trained` (`C-X2`):** the PLANNED specialist inventory (small models tuned on corpus slices). The trained layer is declared, not yet populated (frontier-first at n=1).
- **`generative` (`C-G7.4`):** the Claude frontier orchestrator and the user-facing explanation. Everything the system *records or acts on as true* stays on the deterministic spine; the LLM generates and judges, gated and audited, never the author of a recorded claim.

---

## 3. The living solution diagram

The SOLUTION/runtime view of this stack: real, named components and real topology. Authored in d2 and **rendered to SVG via the pinned d2 binary** (`d2 --layout elk`); a diagram is done when it renders, not when its source parses. **Solid = BUILT** (reconciled against the verified scorecard); **dashed = PLANNED**.

![Solution architecture on our stack: markdown SSOT ingress feeds koine-memory (index → bge-m3 embed → vectors/BM25/graph/provenance stores → hybrid retrieve → intent → compose), the composed context goes to the frontier orchestrator (Claude) and a PLANNED specialist inventory, the write-back path passes through the non-bypassable contradiction gate and the write-back human gate, all grown from the corpus and graded by the three eval tiers, with healthcheck/lint/sanitisation forcing functions and a PLANNED Restate durable substrate](diagrams/solution-example-our-stack.svg)

*Source (canonical):* [diagrams/solution-example-our-stack.d2](diagrams/solution-example-our-stack.d2), rendered to the SVG above via the pinned d2 binary (v0.6.9, `--layout elk`) per the living-solution-architecture discipline. The diagram is *done* when it renders, not when its source parses.

*Legend.* The trust gates are real components: the **contradiction gate** (`guarded_write_back` + `policy/contradiction.py`) is the sole, non-bypassable write path; the **write-back human gate** (`/memory-writeback`) adjudicates held writes. **Access mediation** (`retrieval_filter`) is dashed because it is PARTIAL (annotate-only, candidate filtering is Phase 7). The **specialist inventory** and **Restate** durable substrate are dashed (PLANNED for the vault). The three eval tiers (ground-truth, maturity, activation) grade retrieval, the brain, and learning-activation respectively; the **enforced eval cadence** is dashed because no scheduler fires it yet.

---

## 4. How it doubles as proof

The mapping table answers the central claim of the logical layer: *state a capability once, logically, and any enterprise can stand up its own realisation against it.* Here is the realisation, and it is complete:

- **Coverage.** All **43/43** logical capabilities map to a named component. No capability is a paper abstraction with no realisation path: a not-yet-built capability is PLANNED *with a named intended component*, not a blank. That completeness is the anti-abstraction proof: the logical layer is realisable.
- **The n=1 maturity is the BUILT-and-passing count, honestly.** The 43 capabilities map to **7 BUILT · 17 PARTIAL · 19 PLANNED**. The 7 BUILT (and, where the scorecard covers them, verified at Strong): retrieval (C-G2.1), composition (C-G2.2), the contradiction gate (C-G3.2), in-record provenance (C-G3.3), silent-failure detection (C-G6.2), the write-path human gate (C-G5.2, BUILT on the write path, its read-path half PLANNED), and the feedback-activation loop (C-G7.5, BUILT at build-cycle grain, its corpus-wide measured-latency half PARTIAL). The strongest of these are the two the consumer model omits entirely (contradiction-safety and provenance), the load-bearing result, and both survive strict blind audit.
- **The honest distribution.** The 17 PARTIAL are the capabilities carried by *discipline without a forcing function* (source-truth enforcement, permissions execution, evaluation cadence, the read-path access log, freshness/lifecycle trending): they look more complete than they are, and the scorecard reconciliation is what catches the gap. The 19 PLANNED are the capabilities that need many consumers (or an adversarial cadence) to bite (multi-tier routing, the specialist inventory, tenant isolation, latency/caching/sustainability, residency, the cross-user promotion boundary `C-G5.7`, and the security-assurance suite): each declared as a gate or contract now, so none is a retrofit.

**Reconciled against the verified scorecard, not asserted.** Three reconciliations show the discipline biting:

1. **C-G3.2 contradiction-safe write = BUILT.** The gate is structurally non-bypassable and the behavioural contract test passes; the scorecard holds it at Strong. (A brittle string-order *test* assertion is red after the override branch was added, a test defect, not a gate defect, so the component is BUILT, with the test repair tracked separately.)
2. **C-G3.1 source-of-truth = PARTIAL, marked *down* from a tempting BUILT.** A `decay_scorer` exists and the trust rule is articulated, so it looks built. But `valid_from` autofill is unimplemented, so most files lack the recency anchor and decay is a ~1-2%-of-queries soft nudge, not "recency wins by rule". The scorecard grades it Partial; so it is PARTIAL here.
3. **C-G7.5 feedback loop = BUILT at build-cycle grain, marked *up* honestly, but bounded.** The scorecard graded the Feedback layer *down* (Strong→Partial) because the loop was documentary, not adaptive: nothing queried learnings during a build, so a same-class failure recurred after it was written down. The activation eval + pre-dispatch recall ritual is exactly the fix, and it has shipped, so the build-cycle-grain loop is genuinely BUILT. The corpus-wide *measured* feedback-to-improvement latency remains the PARTIAL remainder, and it depends on the still-PLANNED retrieval-access log (C-G7.2). Claiming the whole layer BUILT would be the optimistic-BUILT error; claiming none of it would deny the shipped activation eval.

---

## 5. Second-environment note

This mapping is one realisation, not the only one. A different enterprise reads the same [logical reference architecture](logical-reference-architecture.md) and stands up its **own** capability→component mapping against the identical forty-three-capability layer (on its own cloud, its own model providers, its own stores, its own durable substrate) without changing a word of the logical layer. That second mapping is a **separate, private** solution-architecture artefact: it lives with that organisation, names its products, and references the logical layer the same way this one does. Portability is demonstrated the moment a second mapping is expressible without editing the logical core; this document is the first such mapping, and it is deliberately the public, product-named-but-organisation-free one.

---

*Paired with:* the [logical reference architecture](logical-reference-architecture.md) (the tech-agnostic layer this realises) and an independently verified maturity scorecard (the requirements-conformance evidence the BUILT claims are reconciled against). It is the enterprise-brain reference implementation, the n=1 instance.
