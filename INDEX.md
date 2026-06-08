---
name: Enterprise Brain reference architecture — index
description: Index for the enterprise-brain reference architecture (EBRA v0.2) — a one-page socialisation summary + the tech-agnostic logical reference architecture (capability map, cross-walk, three views) + the worked solution-architecture example on our stack (built/planned honest) + the portability proof (same logical layer on multiple stacks). Public-generic, tech-agnostic. Paired with the enterprise-brain evaluation framework (the requirements) it answers.
type: index
created: 2026-06-03
valid_from: 2026-06-03
tags:
  - type/index
  - scope/architecture
  - topic/enterprise-brain
  - topic/reference-architecture
  - topic/capability-modelling
  - topic/applied-ai-systems-thesis
aliases:
  - Enterprise brain architecture index
  - EBRA index
---

# Enterprise Brain reference architecture

The reference architecture for an **enterprise brain** — the institutional memory-and-reasoning system that captures an organisation's proprietary knowledge, finds and assembles the right context, resolves trust, reasons over it, and runs resiliently, securely, lawfully, valuably, and at scale.

It is **tech-agnostic and public-generic**: capabilities, logical contracts, and quality attributes as classes — no product, platform, vendor, or organisation named. It is paired with the **enterprise-brain evaluation framework** (the requirements specification it answers) via a cross-walk that proves two-way coverage.

## Artefacts

| Artefact | What it is | Status |
|---|---|---|
| **[summary.md](summary.md)** | **The one-page socialisation summary** — outcome-oriented, human-readable, polished, public-clean. What an enterprise brain is, why a capability-based reference architecture matters (portable, trustworthy, honestly measured), and the shape at a glance (with the at-a-glance diagram). The instrument for socialising the work with architects and leaders. **Start here.** | Shareable |
| [logical-reference-architecture.md](logical-reference-architecture.md) | The logical reference architecture — eight architecture-native capability groups + a cross-cutting reasoning-and-orchestration band (43 capabilities, each a logical contract carrying a determinism class), the experience-flywheel cross-cutting expression, the capability ↔ eval-dimension ↔ runtime-primitive cross-walk (41/41 two-way coverage), and the three views (capability map; logical component + flow with inline trust gates; the two-tier-thesis expression). | Available |
| [solution-example-our-stack.md](solution-example-our-stack.md) (+ [.d2](diagrams/solution-example-our-stack.d2) / [.svg](diagrams/solution-example-our-stack.svg)) | The concrete **solution-architecture example** — all 43 logical capabilities realised on a named-technology stack (koine-memory · markdown SSOT · git · bge-m3 · BM25 · the agentic-build-cycle · the eval tiers · Restate planned), honest about what is built versus planned and reconciled cell-for-cell against the verified maturity scorecard; the worked proof the logical layer is realisable, the bridge to the eval scorecard, and the n=1 instance. Living d2 diagram (rendered to SVG). References the logical layer; never edits it. | Available |
| [portability-proof.md](portability-proof.md) (+ [.d2](diagrams/portability.d2) / [.svg](diagrams/portability.svg)) | The **portability proof** — the same 43-capability layer expressed on **two further public-archetype realisations** (Cloud-A, a Google-Cloud-shaped stack: Vertex AI Search · BigQuery · Cloud Run/Workflows · Vertex Model Registry · Dataplex; and Cloud-B, an Azure-Snowflake-shaped stack: Azure AI Search · Snowflake Cortex · Durable Functions · Azure ML registry · Snowflake Horizon/Purview) side by side with the our-stack example. Comparative capability→component table across all eight groups + the cross-cutting band (trust core, router/inventory, durable substrate, retrieval, governance, security, resilience). **SC-4 result: zero logical-layer edits** to express either archetype. One-logical-layer→N-realisations d2 diagram (rendered to SVG). Public-generic: names public products, never an organisation. | Available |

## How to read it

**To socialise it / get the shape:** start with **[summary.md](summary.md)** — the one-page,
outcome-oriented overview. **For the detail:** the [logical reference architecture](logical-reference-architecture.md)
§1 (framing) and View 1 (the capability map) — an executive or non-specialist reader can locate any
concern from there, then read its capability contract in §2 and trace it to the requirement it answers
via the cross-walk in §3.
