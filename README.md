# The Enterprise Brain — a reference architecture

*A capability-based reference architecture for the institutional memory-and-reasoning system every
enterprise is now trying to build — designed to be **portable** across technology stacks, **trustworthy**
enough for a regulated institution, and **honestly measurable**.*

---

## Start here

**[summary.md](summary.md)** — the one-page, outcome-oriented overview (with the at-a-glance diagram).
Read this first.

## What's in here

Every organisation is building some version of an "AI brain" — a system that holds its proprietary
knowledge, retrieves the right context, and reasons over it. Most cannot answer three plain questions
about theirs: **Does it actually work? Can it be trusted in a decision that matters? Is it locked to one
vendor's stack?** This repository is the answer, in a form you can adopt, measure against, and realise on
whatever technology you already run.

It is **tech-agnostic and organisation-neutral**: capabilities and logical contracts as classes, naming
no product, platform, or organisation in the core. Architecture and evaluation are a permanent pair — the
evaluation says *what to measure*, the architecture says *what to build*, and a cross-walk proves coverage.

| Artefact | What it is |
|---|---|
| **[summary.md](summary.md)** | The one-page socialisation summary. **Start here.** |
| [logical-reference-architecture.md](logical-reference-architecture.md) | The tech-agnostic logical layer — 43 capabilities (eight groups + a cross-cutting reasoning/orchestration band), each a logical contract carrying a determinism class; the experience-flywheel cross-cutting expression; the capability ↔ eval-dimension ↔ runtime-primitive cross-walk; three rendered views. |
| [solution-example-our-stack.md](solution-example-our-stack.md) | A worked solution-architecture example — all 43 capabilities realised on one concrete stack, honest about built / partial / planned. The proof the logical layer is realisable. |
| [portability-proof.md](portability-proof.md) | The same logical layer expressed on two further public-archetype stacks (a Google-shaped cloud; an Azure-and-Snowflake-shaped cloud) — **zero logical-layer edits**. Portability demonstrated, not asserted. |
| [eval/evaluation-framework.md](eval/evaluation-framework.md) | The evaluation framework the capabilities answer to — seven groups, 41 dimensions, anchored to recognised standards. The requirements specification the architecture satisfies. |

Diagrams are authored in [d2](https://d2lang.com/) (canonical `.d2` source in `diagrams/`) and rendered to
verified SVG — a diagram is *done* when it renders, not when its source parses.

## Licence

This work is licensed under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)** —
see [LICENSE](LICENSE). Use it, adapt it, build on it; please give appropriate credit.
