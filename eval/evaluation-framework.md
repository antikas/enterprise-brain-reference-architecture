---
name: Enterprise Brain Evaluation Framework
description: A capability-neutral evaluation framework for an enterprise brain, the institutional memory-and-reasoning system. Extends the popular "company brain" rubric (is-it-a-brain + is-it-auditable) to a full enterprise instrument: functional + trustworthy + resilient + secure + compliant + valuable + runnable-at-scale. Seven groups, 41 measurable dimensions (incl. the flywheel/spine additions B4, E8, and flywheel health folded into F5), each anchored to a named external standard (Google SRE, AWS Well-Architected, NIST AI RMF, ISO/IEC 42001, EU AI Act, SR 11-7 / SS1-23, DORA, OWASP LLM Top 10, MITRE ATLAS, FinOps, OTel-GenAI, ISO 30401, DAMA). Includes the n=1-vs-enterprise calibration rule and a leverage-sequenced build shortlist. The requirements specification the Enterprise Brain Reference Architecture answers.
type: research
created: 2026-06-03
valid_from: 2026-06-03
tags:
  - type/research
  - scope/architecture
  - topic/enterprise-brain
  - topic/evaluation
  - topic/enterprise-ai
aliases:
  - enterprise brain evaluation
  - enterprise brain maturity
  - beyond the 8-layer rubric
---

# Enterprise Brain Evaluation Framework

**The reframe.** The popular "company brain" model (and the common 8-layer extension of it) answers two
questions: *is it a brain?* (capture → retrieval) and *is it auditable?* (source-truth +
contradiction-safety + provenance). That is necessary and not nearly sufficient. The real question is:
**what does a fully functional, value-adding, fully resilient and compliant *enterprise* brain look
like, and what evaluation lets an organisation measure and improve its own?**

This artefact is that evaluation. It keeps the 8 layers, places them inside a larger structure, and
adds the dimensions an enterprise brain succeeds or fails in production on that the consumer model never names.

**Anchoring observation.** Applied to a small (n=1) reference instance, an honest three-role scorecard
of the original 8 layers scores around **~2.1/4**, and predicts exactly this extension. Its deepest
finding, **feedback that is documentary, not adaptive** (a written correction does not prevent the
same class of error recurring), turns out to be an *enterprise-grade value failure*, not just a
mechanism downgrade. So the upgrade is partly additive (new groups) and partly a **re-frame** of layers
already present in the consumer model.

Source-method note: synthesised from a deep-research pass over 9 enterprise dimensions, each checked
against named external standards. The consumer model was treated as useful signal, not gospel. This
file is the synthesis; it is backed by a per-dimension research corpus (held separately) recording the
named clauses, articles, metrics, and gaps for all nine. **Currency note:** US **SR 11-7 was superseded
by SR 26-2** (17 Apr 2026), which *excludes* GenAI/agentic AI, so the harder current bar for a
UK-regulated brain is **FCA-PRA SS1/23** (no carve-out) + ISO/IEC 42001; EU AI Act high-risk
obligations apply from **2 Aug 2026** (fines to 7%/3% of turnover). Where the tables below say
"SR 11-7", read "SS1/23 + ISO 42001 (SR 26-2 = US lens)".

## 1. The structure: seven questions, 41 dimensions

Each dimension carries a **headline criterion** and an **anchor standard**. Maturity is scored on a band
scale (Absent 0 / Emerging 1 / Partial 2 / Strong 3 / Exemplary 4), where *Strong requires the
mechanism verified to RUN*, not merely designed. (An honest per-capability built/partial/planned
self-assessment of one reference instance against these dimensions is the
[solution example](../solution-example-our-stack.md).)

### A. Is it a brain? *(functional core: the consumer model's first half)*
| Dim | Headline criterion | Anchor |
|---|---|---|
| A1 Capture (L1) | Raw material systematically *enters*; breadth, not scattered | DAMA-DMBOK |
| A2 Retrieval (L2) | Pulls the *right* context, measured (single-file & multi-hop), not index size | IR precision/recall; RAGAS |

### B. Is it trustworthy? *(the auditable core, the moat; survives strict audit)*
| Dim | Headline criterion | Anchor |
|---|---|---|
| B1 Source truth (L3) | A conflict is resolved by a trust rule; recency/authority wins | ISO 8000 |
| B2 Contradiction safety (L7) | A conflicting write cannot reach the store silently; held for a human regardless of confidence | (extension; NIST AI RMF "Valid & Reliable") |
| B3 Provenance in artefact (L8) | Reconstruct origin + override from the *record itself*, not a side log | W3C PROV; MITRE ATLAS provenance |
| B4 Deterministic-claim integrity | State the system acts on or presents as true is a deterministic function of observable events, not an LLM-authored claim; an LLM owning an acted-on claim is a graded defect (the [deterministic spine](../logical-reference-architecture.md)) | (extension; neuro-symbolic / deterministic-spine; NIST AI RMF "Valid & Reliable") |

### C. Is it resilient? *(does it STAY a brain under failure; MISSING from the rubric)*
| Dim | Headline criterion | Anchor |
|---|---|---|
| C1 Availability & SLO | Availability SLI/SLO for retrieval + write-back, with an error budget | **Google SRE** |
| C2 Detection (MTTD) | MTTD ≤ 7d for a silent dependency break (≤24h autonomous) | **NIST AI RMF MEASURE 2.7** |
| C3 Recovery (RTO/RPO) | Timed, dated rebuild-from-source drill + post-rebuild eval score | **AWS Well-Architected** REL13 |
| C4 Quality-drift tripwire | Golden-set re-run alerts when retrieval quality drops vs rolling baseline (the "day-9" mode) | LLM-observability drift detection |
| C5 Graceful degradation | Named modes + triggers; ≥1 built+tested (e.g. keyword fallback when the embedder is down, labelled) | NIST AI RMF MEASURE 2.6; Chaos Eng |
| C6 Fault-injection / Game Day | ≥1 dated drill breaking a dependency vs a steady-state hypothesis | **Principles of Chaos** |

### D. Is it secure under attack? *(adversarial robustness; MISSING; Permissions ≠ attack-resistance)*
| Dim | Headline criterion | Anchor |
|---|---|---|
| D1 Permissions / access (L4) | Access follows role/workflow/risk | ISO 27001 access-control |
| D2 Prompt-injection ASR | Measured indirect-injection Attack Success Rate on tool paths; <5% guarded | **OWASP LLM01**; AgentDojo; MITRE ATLAS |
| D3 Retrieval/memory poisoning | Poison-corruption rate on the golden set, trended | **OWASP LLM04/08**; PoisonedRAG |
| D4 Secrets / PII egress | Runtime egress scan of retrieval + write-back + tool payloads; target 0 | OWASP LLM02/07 |
| D5 Supply-chain attestation | % of skills/MCP servers/deps with provenance + signature/pin | OWASP LLM03; MITRE ATLAS |
| D6 Excessive-agency / tool-abuse | Least-privilege + confused-deputy test per tool | OWASP LLM06/09 |

### E. Is it compliant + governed? *(the regulator's view; MISSING; for a regulated deployment this is the gate)*
| Dim | Headline criterion | Anchor |
|---|---|---|
| E1 AI management system | Monitoring run as an audited Plan-Do-Check-Act loop with breach-triggered corrective action | **ISO/IEC 42001:2023** Cl.9→10 |
| E2 Human oversight | A named human in/on the loop at decisions that move money or expose regulated data | **EU AI Act Art. 14**; NIST GOVERN |
| E3 Audit-log completeness & reconstructability | % of decision-class answers fully reconstructable (query→chunk-versions→model/prompt→output→override) from records alone | **EU AI Act Art. 12**; SR 11-7 |
| E4 Right-to-erasure & retention | Erase a subject from source+FTS+vector+graph+caches within SLA, with proof; retention class + TTL enforced | **GDPR Art. 17 + Art. 5** |
| E5 Model inventory & independent validation | On a model inventory; dated independent validation; ongoing monitoring | **FCA-PRA SS1/23** + ISO 42001 (SR 26-2 = US lens, GenAI-excluded) |
| E6 Residency & operational resilience | Approved-jurisdiction processing; ICT incident classification/reporting; LLM-provider concentration risk | **DORA** (Reg. 2022/2554); GDPR Art. 30 |
| E7 Red-team evidence cadence | Scheduled adversarial run mapped to OWASP Top-10, logged + fed back | NIST AI RMF MEASURE 2.7 |
| E8 Cross-user promotion privacy boundary | Cross-user/cross-domain promotion (the experience flywheel's scale-3) carries only distilled, de-identified, consented signal; residual-identifier leak at the promotion boundary = 0; child-facing/regulated raises it to a hard human gate | **GDPR Art. 5/25** (minimisation, privacy-by-design); **UK Children's Code** |

### F. Does it add value + get used? *(value, adoption, trust: where most enterprise GenAI fails to deliver measurable value)*
| Dim | Headline criterion | Anchor |
|---|---|---|
| F1 Outcome / decision-quality | Measured *delta* on real decisions the brain informed vs a no-brain baseline; zero high-confidence-wrong on audit-relevant queries | DAMA "data value"; benefits-realisation |
| F2 Adoption / active-use | % of real work sessions that invoked the brain vs bypassed it; abandoned-query rate | KM "abandoned search"; ADKAR Reinforcement |
| F3 Appropriate reliance & trust calibration | On seeded correct/wrong outputs: automation-bias rate (wrong accepted) + algorithm-aversion rate (right rejected); reported-trust vs measured-reliability gap | **EU AI Act Art. 14(4)(b)/(d)**; Lee & See; TPA/TAI |
| F4 User-facing explainability | A *non-expert* can tell from the answer alone whether to act on it (distinct from auditor provenance) | EU AI Act Art. 13; HCI |
| F5 Feedback-to-improvement latency & flywheel health | Time/builds between a correction captured and it *changing a later answer*; **and** the experience flywheel's continuous health (capture completeness · promotion latency · eval-gate calibration · error-loop guard, graded *continuously*, not periodically) | (operationalises the enterprise-AI learning gap; the experience flywheel) |

### G. Can we run it at scale? *(operational viability: cost, observability, scale, lifecycle)*
| Dim | Headline criterion | Anchor |
|---|---|---|
| G1 Cost / unit economics | Cost-per-answer (tokens in+out, $) reportable; cost-per-outcome trended | **FinOps for AI** + FOCUS |
| G2 Budget enforcement (write-time) | Token/API/compute budget enforced *before* the model call; named breach action | FinOps |
| G3 Latency SLO (percentile) | TTFT p95 + E2EL p95 declared + measured (not a mean); goodput | NVIDIA NIM / SRE |
| G4 Cache effectiveness | Semantic/prefix cache hit-rate; cost/latency saved | GPT-Semantic-Cache |
| G5 Sustainability (carbon) | SCI-style energy/carbon per answer (or token→energy proxy) | **ISO/IEC 21031:2024 (SCI)** |
| G6 Observability (4 pillars) | Logs + metrics + distributed traces + **eval-in-production**; OTel-GenAI schema; SLOs alerted | **OpenTelemetry GenAI**; Google SRE; LLM-observability |
| G7 Scalability & isolation | Cross-tenant leak rate **0** (isolation by construction, non-bypassable); retrieval-quality degradation curve at 1×/10×/100×; p95 at N concurrent | data-mesh federated governance; SOC 2 CC6; ISO 27001 A.8 |
| G8 Lifecycle & freshness | Corpus-wide Freshness Score ≥85 + Coverage Drift + Stale-Retrieval-Rate, trended | **ISO 30401**; freshness scoring; DAMA Currency |
| G9 Contradiction *stock* | Full-corpus contradiction sweep; latent-contradiction count flat/falling | (a write-time gate extended periodic) |
| G10 Ontology conformance & knowledge-debt | Post-schema-change conformance %; (stale+contradictory+non-conforming+orphaned)/total <20% | "Consistent Evolution of OWL"; TDR discipline |

**Headline.** Of the 41 enterprise-grade criteria, the consumer "company brain" model scores only Groups
A and B, and even there, the trustworthy core (Group B) is the layer most deployments *forget* and a
regulator asks about *first*. The five groups the popular instrument barely scores (**C resilient · D
secure · E compliant · F valuable · G at-scale**) are where an enterprise brain actually stands or falls in production.
A typical maturity profile builds a trustworthy retrieval core and has barely begun on resilient,
secure, compliant, valuable, and at-scale.

## 2. The pattern: where brains are typically strong vs blind

Across the dimensions, the same shape recurs and is worth naming because it is the inverse of where
attention usually goes:

- **Typically strong (and under-credited):** the functional core (capture/retrieval) and, where it is
  built deliberately, the **trustworthy core** (source-truth resolution, a non-bypassable
  contradiction gate, provenance reconstructable from the record itself). These are precisely the
  layers the consumer model under-weights and a regulator weights first.
- **Typically blind (and over-credited):** the entire operational surface. **Resilience** (no SLO, no
  measured RTO, no drift tripwire, no degradation path, no Game Day) is usually unscored, a silent
  partial-failure mode with no alert. **Security** (indirect-injection ASR, retrieval poisoning,
  secrets egress) is usually *unmeasured*, and against published unguarded agentic attack-success
  baselines, "unknown" is the riskiest state for a tool-wired brain. **Compliance** (right-to-erasure,
  audit-log *coverage*, model inventory + independent validation, residency/DORA) is usually
  unaddressed. **Value + adoption** is the highest-leverage blind spot. Most instruments score the
  mechanism, not the outcome: nothing scores whether an answer was *good, fast, used, or changed a decision*,
  and without a retrieval-access log an organisation cannot even tell how often the brain is used.
  **Scale** (cross-tenant isolation, concurrency, growth-degradation) and **observability**
  (system-wide metrics/traces/alerting, and the fourth pillar, eval-in-production) round out the blind
  half.

The single sharpest instance of the value blind spot is **feedback that is documentary, not adaptive**:
a captured correction that does not change a later answer. This is the literal "learning gap" that
separates the small fraction of enterprise GenAI that delivers value from the majority that does not.
These are not missing dimensions. They are **existing layers (Feedback and Evaluation) failing their
enterprise bar.**

## 3. Build shortlist, sequenced by leverage

A generic leverage order for closing the gap. The first two dominate everything else.

1. **Green the safety contract.** A red test in the safety spine (the contradiction/write gate)
   invalidates every Group-B "Strong". Repair it first. *Hours.*
2. **Feedback activation (highest leverage overall).** Make captured corrections *retrievable and
   surfaced at the point of work*. Converts the brain from **documentary to adaptive**: the enterprise
   gate between "files corrections" and "wakes up smarter," and the literal fix for the learning gap
   (F5).
3. **The Evaluation forcing function (E1 / C2 / G6).** Schedule the macro maturity test + micro
   retrieval baseline + a liveness healthcheck as *enforced* cadence and prove the schedule fires.
   Without it every layer below is unverified, *and* it makes MTTD ≤7d true rather than designed.
4. **Extend the rubric to the missing groups:** add scored layers for **Resilience**, **Security**,
   **Compliance & governance**, **Value & adoption**, and **Scale & operability** (cost +
   observability + isolation + lifecycle), each Absent→Exemplary, plus acceptance questions that each
   use the rubric's own *"if nothing is ever refused/stopped/costed/pruned/used, the gate is
   decoration"* logic.
5. **Two cheapest unlocks, in parallel:**
   - **Retrieval-access log:** closes F2 (adoption), F1/F5 (value/latency), and turns usage from
     approximation to fact. The single highest-leverage primitive in Groups F/G.
   - **A `last_verified` field + criticality tier:** unlocks every freshness metric (G8-G10).
6. **An SLO sheet:** availability SLI/SLO for retrieval + write-back, RTO/RPO, error-budget breach
   policy. Makes Group-C targets measurable instead of implicit.
7. **A drift tripwire + a degradation breaker:** the day-9 alarm + graceful degradation (C4+C5
   evidence).
8. **Stand up an adversarial harness:** the security counterpart to the retrieval golden set:
   injection + poisoning + egress + system-prompt-extraction against the live stack; seed from
   AgentDojo + PoisonedRAG; reuse the retrieval golden set as the poisoning target; record a dated
   baseline. Adversarially re-test the contradiction gate (poison, not just honest conflict).
9. **A Decision-Quality set** (value analogue of the retrieval golden set): real past decisions with
   later-verified answers; score correctness + time-to-answer + high-confidence-wrong count. The
   instrument Group F entirely lacks, with a North-Star ("trusted provenanced answers that
   changed/confirmed a real decision per week"; counter-metric: high-confidence-wrong rate).
10. **Quarterly Game Day (C6) + full-corpus contradiction sweep (G9) + supply-chain attestation
    inventory (D5)**: the evidence-generating drills; tie to one quarterly review (forcing functions).
11. **A compliance register for any deployed instance:** model inventory + independent validation,
    DPIA/AIIA, retention classes, residency, the right-to-erasure design fork. Bites the moment a
    regulated deployment is real; declare now.
12. **Cost + carbon + p95 instrumentation** (G1/G3/G5). Lowest urgency at small scale; a hard
    compliance/ESG gap the moment the brain is multi-tenant or reported.

## 4. n=1 vs enterprise: the calibration rule *(so an instance is neither over-credited nor over-penalised)*

Several dimensions are **genuinely not-yet-needed at n=1** and should be scored **"structurally
deferred"** (declare the field/target now, defer the enforcement) rather than "Absent (failing)":

- **D1 Permissions / G7 isolation / E2 read-path oversight / cost-allocation showback (G1):** single-user.
  *The field/gate must exist now so the multi-tenant case is not a retrofit*, but grading them
  "Absent-failing" over-penalises, "Strong" over-credits. Extend the stance the rubric
  already takes for Permissions explicitly.
- **G5 Sustainability / G3 latency-percentiles:** at n=1 one human queries interactively and
  infrequently, real enterprise gates, premature here. Keep in the rubric so an enterprise instance
  cannot skip them.
- **C1 Availability SLO / C3 RTO:** declare the *targets* now (cheap discipline); the *consequence*
  (unseen consumers deciding on a brain they cannot rebuild) bites at scale, not n=1.

**Conversely, dimensions where n=1 gets NO pass** (they bite a single confident author serving a single
confident wrong answer):

- **C2 Detection · C4 drift · G8/G9 freshness + contradiction-stock · D2/D3 injection + poisoning ·
  F1/F2/F5 value + adoption + adaptive-feedback.** The day-9 silent decay, a long silent-outage
  detection gap, the documentary-not-adaptive feedback failure, and a poisoned web page the brain will
  retrieve are **live risks even in a single-user instance**, which can feel corpus drift and suffer a
  silent outage exactly as a larger one can. Grading these "deferred because n=1" is the mis-grade to
  avoid.

**The clean rule:** *failures that need many consumers to bite* → structurally deferred (declare the
field/target, defer enforcement). *Failures that bite a single confident author* → fully in scope at
n=1, graded without mercy.

## 5. Strategic read

The honest read is twofold. (1) The genuine strength of a well-built brain is the **trustworthy core
(Group B)**, exactly the layers the market forgets and a regulator asks about first; lead with it. (2)
The honest weakness is everything operational (resilience, security, compliance, value, scale), which
is the **roadmap, not an embarrassment**. For any regulated deployment, Groups **E (compliant)** and **C
(resilient)** are the gate between "interesting tool" and "auditable enterprise system."

The single highest-leverage move is **Feedback activation** (item 2 above). It is simultaneously the
deepest value gap (F5) and the missing fourth observability pillar (G6 eval-in-production). One build
closes both.

## Architecture response: the eval ⇄ architecture pair

This framework is the **requirements specification** for the enterprise brain; its answer is the
[Enterprise Brain Reference Architecture](../INDEX.md) (EBRA), a capability-based logical reference
architecture whose 43 capabilities each satisfy ≥1 dimension here, proven two-way by the cross-walk in
[logical-reference-architecture.md](../logical-reference-architecture.md) §3. The two are a **permanent
pair**: this file is EBRA's requirements; EBRA is this eval's response artefact. Extending either
obliges revisiting the other, because the cross-walk is the drift detector. (The seven groups and 41 dimensions
here are the requirement axis; EBRA's capability map is the response axis.) The three most recent
additions (**B4** deterministic-claim integrity, **E8** cross-user promotion privacy, and flywheel
health folded into **F5**) were added in lockstep with EBRA's deterministic-spine and experience-flywheel
fold; the broader operational-group rubric extension (scored layers for Resilience, Security, Compliance,
Value, and Scale) is the next increment.

## Disposition

Drives the operational-group extension of the maturity rubric (scored layers + acceptance questions
Q6-Q10). It does not duplicate the per-dimension research briefs; it positions them in the seven-group
model and supplies the n=1-vs-enterprise calibration the separate briefs could not. Re-run the maturity
test under the extended rubric at each phase boundary; the value is the per-dimension band **delta** over
time.
