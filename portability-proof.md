---
name: Enterprise Brain portability proof
description: "The portability proof for the tech-agnostic enterprise-brain logical reference architecture. Demonstrates that the 43-capability logical layer is portable by expressing two further substitutable realisations, Cloud-A (a Google-Cloud-shaped stack) and Cloud-B (an Azure-Snowflake-shaped stack), alongside the our-stack solution example, with a comparative capability-to-component mapping across all eight groups plus the cross-cutting band. The portability conclusion (SC-4) records whether the logical layer needed any edit to express either archetype. It did not. Public-generic: names public products, never an organisation or client."
type: portability-proof
created: 2026-06-03
valid_from: 2026-06-03
tags:
  - type/portability-proof
  - scope/architecture
  - topic/enterprise-brain
  - topic/reference-architecture
  - topic/applied-ai-systems-thesis
  - topic/diagrams-as-code
aliases:
  - Enterprise brain portability proof
  - EBRA portability proof
  - Portability proof our stack Cloud-A Cloud-B
---

# Enterprise Brain: portability proof

## 1. What this proves, and how

The [logical reference architecture](logical-reference-architecture.md) makes a load-bearing claim: it names **what an enterprise brain must be able to do** (forty-three capabilities, each a logical contract) and names **no product, platform, vendor, or organisation**, so that *any* organisation can realise it on whatever technology it already runs. A concrete realisation on one named stack is a *substitutable* artefact that links to the logical layer and never edits it. The [our-stack solution example](solution-example-our-stack.md) is the first such realisation.

That document, on its own, proves the logical layer is **realisable** (every capability maps to a real component). It does not, on its own, prove the logical layer is **portable**, because a single mapping could have been quietly written *to* the stack that already existed. Portability is a stronger property, and it has a precise test:

> **Portability is demonstrated the moment a *second* realisation is expressible on a *different* stack without editing a single word of the logical layer.** A third realisation makes the point conclusively.

The portability proof below is that demonstration. It takes the same forty-three-capability layer and expresses **two further realisations** on deliberately different technology shapes, side by side with the our-stack one:

- **Cloud-A, a Google-Cloud-shaped stack.** Vertex AI Search for retrieval, BigQuery as the warehouse, Cloud Run plus Cloud Workflows for serverless and durable execution, Vertex Model Registry for the specialist inventory, Dataplex for governance and lineage.
- **Cloud-B, an Azure-Snowflake-shaped stack.** Azure AI Search for retrieval, Snowflake (Cortex) as the warehouse and reasoning surface, Azure Durable Functions for durable execution, Azure ML model registry for the specialist inventory, Snowflake Horizon plus Microsoft Purview for governance and lineage.

These are *archetypes*, named by their technology shape, not by any organisation that runs them. Naming the public clouds and their products is allowed and necessary, because it is what makes the realisations concrete. Naming an employer or client is not, and this document names none. (Two **private** downstream mappings, one organisation onto a Google stack and one onto an Azure/Snowflake stack, exist as separate artefacts in their own private folders; they apply this public reference architecture to specific contexts and are deliberately held apart from it.)

> **Status convention.** This is a *portability* proof, not a maturity proof. The our-stack column carries the honest BUILT/PARTIAL/PLANNED status from the [solution example](solution-example-our-stack.md) (reconciled against the verified scorecard). The Cloud-A and Cloud-B columns name the **intended component** that would honour each capability's contract; they are *expressibility* claims (the contract is realisable on that stack with a named product), not maturity claims about a system anyone has built. That is exactly the right grain for a portability proof: the question is *"can the logical contract be honoured on this stack?"*, not *"has someone already built it?"*

## 2. The comparative mapping

Every one of the forty-three capabilities is portable, and expressing all forty-three as a three-column table would be unwieldy. So the table below carries a **representative, high-signal subset that covers every group**, all eight capability groups plus the cross-cutting band, and deliberately includes the load-bearing capabilities the proof must not skip: the **trust core** (G3), the **cross-cutting router and inventory** (GX), the **durable substrate**, **retrieval** (G2), **governance** (G5), **security** (G4), and **resilience/operations** (G6). Each row reads: **logical capability → our-stack realisation | Cloud-A (Google-shaped) | Cloud-B (Azure-Snowflake-shaped)**. Public product names only.

### G1: Knowledge Ingress and Lifecycle

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **C-G1.1** Capture proprietary knowledge | Markdown SSOT + YAML frontmatter under git; capture/ingest skills; koine-memory indexer *(PARTIAL)* | Document AI + Cloud Storage landing + Pub/Sub ingest; provenance metadata in BigQuery; Dataplex catalogues the source classification | Azure Data Factory / Event Grid ingest into ADLS Gen2; Snowflake external tables + streams; Purview captures classification and lineage at ingress |
| **C-G1.2** Maintain corpus freshness | Bi-temporal frontmatter; vault-lint rot check *(PARTIAL)* | BigQuery scheduled query over per-artefact `last_verified` + criticality tier; Dataplex data-freshness profiling | Snowflake task computing a corpus-wide freshness/coverage-drift figure; Horizon data-quality monitors |
| **C-G1.5** Govern knowledge lifecycle | Archive-not-delete; write-back human gate; supersession frontmatter *(PARTIAL)* | Cloud Workflows scheduled lifecycle loop; archive/supersede/re-verify actions gated by a human approval step (Cloud Tasks queue); knowledge-debt ratio in Looker | Snowflake task-driven lifecycle loop; time-travel + retention policies for reversible-by-record supersession; debt ratio surfaced in Power BI |

### G2: Retrieval and Context Composition

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **C-G2.1** Retrieve relevant context | koine-memory hybrid retrieval (sqlite-vec + BM25 + graph) + rerank; ground-truth eval *(BUILT)* | **Vertex AI Search** (semantic + keyword hybrid, built-in reranker) over BigQuery + Vertex Vector Search; relational signal via a graph in Spanner; quality on a fixed eval set | **Azure AI Search** (vector + BM25 hybrid + semantic reranker) over a Snowflake Cortex Search index; relational signal via a graph store; quality on a fixed eval set |
| **C-G2.2** Compose context for reasoning | `composition_engine` + L3A policy + token budget *(BUILT)* | A composition service on Cloud Run assembling named slots within a token budget, trust-flagged content labelled | An Azure Function (or Snowflake Cortex prompt template) assembling named, budgeted slots with conflict flags labelled |

### G3: Trust and Provenance

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **C-G3.1** Resolve source of truth | `decay_scorer` + authority/source fields; trust rule *(PARTIAL)* | Trust rule as a BigQuery resolution view keyed on validity-time + authority; superseded rows retained and marked | Trust rule as a Snowflake view/stored procedure over validity-time + authority columns; superseded rows retained and flagged |
| **C-G3.2** Hold contradiction-unsafe writes *(maker-checker in the memory layer)* | `guarded_write_back` (sole gated write path) + `policy/contradiction.py` *(BUILT)* | The **only** write path is a Cloud Run service that runs the conflict policy and routes a conflict to a human-adjudication queue (Cloud Tasks); confidence buys no bypass; override recorded | The **only** write path is a Durable Functions orchestration running the conflict check; a conflict is held for human approval; override recorded. Non-bypassable by construction (no direct table writes granted) |
| **C-G3.3** Bind provenance into the record | In-record provenance + override frontmatter; stamped unconditionally *(BUILT)* | Provenance + override bound *in-row* in BigQuery (not a side audit table); stamped unconditionally by the write service | Provenance + override bound *in-row* in Snowflake; immutable history via time-travel + streams; stamped unconditionally |

### GX: Reasoning and Orchestration *(cross-cutting, the two-tier thesis)*

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **C-X1** Orchestrate and route reasoning *(hybrid router)* | Claude (frontier) + intent classifier/gate/router *(PARTIAL: frontier-only at n=1)* | A router on Cloud Run / Vertex AI Agent Builder that defaults to a Vertex-hosted specialist where one fits and escalates to a frontier model (Gemini, or any swappable frontier) on novel/low-confidence requests; routing reason logged | A router (Azure AI Foundry agent / Durable Functions) defaulting to a registered specialist and escalating to a frontier model via Azure OpenAI / Snowflake Cortex; the frontier tier stays swappable, never fine-tuned; routing reason logged |
| **C-X2** Maintain the specialist inventory | Model/corpus/eval card schema + eval-before-deploy gate *(PLANNED)* | **Vertex Model Registry** holds specialists tuned on corpus slices (Vertex tuning); each carries model/corpus/eval cards; promotion gated on a clean blind eval vs the frontier baseline; retired by router-policy update | **Azure ML model registry** holds specialists (or Snowflake Cortex fine-tuned models); model/corpus/eval cards attached; eval-before-deploy gate; retirement on frontier overtake |

### G4: Security and Access Control

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **C-G4.1** Mediate access by need-to-know | `retrieval_filter` + per-agent access scope *(PARTIAL: filter is a stub)* | IAM + VPC-SC; BigQuery row/column-level security and Vertex AI Search ACL filters applied *before* results return; identity from a verified Google identity token, never user-supplied | Microsoft Entra ID + Snowflake row-access policies / dynamic data masking; Azure AI Search security trimming applied pre-return; identity from a verified Entra token |
| **C-G4.4** Contain sensitive-data egress | Sanitisation scanner (commit deny-list); runtime egress scan *(PARTIAL)* | Cloud DLP scanning retrieval outputs, write artefacts, and tool payloads at runtime; planted-secret leak rate measured; redact/block on hit | Microsoft Purview DLP + Presidio scanning the same three egress surfaces at runtime; leak rate measured against a planted-secret set |
| **C-G4.6** Constrain tool agency *(confused-deputy)* | Tool gateway + least-privilege + per-tool check *(PLANNED)* | Tools invoked through an Apigee / API Gateway policy point under least-privilege service accounts; confused-deputy test per tool; no tool callable without a gateway check | Tools invoked through Azure API Management under least-privilege managed identities; per-tool confused-deputy test; gateway check mandatory |
| **C-G4.7** Exercise adversarial assurance | Scheduled adversarial harness mapped to attack taxonomy *(PLANNED)* | Cloud Scheduler firing a Cloud Run adversarial harness (injection + poisoning + egress + extraction); dated scorecard into Security Command Center | Azure Logic Apps / scheduled pipeline firing an adversarial harness; dated scorecard into Microsoft Defender / Sentinel |

### G5: Governance and Compliance

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **C-G5.1** Operate the AI management system *(audited PDCA loop)* | Maturity scorecard + healthcheck + lint as signals; breach→corrective-action *(PARTIAL: no enforced cadence)* | Cloud Scheduler-driven monitoring loop; breach thresholds in Cloud Monitoring trigger a corrective-action workflow that pre-empts feature work; recorded in an audit log | Azure Monitor + scheduled pipeline driving the PDCA loop; alert-triggered corrective-action runbook (Azure Automation) with priority over growth work |
| **C-G5.3** Reconstruct the decision record *(read-path logged too)* | In-record provenance + git history; read-path access log missing *(PARTIAL)* | Both read and write paths logged to Cloud Logging / BigQuery; audit-completeness coverage measured; an evidence pack producible per decision | Both paths logged to Azure Monitor / a Snowflake audit schema; coverage measured; evidence pack producible per decision |
| **C-G5.4** Enforce erasure and retention *(across every store)* | Archive-not-delete + retention frontmatter; multi-store erasure *(PLANNED)* | Erasure propagated across BigQuery, Vertex Vector Search, the lexical index, the graph, and caches within an SLA, with re-query-empty proof; retention classes via BigQuery TTL / Dataplex policy | Erasure propagated across Snowflake, the vector index, Azure AI Search, the graph, and caches; Snowflake retention + Purview policy enforce class/TTL; provable erasure |
| **C-G5.5** Validate the brain as a model *(independent validation)* | Three-role blind audit (validator ≠ builder); model inventory *(PARTIAL)* | Risk-tiered model inventory in Vertex Model Registry + Model Cards; dated independent validation by a separate team; re-validation triggers via Vertex Model Monitoring | Risk-tiered inventory in Azure ML registry + responsible-AI dashboards; independent validation by a separate team; re-validation triggers on drift |
| **C-G5.6** Honour residency and operational-resilience obligations | Residency policy + incident runbook + provider register *(PLANNED)* | Processing pinned to approved Google Cloud regions (region/Assured Workloads); incident classification on the regulatory clock; provider-concentration register (single-model-provider risk) | Processing pinned to approved Azure regions + Snowflake region selection; incident runbook on the regulatory clock; provider-concentration register |
| **C-G5.7** Bound cross-user promotion by consent and de-identification *(the flywheel's cross-user boundary)* | Operational-data-mine propose-only pipe + privacy gate *(PLANNED: cross-user scale deferred)* | A promotion gate on Cloud Workflows that de-identifies via Cloud DLP and checks a consent record in BigQuery before any cross-user promotion; residual-identifier leak rate measured | A Durable Functions promotion gate de-identifying via Purview / Presidio and checking consent records in Snowflake before cross-user promotion; residual-identifier leak rate measured |

### G6: Runtime and Operations *(incl. the durable substrate)*

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **Durable-execution substrate** *(underpins C-X1, C-G6.3, C-G6.6)* | Restate (PLANNED for the vault; in production in sibling solutions) | **Cloud Workflows** (+ Cloud Tasks / Eventarc) for replayable, failure-surviving multi-step reasoning | **Azure Durable Functions** orchestrations (durable, replayable, checkpointed) |
| **C-G6.2** Detect silent failure | koine-memory healthcheck (weekly real-query embedder smoke test) *(BUILT)* | Cloud Monitoring uptime checks + a scheduled real-query probe per critical dependency (embedder, index, model); FAIL is visible, bounded time-to-detect | Azure Monitor availability tests + a scheduled real-query probe; FAIL surfaced, bounded time-to-detect |
| **C-G6.3** Recover from store *(rebuild from source-of-truth)* | Rebuild-from-markdown-SSOT (`cli rebuild`); derived indexes rebuildable *(PARTIAL)* | Rebuild all derived indexes (Vertex Vector Search, lexical, graph) from the authoritative BigQuery / Cloud Storage source; dated timed drill + post-rebuild eval | Rebuild all derived indexes from authoritative Snowflake (time-travel / zero-copy clone) + ADLS source; dated timed drill + post-rebuild eval |
| **C-G6.5** Degrade gracefully *(named modes)* | Named degraded-mode catalogue *(PLANNED)* | Named modes (lexical-only when the embedder is down; read-only; refuse-and-say-so) selected by the Cloud Run service on a healthcheck trigger; degraded answer labelled | Named modes selected by the Durable Functions orchestrator on a health signal; degraded answer labelled; never silently fails open |
| **C-G6.11** Observe the running system *(four pillars incl. eval-in-production)* | git history + run logs + eval results; eval-in-production via activation eval *(PARTIAL)* | Cloud Logging + Cloud Monitoring + Cloud Trace + an eval-in-production stream (scheduled golden-set re-run); alert on objective breach | Azure Monitor (logs + metrics) + Application Insights traces + an eval-in-production stream; alert on objective breach |
| **C-G6.12** Scale with tenant isolation *(zero cross-tenant leak by construction)* | Per-tenant isolation model; zero-leak by construction *(PLANNED)* | Isolation by construction via per-tenant datasets / VPC-SC perimeters or pooled-with-row-level-filter on a verified server-side tenant claim; leak rate zero; degradation curve characterised | Isolation via Snowflake per-tenant databases or row-access policies + Azure AI Search index-per-tenant, on a verified Entra tenant claim; leak rate zero; degradation curve characterised |

### G7: Value and Feedback

| Capability | Our stack (status) | Cloud-A, Google-shaped | Cloud-B, Azure-Snowflake-shaped |
|---|---|---|---|
| **C-G7.2** Instrument adoption *(the keystone retrieval-access log)* | Retrieval-access log *(PLANNED: its absence blocks C-G7.1/.5 and the C-G5.3 read-path)* | A retrieval-access log in BigQuery (query → results → use); invoked-vs-bypassed + abandoned-query rate in Looker | A retrieval-access log in a Snowflake table; invoked-vs-bypassed + abandoned-query rate in Power BI |
| **C-G7.5** Close the feedback-to-improvement loop | Activation eval + pre-dispatch recall ritual *(BUILT at build-cycle grain)* | Captured corrections re-train a Vertex specialist (the adaptive-in-inventory form) and/or are surfaced at the next same-class request; feedback-to-improvement latency measured | Captured corrections re-train an Azure ML / Cortex specialist and/or are surfaced at the next same-class request; latency measured |

## 3. The portability conclusion (SC-4)

> **SC-4 result: the logical layer required ZERO edits to express either Cloud-A or Cloud-B.**

Every one of the forty-three capabilities, and every capability in the representative subset above, across all eight groups and the cross-cutting band, was expressible on a Google-Cloud-shaped stack and on an Azure-Snowflake-shaped stack **without changing a single word of the logical reference architecture.** The logical layer is the invariant; the three columns are three substitutable realisations of it. No capability's logical contract had to be relaxed, re-scoped, or rewritten to fit either archetype. That is the portability claim, and it is now demonstrated three ways (our stack, Cloud-A, Cloud-B), not asserted.

The reason it holds is structural, and it is exactly the discipline §6 of the logical layer enforces:

- **Contracts are invariants, realised many ways.** *"A write that conflicts with trusted memory must not land silently, regardless of model confidence"* (C-G3.2) is honoured by a private executor + contradiction policy on our stack, by a sole-write-path Cloud Run service routing to a human queue on Cloud-A, and by a Durable Functions orchestration on Cloud-B. Three technologies, one invariant. The contract never mentioned any of them.
- **Quality attributes are classes, not numbers.** Because the logical layer says *availability class* and *latency class* rather than "99.9%", each archetype sets its own targets (Cloud Monitoring SLOs on Cloud-A; Azure Monitor SLOs on Cloud-B) without the logical layer needing a different number per stack.
- **The trust core and the two-tier spine are technology-neutral by design.** The moat (the contradiction-safe write gate C-G3.2, in-record provenance C-G3.3, the specialist inventory C-X2) and the hybrid router (C-X1) are described as *contracts on the reasoning and memory layers*, so they map onto a managed model registry + serverless write service on either cloud just as they map onto koine-memory locally.

### Controlled SC-4 observations (no exceptions raised)

The discipline requires that any capability which *could not* be realised on an archetype without changing its logical contract be surfaced as a controlled SC-4 exception, not papered over. **No such exception arose.** All forty-three contracts mapped cleanly to both archetypes. Two honest observations are worth recording, because they are where a careless mapping would have tried to bend the contract, and the contract held instead:

1. **The hybrid router (C-X1) and specialist inventory (C-X2) are *structurally deferred at n=1*, not unportable.** On both Cloud-A and Cloud-B the contract is expressible today (Vertex Model Registry / Azure ML registry + a routing service), even though no archetype has a *populated* inventory yet. The logical layer already bands these as deferred-at-n=1; the cloud columns express the *contract and intended component*, which is precisely the portability question. No edit needed.
2. **Cloud-B blends two vendors (Azure + Snowflake) for one stack.** This is a stress case for portability, a realisation that is not a single vendor's reference stack, and every capability still mapped (e.g. retrieval splits across Azure AI Search and Snowflake Cortex Search; governance splits across Snowflake Horizon and Microsoft Purview). That a *multi-vendor* archetype maps with zero logical edits is a harder test than a single-vendor stack, and it passed.

The conclusion stands: **one logical layer, three realisations, zero logical-layer edits.** Portability is proven, not claimed.

## 4. One logical layer, N realisations

![Portability: one tech-agnostic logical reference architecture (43 capabilities, no product or organisation named) realised by three substitutable stacks: our stack (koine-memory, the n=1 instance), Cloud-A (a Google-Cloud-shaped stack: Vertex AI Search, BigQuery, Cloud Run/Workflows, Vertex Model Registry, Dataplex) and Cloud-B (an Azure-Snowflake-shaped stack: Azure AI Search, Snowflake Cortex, Durable Functions, Azure ML registry, Snowflake Horizon/Purview), and extensible to any further realisation N, each realised with zero edits to the logical layer](diagrams/portability.svg)

*Source (canonical):* [diagrams/portability.d2](diagrams/portability.d2), rendered to the SVG above via the pinned d2 binary (v0.6.9, `--layout elk`) per the render-diagrams-to-verify discipline. A diagram is done when it *renders*, not when its source parses.

*Legend.* The single shaded node on the left is the **logical reference architecture** (the invariant). Each dashed edge points to a **substitutable realisation**: our stack (the n=1 instance), Cloud-A, Cloud-B, and an open "...realisation N". Every edge is labelled *realised by (zero logical edits)*, which is the whole claim: the layer fans out to N stacks without itself changing.

## 5. Where this sits

This is the third artefact in the enterprise-brain reference-architecture set, and it closes the portability claim the first two opened:

- The [logical reference architecture](logical-reference-architecture.md) states the invariant (§6: "portability is demonstrated the moment a second mapping is expressible without changing a word of this layer").
- The [our-stack solution example](solution-example-our-stack.md) is the first realisation and the realisability proof (§5: a second realisation is a separate, private artefact that does not edit the logical layer).
- **This document** expresses the second and third realisations on public archetypes and records the SC-4 result: zero logical-layer edits. It is public-generic, naming public products, never an organisation.

Two **private** downstream mappings apply this reference architecture to specific organisational contexts (one on a Google-shaped stack, one on an Azure-Snowflake-shaped stack). They live in their own private project folders, name their context, and reference this public layer the same way the our-stack example does. They are *applications* of the reference architecture, not part of it, and they are held entirely apart from each other.

*Registered in the [enterprise-brain INDEX](INDEX.md).*
