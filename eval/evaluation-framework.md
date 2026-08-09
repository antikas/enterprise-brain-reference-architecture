---
name: Enterprise Brain Evaluation Framework
description: Requirements and evidence for assessing the function, trust, resilience, security, governance, value, and operation of an enterprise brain.
type: research
tags:
  - type/research
  - scope/architecture
  - topic/enterprise-brain
  - topic/evaluation
  - topic/enterprise-ai
aliases:
  - enterprise brain evaluation
  - enterprise brain maturity
---

# Enterprise Brain Evaluation Framework

An enterprise brain needs more than capture and retrieval. It must also preserve authority, survive failure, resist attack, meet its legal duties, improve decisions, and operate at enterprise scale.

This framework defines the requirements and the evidence used to assess them. The [logical reference architecture](../logical-reference-architecture.md) assigns each requirement to one owning capability.

Each requirement has an external anchor where established work exists. The anchors include standards, regulations, supervisory guidance, research instruments, and bodies of practice.

Use the version of each regulation or supervisory instrument that applies to the deployment date and jurisdiction. Official sources include [SR 26-2](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm), the [EU AI Act](https://eur-lex.europa.eu/eli/reg/2024/1689/oj), and its [amending regulation](https://eur-lex.europa.eu/eli/reg/2026/1744/oj).

## Scoring

Score each requirement on the following scale:

| Score | Meaning |
|---|---|
| 0 Absent | The mechanism and its evidence are missing. |
| 1 Emerging | A design or partial mechanism exists. |
| 2 Partial | The mechanism works for part of the required scope. |
| 3 Strong | The mechanism works across the required scope and has current exercise evidence. |
| 4 Exemplary | The mechanism has sustained evidence, measured improvement, and independent challenge. |

A design alone can reach Emerging. Strong requires evidence from a running system or a representative exercise.

The identifiers L1-L8 show the matching layer in the common company brain rubric. L0 belongs to the architecture and names the approved knowledge source of truth.

## A. Core function

| Requirement | Criterion | Anchor |
|---|---|---|
| A1 Capture (L1) | Source material enters through an enumerable process and carries provenance from capture. | DAMA-DMBOK |
| A2 Retrieval (L2) | Fixed tests measure retrieval of the right evidence for direct and multi-step questions. | Information retrieval precision and recall; RAGAS |
| A3 Structural understanding | Repeated evidence produces stable algorithmic structure. Narration stays within cited evidence. Serving status controls use. | ISO 30401:2018; NIST AI RMF MEASURE |
| A4 Enterprise integration and mastering | Governed source reach produces one enterprise entity view, conformant products, current paths, and queryable lineage. | DAMA-DMBOK2 Revised; ISO 8000-61:2016 |

## B. Trust

| Requirement | Criterion | Anchor |
|---|---|---|
| B1 Source truth (L3) | Declared authority and recency rules resolve conflicting facts. | ISO 8000 |
| B2 Contradiction safety (L7) | A conflicting claim enters a human review queue with the current claim preserved. | NIST AI RMF Valid and Reliable |
| B3 Provenance in the record (L8) | The record carries enough origin and override data to reconstruct its history. | W3C PROV; MITRE ATLAS |
| B4 Deterministic claim integrity | Rules over observable events produce the state used or presented as true. | Neuro-symbolic systems; NIST AI RMF Valid and Reliable; deterministic spine |

## C. Resilience

| Requirement | Criterion | Anchor |
|---|---|---|
| C1 Availability and service objectives | Retrieval and write paths have service indicators, objectives, error budgets, and breach action. | Google SRE |
| C2 Failure detection | Every critical dependency has a measured maximum detection time. | NIST AI RMF MEASURE 2.7 |
| C3 Recovery | A timed recovery exercise meets declared recovery time and recovery point objectives. Post-recovery evaluation confirms service quality. | AWS Well-Architected REL13 |
| C4 Quality drift | A fixed evaluation set detects regression against a rolling baseline. | Model observability practice |
| C5 Degraded service | Declared service modes have triggers, allowed functions, user messages, and exit conditions. At least one mode has exercise evidence. | NIST AI RMF MEASURE 2.6; chaos engineering |
| C6 Failure rehearsal | A dated exercise breaks a dependency and tests a stated steady state. | Principles of Chaos |
| C7 Durable agent execution | Work resumes after process loss with approvals and effect settlement intact. Recovery follows the effect's idempotency class. | Google SRE recovery practice; NIST SP 800-53 AU |

## D. Security

| Requirement | Criterion | Anchor |
|---|---|---|
| D1 Access control (L4) | Access follows verified identity, role, workflow, purpose, and risk. | ISO/IEC 27001 access control |
| D2 Prompt injection | Tool paths have a measured attack success rate under indirect injection tests. | OWASP LLM01; AgentDojo; MITRE ATLAS |
| D3 Retrieval and memory poisoning | Fixed tests measure the effect of planted material on retrieval and answers. | OWASP LLM04 and LLM08; PoisonedRAG |
| D4 Sensitive data egress | Runtime checks cover retrieved content, write-back, files, messages, and tool payloads. | OWASP LLM02 and LLM07 |
| D5 Supply chain | Loaded skills, tool servers, models, and dependencies carry verified provenance and a signature or pin. | OWASP LLM03; MITRE ATLAS |
| D6 Tool agency | Each tool uses scoped authority and passes a confused deputy test. | OWASP LLM06 |

## E. Governance and compliance

| Requirement | Criterion | Anchor |
|---|---|---|
| E1 AI management system | Objectives, monitoring, review, and corrective action form an audited management loop. | ISO/IEC 42001:2023 clauses 9 and 10 |
| E2 Human oversight | Named people make the decisions required for money movement, protected data, claim admission, and irreversible action. | EU AI Act Article 14; NIST AI RMF GOVERN |
| E3 Decision reconstruction | Records reconstruct the request, evidence versions, policy, model, prompt, output, release, and override. | EU AI Act Article 12; SR 26-2; PRA SS1/23 |
| E4 Erasure and retention | Subject data is removed from authoritative stores, indexes, graphs, caches, release payloads, and exports within the stated service objective. | GDPR Articles 5 and 17 |
| E5 Model inventory and validation | Models have inventory records, independent validation, use conditions, monitoring, and revalidation triggers. | PRA SS1/23; ISO/IEC 42001 |
| E6 Residency and operational resilience | Processing follows approved jurisdictions. Incidents follow the required classification and reporting process. Provider concentration has tested controls. | DORA; GDPR Article 30 |
| E7 Adversarial review | Scheduled exercises map to recognised attack classes, record findings, and track corrective action. | NIST AI RMF MEASURE 2.7 |
| E8 Cross-user promotion | Shared learning uses distilled, de-identified, consented data. Tests measure residual identifiers at the promotion boundary. | GDPR Articles 5 and 25; UK Children's Code |
| E9 Information release | Every external answer uses one release path after classification and the required verdicts. The release record exists before output begins. | NIST SP 800-207; GDPR Articles 5, 6, and 25 |

## F. Value and use

| Requirement | Criterion | Anchor |
|---|---|---|
| F1 Decision quality | Outcome measures compare assisted decisions with a suitable baseline. Audit-relevant tests track high-confidence errors. | DAMA data value; benefits realisation |
| F2 Adoption | Measures cover active use, bypass, abandonment, repeat use, and task completion. | Knowledge management abandoned search; ADKAR Reinforcement |
| F3 Appropriate reliance | Seeded tests measure acceptance of wrong answers and rejection of correct answers. Reported trust is compared with observed reliability. | EU AI Act Article 14; Lee and See; trust instruments |
| F4 User explanation | A person can identify the evidence, confidence, limits, and conditions that would change the answer. | EU AI Act Article 13; human-computer interaction |
| F5 Feedback and improvement | Measures track capture, promotion time, gate accuracy, repeated errors, and the time until a correction changes a later answer. | Experience flywheel |

## G. Operation at scale

| Requirement | Criterion | Anchor |
|---|---|---|
| G1 Unit cost | Cost per answer and cost per outcome are available by service and use case. | FinOps for AI; FOCUS |
| G2 Budget control | Token, API, and compute budgets are checked before work begins. Each breach has a declared action. | FinOps |
| G3 Latency | Time to first output and complete response use percentile objectives. Useful throughput is also measured. | Google SRE latency practice; inference benchmarking |
| G4 Cache value | Caches report hit rate, cost saved, latency saved, and invalidation accuracy. | Semantic caching research |
| G5 Sustainability | Energy or carbon per answer is measured directly or through a declared proxy. | ISO/IEC 21031:2024 |
| G6 Observability | Logs, metrics, traces, and live answer evaluation share identifiers and alert against service objectives. | OpenTelemetry GenAI; Google SRE |
| G7 Scale and isolation | Tests cover cross-boundary leakage, retrieval quality under growth, and percentile latency under concurrency. | Data mesh governance; SOC 2 CC6; ISO/IEC 27001 Annex A.8 |
| G8 Knowledge freshness | Measures cover the whole corpus, materiality-based age limits, and stale retrieval. | ISO 30401; DAMA Currency |
| G9 Contradiction stock | A full corpus sweep measures latent contradictions and tracks their trend. | Deterministic spine extension |
| G10 Ontology conformance and knowledge debt | Schema changes have impact measures, migration evidence, and a current view of stale, conflicting, invalid, and orphaned knowledge. | Consistent Evolution of OWL; technical debt register practice |

## Anchor terms

### Standards and specifications

- **ISO 30401:2018** sets requirements for knowledge management systems.
- **ISO 8000** covers data quality. ISO 8000-61:2016 defines a data quality management process model.
- **ISO/IEC 42001:2023** defines an AI management system.
- **ISO/IEC 27001:2022** defines an information security management system and its controls.
- **ISO/IEC 21031:2024** defines Software Carbon Intensity.
- **W3C PROV** defines a data model for provenance.
- **OpenTelemetry GenAI** defines telemetry conventions for generative AI systems.
- **FOCUS** defines a common format for cloud cost and usage data.
- **SOC 2 CC6** covers logical and physical access controls.

### Regulation and supervisory guidance

- **EU AI Act** means Regulation (EU) 2024/1689 and applicable amendments.
- **GDPR** means Regulation (EU) 2016/679.
- **DORA** means Regulation (EU) 2022/2554.
- **UK Children's Code** means the Age Appropriate Design Code from the Information Commissioner's Office.
- **PRA SS1/23** gives UK supervisory expectations for model risk management in banks.
- **SR 26-2** gives current US Federal Reserve guidance on model risk management. It supersedes SR 11-7.

### Frameworks and bodies of practice

- **NIST AI RMF** covers GOVERN, MAP, MEASURE, and MANAGE activities for AI risk.
- **NIST SP 800-207** defines Zero Trust Architecture.
- **NIST SP 800-53** defines security and privacy controls. Its AU family covers audit and accountability.
- **OWASP Top 10 for LLM Applications** lists common risks in model-based applications.
- **MITRE ATLAS** records adversary tactics and techniques for AI systems.
- **AWS Well-Architected REL13** covers disaster recovery planning.
- **Google SRE** supplies service objectives, error budgets, recovery, and reliability practice.
- **Principles of Chaos** defines the core practice for controlled failure experiments.
- **FinOps** supplies methods for cost allocation, budgeting, and unit economics.
- **DAMA-DMBOK** supplies established data management concepts and controls.
- **Information retrieval precision and recall** measure result relevance and coverage.
- **RAGAS** provides measures for retrieval and answer evaluation.
- **AgentDojo** provides prompt injection tests for tool-using agents.
- **PoisonedRAG** describes retrieval corpus poisoning attacks.
- **ADKAR** supplies a change model whose final element is reinforcement.
- **Lee and See** defines appropriate reliance on automation.

The deterministic spine and the experience flywheel are defined in the [Lexikon](https://antikas.io/writing/lexikon/) and applied in the [logical reference architecture](../logical-reference-architecture.md).

## Detailed evidence and hard failures

Some requirements depend on the form of their evidence. The sections below define that evidence and the conditions that fail the requirement.

### A3 Structural understanding

| Evidence | Hard failures |
|---|---|
| Fixed multi-record fixtures; stable signatures and groups on repeated runs; complete evidence links; scope isolation tests; entailment checks; sampled human labels; serving status tests; erasure and rebuild tests. | A model chooses group membership; narration adds an unsupported claim; identity changes on stable evidence; scope data leaks; held or retired observations serve; erased material returns after rebuild. |

Consequential use also requires a persisted oversight verdict. Recalculation and ordinary serving use the algorithmic and serving status controls.

### A4 Enterprise integration and mastering

| Evidence | Hard failures |
|---|---|
| Shared entity fixtures across sources and unit scopes; realistic duplicates; review queue volume; field survivorship records; build and query lineage; materialisation stamps; reconciliation; stale refusal; source invalidation; contract promotion; live conformance. | Duplicate unit masters; automatic uncertain merges; missing review volume; operational facts in recall; missing lineage; reconstructed lineage; stale service; active service after source invalidation; draft contracts driving consequential work. |

The evidence must cover source allocation, entity resolution, survivorship, lineage, product generation, freshness, reconciliation, and contract promotion.

### C7 Durable agent execution

| Evidence | Hard failures |
|---|---|
| Task ordering; intent persisted before effects; results persisted before output; durable streamed deltas; approval and settlement recovery; idempotency fixtures; uncertain effect reconciliation; journal and compaction comparison; erasure and tombstone propagation. | Output precedes its record; approval state exists only in process memory; uncertain effects repeat without inspection; compaction replaces the journal; replay claims exact model output; erased content returns through recovery or export. |

### E9 Information release

| Evidence | Hard failures |
|---|---|
| Surface registry; classification cases; access, purpose, lawful basis, minimisation, and query policy tests; relational and non-relational reads; persist-before-stream tests; refusal records; unknown surface tests; expiry, erasure, recovery, and export tests. | External output bypasses release; output begins before its record; a protected release lacks a required verdict; expired authority passes; unknown surfaces receive output; release and workflow records disagree; erased content returns. |

## Scale calibration

Some requirements need several consumers or an enterprise service level before their full enforcement can be tested. The contract and target still need to exist from the first deployment.

The following requirements can defer full enforcement while the system has one consumer:

- D1 live access separation and G7 cross-user isolation.
- E2 oversight for ordinary read decisions.
- G1 cost allocation across teams.
- G3 percentile latency and G5 sustainability as service gates.
- C1 availability objectives and the timing target in C3 recovery.

The following requirements apply to the first consumer:

- Failure detection, quality drift, freshness, and contradiction stock.
- Prompt injection, retrieval poisoning, and sensitive data egress.
- Structural understanding, durable work, and governed release.
- Decision quality, adoption, reliance, explanation, and feedback.
- Entity mastering once the system reaches a second source.

Record a deferred requirement with its contract, target, trigger for enforcement, and current evidence. Score the mechanism that can be exercised at the current size.

## Architecture mapping

This framework owns the requirements. The [logical reference architecture](../logical-reference-architecture.md) owns the capability response.

The cross-walk in the logical architecture gives each requirement one owning capability and records any supporting capabilities. A change to either side requires a cross-walk check.
