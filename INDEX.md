---
name: "Enterprise Brain reference architecture: index"
description: Navigation for the Enterprise Brain reference architecture, its solution examples, diagrams, and evaluation framework.
type: index
tags:
  - type/index
  - scope/architecture
  - topic/enterprise-brain
  - topic/reference-architecture
  - topic/capability-modelling
aliases:
  - Enterprise brain architecture index
  - EBRA index
---

# Enterprise Brain reference architecture

An **enterprise brain** gives people and software governed access to an organisation's knowledge. It captures knowledge, finds evidence, supports reasoning, and controls the work that follows.

The architecture defines capabilities and contracts. It names the required behaviour and leaves product choices to the adopting organisation.

The **deterministic spine** sets the rule for truth. Rules over recorded evidence decide what the system may store or present as true. The [Lexikon](https://antikas.io/writing/lexikon/) defines this term and the other named concepts used in the material.

Start with the [README](README.md). The [short article on antikas.io](https://antikas.io/writing/the-enterprise-brain/) gives a general introduction.

## Documents

| Document | Purpose | Use it for |
|---|---|---|
| [README](README.md) | Introduces the system, its truth rule, and its main parts. | A first reading. |
| [Logical reference architecture](logical-reference-architecture.md) | Defines the technology-independent capabilities and their contracts. | Architecture design and capability assessment. |
| [Illustrative solution architecture](illustrative-solution-architecture.md) | Maps the logical contracts to one set of component types and flows. | Testing how the contracts fit a concrete design. |
| [Alternative solution patterns](alternative-solution-patterns.md) | Shows other placements for the same logical contracts. | Comparing estate shapes and deployment choices. |
| [Evaluation framework](eval/evaluation-framework.md) | Defines the requirements, evidence, and hard failure conditions. | Assessing a working system. |

## Diagrams

Each diagram has a D2 source and a matching SVG image. The topology also has a Mermaid source.

| Diagram | Purpose |
|---|---|
| [Summary](diagrams/summary-at-a-glance.svg) | Shows the full design and the controls in the deterministic spine. |
| [Capability map](diagrams/view1-capability-map.svg) | Groups the capabilities by the outcome they own. |
| [Components and flows](diagrams/view2-component-flow.svg) | Shows information stores, derived views, routing, durable work, and release. |
| [Reasoning tiers](diagrams/view3-two-tier-expression.svg) | Shows evidence routing, reasoning routing, the general model, and the specialist inventory. |
| [Trust boundary topology](diagrams/view4-mesh-topology.svg) | Shows business unit scopes, a sensitive domain, separate enterprises, and governed projections. |
| [Learning and operation](diagrams/view5-learn-and-run.svg) | Shows how the system learns an organisation and how durable work recovers from failure. |
| [Illustrative solution](diagrams/illustrative-solution-architecture.svg) | Places the logical contracts on one set of component types. |
| [Alternative patterns](diagrams/alternative-solution-patterns.svg) | Compares several solution shapes. |

The trust boundary topology is also available as [Mermaid](diagrams/view4-mesh-topology.mmd).

## Relationship between the documents

The evaluation framework defines the requirements. The logical architecture assigns each requirement to one capability. Its cross-walk also records the requirements supported by each capability.

The illustrative solution and alternative patterns apply the logical contracts to component and estate shapes. Product mappings can change while the logical contracts remain stable.
