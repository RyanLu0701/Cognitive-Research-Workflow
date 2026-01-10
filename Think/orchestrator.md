# Thinker Orchestrator

This document defines the **Thinking Layer** of the AgentResearchSkill system.

The Thinking Layer does not execute tools or generate artifacts.
Its role is to **guide reasoning strategy, decision routing, and research posture**
across the workflow.

---

## 1. Core Principles

### P1 — Thinking is explicit, not hidden
Reasoning strategies are externalized as modes, profiles, and policies,
rather than implicit chain-of-thought.

### P2 — Structure enables freedom
Constraints exist only to:
- prevent meaningless outputs
- maintain traceability
- protect academic integrity

They do not suppress exploration.

### P3 — Judgment controls routing, not truth
The Thinker decides:
- whether to proceed
- whether to refine
- whether to escalate

It never claims correctness.

---

## 2. Thinking States

The system may operate in different **thinking states**.

### Supported States

- `execution` (default)  
  Focus on stability, structure, and delivery.

- `exploration`  
  Allow cross-domain association, hypothesis surfacing,
  and alternative abstractions.

### State Rules

- Exploration outputs MUST be explicitly labeled.
- Exploration outputs MUST NOT overwrite confirmed artifacts.
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
  - includes research-level contributions
  - enables concept abstraction, formalization, and hypothesis generation

Profile selection affects:
- whether Contribution Generation is executed
- how Report Making is evaluated

---

## 4. Contribution Policy (Active when profile = academic)

### Contribution Intensity

Defines how deep the system should go beyond summarization.

| Level | Description |
|------|------------|
| 0 | No contribution (pure review) |
| 1 | Light contribution (concept + one formal or hypothesis) |
| 2 | Full contribution (concept + formal + hypothesis) |

Default:
- `intensity = 1` when profile = academic

---

### Required Contribution Types (Intensity ≥ 1)

- Conceptual abstraction
- Either:
  - Formal / structural representation
  - OR testable hypothesis

### Required Contribution Types (Intensity = 2)

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

Not to claim discovery.

---

## 5. Thinking Modes by Workflow Step

### Step 1 — Search
**Mode:** Coverage Thinking  
Goal: ensure sufficient and diverse evidence.

---

### Step 2 — Categorization
**Mode:** Taxonomy Thinking  
Goal: produce interpretable, non-overlapping categories.

---

### Step 3 — Table Extraction
**Mode:** Precision Thinking  
Goal: ensure structured, consistent artifacts.

---

### Step 4 — Information Confirmation
**Mode:** Human Feedback Thinking  
Goal: align scope and relevance with user intent.

---

### Step 4.5 — Contribution Generation (conditional)
**Mode:** Abstraction & Formalization Thinking  

Activated when:
- profile = academic
- contribution intensity ≥ 1

Goal:
- generate concepts, structures, and hypotheses
- prepare intellectual content for academic synthesis

---

### Step 5 — Report Making
**Mode:** Trajectory Thinking  

Goal:
- integrate evidence + contributions
- construct a coherent research narrative

---

### Step 6 — Report Confirmation
**Mode:** Acceptance Thinking  
Goal: collect approval or actionable revision feedback.

Step 7 — Report Output is a terminal delivery step.
**Mode:** Delivery Thinking
Goal: format and deliver the approved report.
It is not influenced by thinking state or quality gates.

---

## 6. Interaction with Quality Gates

- Quality Gates determine routing decisions
- Thinking Modes determine *how refinement happens*
- Contribution Policy does NOT affect routing directly

Quality Gates are defined separately and referenced by the Decision Matrix.

---

## 7. Exploration Side Channel

During `exploration` state, the system may generate:

- alternative categorizations
- speculative future directions
- cross-domain analogies

Rules:
- must be clearly labeled as exploratory
- must not alter workflow routing
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

---
