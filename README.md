# The Enterprise Brain: a reference architecture

*A capability-based reference architecture for the institutional memory-and-reasoning system almost
every large enterprise is now trying to build. It is designed to be **portable** across technology
stacks, **trustworthy** enough for a regulated institution, and **honestly measurable**.*

![The enterprise brain at a glance](diagrams/summary-at-a-glance.svg)

## The problem this solves

Most organisations are building some version of an "AI brain": a system that holds proprietary
knowledge, retrieves the right context, and reasons over it. Most cannot answer three plain questions
about the one they are building: **Does it actually work? Can it be trusted in a decision that matters?
And is it locked to a single vendor's stack?**

Teams build the two easy layers (load the documents, search them) and stop. The layers that decide
whether a brain is *trustworthy*, *resilient*, *compliant*, and *valuable* are the ones that get
skipped, and they are exactly the layers a bank, an investment manager, or any regulated institution
cannot skip. This work answers those questions in a form you can adopt, measure against, and realise on
whatever technology you already run.

## At a glance

The brain answers three questions, in order. **Is it a brain?** It captures knowledge, retrieves the
right context, and assembles it for reasoning. **Is it trustworthy?** This is the moat: it resolves
which source to believe, it refuses to absorb a contradiction without a human, and every record carries
its own provenance, so an audit lives in the record rather than a side log. **Can we run it?** It stays
up under failure, resists attack, satisfies a regulator, proves its value, and runs at scale.

Underneath sits a **two-tier engine**: a general frontier model orchestrates, a router decides each
request, and an inventory of specialist models, grown on the organisation's own proprietary data, is the
durable competitive asset.

Two runtime properties make it more than a search box. The **experience flywheel**: every interaction
is a learning event (*capture, distil, eval-gate, promote, improve*), so the brain gets better the more
it is used, and that compounding is hard for a competitor to replicate quickly, because the advantage is
the accumulated interactions, not the mechanism. The **deterministic spine**: anything the brain records
or presents *as true* must follow from a rule over observable evidence, never a model's guess, so it
does not confabulate the facts it acts on.

## Why it matters

- **Portable, not vendor-locked.** Because the logical layer names no product, the *same* architecture
  is realised on different stacks (our own, a Google-shaped cloud, an Azure-and-Snowflake-shaped cloud)
  with zero changes to the architecture itself. An organisation maps its existing technology onto the
  capabilities; it does not rebuild to a vendor's blueprint. The portability proof shows this on
  multiple stacks rather than claiming it.
- **Trustworthy by design.** The two layers most "AI brain" models forget are the two a regulated
  institution asks about first: a **contradiction-safe gate** (four-eyes / maker-checker rendered into
  the memory itself, so a confident model cannot silently corrupt the brain) and **provenance in the
  record** (lineage and human-override carried in the artefact, audit-by-design), underpinned by a
  **deterministic spine** that records as true only what a rule derives from evidence. All three are
  first-class layers here, given the same weight as capture and retrieval.
- **Honestly measured.** Every capability is graded against the evaluation framework, so a team can see
  exactly what is built, what is partial, and what is still a roadmap, and watch the maturity rise only
  on genuine progress.
- **Grounded in a clear thesis.** The engine is a frontier orchestrator plus an inventory of specialist
  models accumulated patiently on proprietary data, and the experience flywheel turns that inventory
  into a *compounding* asset. The architecture makes that thesis buildable rather than leaving it as a
  slide.

## The artefacts

| Artefact | What it is |
|---|---|
| [logical-reference-architecture.md](logical-reference-architecture.md) | The tech-agnostic logical layer: 43 capabilities (eight groups plus a cross-cutting reasoning/orchestration band), each a logical contract carrying a determinism class; the experience-flywheel cross-cutting expression; the capability ↔ eval-dimension ↔ runtime-primitive cross-walk; three rendered views. |
| [solution-example-our-stack.md](solution-example-our-stack.md) | A worked solution-architecture example: all 43 capabilities realised on one concrete stack, honest about built / partial / planned. The proof the logical layer is realisable. |
| [portability-proof.md](portability-proof.md) | The same logical layer expressed on two further public-archetype stacks (a Google-shaped cloud; an Azure-and-Snowflake-shaped cloud), with **zero logical-layer edits**. |
| [eval/evaluation-framework.md](eval/evaluation-framework.md) | The evaluation framework the capabilities answer to: seven groups, 41 dimensions, anchored to recognised standards. The requirements specification the architecture satisfies. |

## Licence

This work is licensed under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**;
see [LICENSE](LICENSE). Use it, adapt it, build on it, with appropriate credit.
