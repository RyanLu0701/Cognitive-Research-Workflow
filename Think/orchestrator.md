# Thinker Orchestrator (v1.1)

This document defines the **strategy-level Thinking Layer**
of the AgentResearchSkill system.

The Thinking Layer does NOT execute tools or generate artifacts.
Its role is to **define reasoning posture, thinking policies, and cognitive constraints**
that guide how workflow decisions are made.

Operational routing decisions are defined separately in:
- `Think/orchestrator_runtime.md`
- `Think/decision_matrix.md`

---

## 0. Scope & Responsibility

This orchestrator defines:

- thinking principles
- thinking states
- research output profiles
- contribution policies
- canonical thinking modes

It does NOT define:
- step-to-step routing
- failure recovery paths
- tool execution logic

Those responsibilities belong to the **Decision Matrix** and **Runtime Orchestrator**.

---

## 1. Core Principles

### P1 — Thinking is explicit, not hidden
Reasoning strategies are externalized as modes, profiles, and policies,
rather than implicit chain-of-thought.

This allows:
- traceability
- debuggability
- controlled variation of reasoning behavior

---

### P2 — Structure enables freedom
Constraints exist only to:
- prevent meaningless outputs
- maintain traceability
- protect academic integrity

They do not suppress exploration or creativity.

---

### P3 — Judgment controls routing, not truth
The Thinker decides:
- whether refinement is needed
- which reasoning posture should be applied
- what level of contribution is appropriate

It never claims correctness or empirical truth.

---

## 2. Thinking States

The system may operate in different **thinking states**.

### Supported States

- `execution` (default)  
  Focus on stability, structure, and reliable delivery.

- `exploration`  
  Allow cross-domain association, hypothesis surfacing,
  alternative abstractions, and creative reframing.

---

### State Rules

- Exploration outputs MUST be explicitly labeled.
- Exploration outputs MUST NOT overwrite confirmed artifacts.
- Exploration outputs MUST NOT affect workflow routing.
- Execution state enforces quality gates strictly.

State may be changed by:
- explicit user instruction
- system decision with justification

---

## 3. Research Output Profiles

Profiles define **what level of research contribution is expected**.

### Supported Profiles

- `review` (default)
  - structured summarization
  - taxonomy and trend description
  - no required conceptual contribution

- `academic`
  - requires research-level contribution
  - enables abstraction, formalization, and hypothesis generation

Profile selection affects:
- whether Contribution Generation is executed
- how Report Making is evaluated
- which Quality Gates are activated

---

## 4. Contribution Policy  
(Active when profile = `academic`)

### Contribution Intensity

Defines how deeply the system should go beyond summarization.

| Level | Description |
|------|------------|
| 0 | No contribution (pure review) |
| 1 | Light contribution (concept + formal OR hypothesis) |
| 2 | Full contribution (concept + formal + hypothesis) |

Default:
- `intensity = 1` when profile = academic

---

### Required Contribution Types

**Intensity ≥ 1**
- Conceptual abstraction
- Either:
  - Formal / structural representation
  - OR testable hypothesis

**Intensity = 2**
- Conceptual abstraction
- Formal / structural representation
- Testable hypothesis

---

### Contribution Constraints

- No new external sources
- All contributions must map to confirmed information
- Speculative elements must be explicitly labeled

Contribution Generation exists to:
- reframe
- abstract
- formalize

It does NOT claim discovery or empirical validation.

> **Contribution Policy does NOT determine workflow routing.**  
> Routing is exclusively controlled by Quality Gates and the Decision Matrix.

---

## 5. Canonical Thinking Modes (Strategy-Level)

Thinking modes define **how the system reasons**, not where it routes.
Routing decisions are handled by the Decision Matrix.

---

### Coverage Thinking
**Goal:** ensure sufficient and diverse evidence.

Typical focus:
- source diversity
- temporal coverage
- missing subdomains

---

### Taxonomy Thinking
**Goal:** produce interpretable, non-overlapping organizational structures.

Typical focus:
- clarity of category boundaries
- explanatory power of taxonomy
- alignment with field evolution

---

### Precision Thinking
**Goal:** ensure structured, consistent, and traceable artifacts.

Typical focus:
- metadata completeness
- duplication
- schema consistency

---

### Human Feedback Thinking
**Goal:** align scope, relevance, and intent with user expectations.

Typical focus:
- scope adjustment
- relevance confirmation
- intent clarification

---

### Academic Framing Thinking
**Goal:** articulate why this work must exist academically.

Typical focus:
- limitations of existing surveys
- unaddressed gaps
- unique organizing perspective

---

### Abstraction & Formalization Thinking
**Goal:** generate intellectual contributions beyond summarization.

Typical focus:
- conceptual unification
- structural representation
- hypothesis formulation

---

### Trajectory Thinking
**Goal:** synthesize evidence and contributions into a coherent research narrative.

Typical focus:
- narrative coherence
- logical progression
- alignment between framing and contribution

---

### Acceptance Thinking
**Goal:** interpret approval or actionable revision feedback.

Typical focus:
- revision intent classification
- routing justification

---

### Delivery Thinking
**Goal:** ensure correct and faithful output formatting.

This mode does NOT:
- modify content
- trigger refinement
- activate quality gates

---

## 6. Interaction with Quality Gates

- Quality Gates determine **whether refinement is required**
- Thinking Modes determine **how refinement should be approached**
- Contribution Policy does NOT override gate decisions

Quality Gates are defined independently and referenced by the Decision Matrix.

---

## 7. Exploration Side Channel

During `exploration` state, the system may generate:

- alternative categorizations
- speculative future directions
- cross-domain analogies

Rules:
- must be clearly labeled as exploratory
- must not alter confirmed artifacts
- must not influence workflow routing
- may be presented as optional notes to the user

---

## 8. Design Intent

This Thinker is designed to:

- allow freedom without chaos
- enable academic insight without hallucination
- separate judgment from generation
- support evolution of research depth over time

It is a **strategy layer**, not a controller.

---

## 9. Summary

The Thinker defines:
- when to explore
- when to execute
- when to contribute
- how deep to go

It does not define:
- what is true
- what is novel
- what must be accepted

Those remain human decisions.
