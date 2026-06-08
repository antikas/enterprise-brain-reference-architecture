---
name: The Enterprise Brain — a reference architecture (summary)
description: The one-page socialisation summary of the Enterprise Brain Reference Architecture — outcome-oriented, human-readable, public-clean. What an enterprise brain is, why a capability-based reference architecture matters (portable, trustworthy, honestly measured), and the shape at a glance. The instrument for socialising the work with architects and leaders. Full detail in the logical + solution + portability artefacts.
type: summary
status: shareable
created: 2026-06-03
valid_from: 2026-06-03
tags:
  - type/summary
  - scope/architecture
  - topic/enterprise-brain
  - topic/reference-architecture
aliases:
  - enterprise brain summary
  - EBRA at a glance
  - enterprise brain one-pager
---

# The Enterprise Brain — a reference architecture

*A capability-based reference architecture for the institutional memory-and-reasoning system every
enterprise is now trying to build — designed to be portable across technology stacks, trustworthy
enough for a regulated institution, and honestly measurable.*

---

## The problem this solves

Every organisation is building some version of an "AI brain" — a system that holds its proprietary
knowledge, retrieves the right context, and reasons over it. Most cannot answer three plain questions
about the one they are building: **Does it actually work? Can it be trusted in a decision that matters?
And is it locked to a single vendor's stack?**

The reason is that teams build the two easy layers (load the documents, search them) and stop. The
layers that decide whether a brain is *trustworthy*, *resilient*, *compliant*, and *valuable* are the
ones that get skipped — and they are exactly the layers a bank, an investment manager, or any regulated
institution cannot skip.

This work is the answer to those questions, in a form you can adopt, measure against, and realise on
whatever technology you already run.

---

## What it is

Two paired artefacts, plus the test that grades them:

- **A logical reference architecture** — *what an enterprise brain must be able to do*, expressed as a
  map of capabilities with a clear contract for each, and **naming no product or vendor**. It is the
  invariant: the part that stays the same no matter whose technology realises it.
- **A worked solution example** — *how those capabilities are realised on one concrete stack*, with an
  honest "built / partial / planned" status for each, so the architecture doubles as a maturity
  picture rather than a wish-list.
- **An evaluation framework** — the *requirements* the capabilities answer to. Architecture and
  evaluation are a permanent pair: the evaluation says what to measure, the architecture says what to
  build, and a cross-walk between them is the instrument that proves coverage and catches drift.

---

## At a glance

![The enterprise brain at a glance](diagrams/summary-at-a-glance.svg)

The brain answers three questions, in order. **Is it a brain?** — it captures knowledge, retrieves the
right context, and assembles it for reasoning. **Is it trustworthy?** — this is the moat: it resolves
which source to believe, it refuses to absorb a contradiction without a human, and every record carries
its own provenance, so an audit lives in the record rather than a side log. **Can we run it?** — it
stays up under failure, resists attack, satisfies a regulator, proves its value, and runs at scale.

Underneath sits a **two-tier engine**: a general frontier model orchestrates, a router decides each
request, and an inventory of specialist models — grown on the organisation's own proprietary data — is
the durable competitive asset.

Two runtime properties make it more than a search box. The **experience flywheel** — every interaction
is a learning event (*capture → distil → eval-gate → promote → improve*), so the brain gets better the
more it is used, and that compounding is something a competitor cannot copy because they did not have
the interactions. The **deterministic spine** — anything the brain records or presents *as true* must
follow from a rule over observable evidence, never a model's guess, so it does not confabulate the facts
it acts on. The flywheel makes it improve; the spine keeps it honest.

---

## Why it matters — the four outcomes

- **Portable, not vendor-locked.** Because the logical layer names no product, the *same* architecture
  is realised on different stacks — our own, a Google-shaped cloud, an Azure-and-Snowflake-shaped cloud
  — **with zero changes to the architecture itself**. An organisation maps its existing technology onto
  the capabilities; it does not rebuild to a vendor's blueprint. This portability is demonstrated, not
  asserted.
- **Trustworthy by design.** The two layers most "AI brain" models forget are the two a regulated
  institution asks about first: a **contradiction-safe gate** (four-eyes / maker-checker rendered into
  the memory itself — a confident model cannot silently corrupt the brain) and **provenance in the
  record** (lineage and human-override carried in the artefact, audit-by-design, not a log that can
  drift) — underpinned by a **deterministic spine** that lets the brain record as true only what a rule derives from evidence, so it cannot confabulate a fact it then acts on. These are first-class layers here, not footnotes.
- **Honestly measured.** Every capability is graded against the evaluation framework, so a team can see
  exactly what is built, what is partial, and what is still a roadmap — and watch the maturity rise only
  on genuine progress. No vanity green.
- **Grounded in a clear thesis.** The engine is a frontier orchestrator plus a patiently-accumulated
  inventory of specialist models on proprietary data — and the **experience flywheel** turns that
  inventory into a *compounding* asset: every interaction is a learning event, so the moat widens with
  use. The architecture makes that thesis visible and buildable, rather than leaving it as a slide.

---

## How to use it

It gives architects and leaders a **shared language** for "what is our AI brain, and is it any good?" —
and a **test** to answer it. Put the three questions to any system you run today; map your stack onto the
capability layer; grade yourself honestly against the evaluation; and use the gaps as the roadmap. It
applies across organisations precisely because it names no vendor — the logical layer is the common
reference, and each environment supplies its own realisation.

---

## Where the detail lives

- **Logical reference architecture** (the capability map + contracts + the three views): [logical-reference-architecture.md](logical-reference-architecture.md)
- **Solution example** (capabilities → concrete components, built/planned honest): [solution-example-our-stack.md](solution-example-our-stack.md)
- **Portability proof** (the same logical layer on multiple stacks): [portability-proof.md](portability-proof.md)
- **Index:** [INDEX.md](INDEX.md)

*This page is the summary; the artefacts above carry the detail. It names no organisation and no
confidential information — it is the shareable form.*
