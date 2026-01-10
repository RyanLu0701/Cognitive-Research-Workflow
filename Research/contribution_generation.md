# Contribution Generation Tool

This document defines the **Contribution Generation Tool** used within the
`AgentResearchSkill` workflow.

This tool is responsible for generating **research-level contributions**
based strictly on **confirmed information**, without introducing new external sources.

Its purpose is to elevate outputs from **summarization**
to **conceptual and academic-level insight**.

---

## Role Definition

### This tool does NOT:
- search new information
- validate correctness
- claim empirical truth

### This tool DOES:
- abstract concepts
- formalize observed structures
- propose testable hypotheses

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Contribution Generator | Generates conceptual, formal, and hypothetical research contributions from confirmed information |

---

## Inputs

### Required
- `confirmed_information_table`: table or excel  
  (validated and approved in previous workflow steps)

### Optional
- `contribution_constraints`: object

Example:
```json
{
  "allow_speculation": true,
  "max_concepts": 1,
  "max_formalizations": 1,
  "max_hypotheses": 1
}
```

---

## Output Artifacts

**contribution_notes** (object)

The `contribution_notes` object MUST include exactly:

```json
{
  "conceptual_contribution": {...},
  "formal_contribution": {...},
  "hypothesis_contribution": {...}
}
```

Each contribution MUST be explicitly labeled as:
- **grounded** — directly supported by confirmed information
- **speculative** — inferred or extrapolated from observed patterns

---

## Contribution Types

### 1. Conceptual Contribution (Required)
**Goal**
Introduce a new conceptual abstraction or framework that unifies or reframes existing methods.

**Allowed Actions**
- define new terminology
- identify latent dimensions
- group methods under a shared principle

**Constraints**
- MUST reference entries in the `confirmed_information_table`
- MUST explain the mapping between the concept and source entries

**Output Format**
```json
{
  "label": "grounded | speculative",
  "concept_name": "string",
  "description": "string",
  "source_mapping": ["row_id_3", "row_id_7"]
}
```

### 2. Formal / Structural Contribution (Required)
**Goal**
Express observed relationships using symbolic or mathematical structure.

This formalization:
- does NOT claim physical or mathematical truth
- represents structure, trade-offs, or design space

**Allowed Forms**
- symbolic definitions
- abstract equations
- optimization or trade-off formulations

**Constraints**
- MUST be interpretable
- MUST relate variables back to observed trends

**Output Format**
```json
{
  "label": "grounded | speculative",
  "formal_structure": "LaTeX or symbolic notation",
  "explanation": "string",
  "source_mapping": ["row_id_1", "row_id_5"]
}
```

**Example**
Let $M = \{m_1, m_2, \dots, m_n\}$ be the set of observed methods.
Define a performance vector: $f(m_i) \in \mathbb{R}^d$.
Observed trends suggest the existence of a *Pareto frontier* over the space defined by $f$.

### 3. Hypothesis Contribution (Required)
**Goal**
Propose a testable research hypothesis that logically follows from observed trends or gaps.

**Constraints**
- MUST clearly state assumptions
- MUST specify what would falsify the hypothesis
- MUST indicate the empirical gap

**Output Format**
```json
{
  "label": "speculative",
  "hypothesis": "string",
  "assumptions": ["string"],
  "testable_prediction": "string",
  "source_mapping": ["row_id_2", "row_id_9"]
}
```

---

## Execution Behavior

### Step 1 — Pattern Extraction
- Analyze the `confirmed_information_table`
- Identify dominant trends, gaps, and contrasts

### Step 2 — Contribution Synthesis
Generate exactly:
- 1 conceptual contribution
- 1 formal contribution
- 1 hypothesis contribution

### Step 3 — Labeling & Grounding
- Explicitly label each contribution
- Provide source mapping for traceability

### Step 4 — Output
- Return `contribution_notes`
- Do NOT merge content into the report directly

---

## Quality Constraints

Contribution Generation **FAILS** if:
- new external sources are introduced
- contributions cannot be traced to confirmed data
- speculative elements are not explicitly labeled

---

## Position in Workflow

This tool MUST be executed:
- after **Information Confirmation**
- before **Report Making**

**Report Making** MUST:
- consume `contribution_notes`
- explicitly integrate them into discussion and analysis sections

---

## Design Rationale

This tool exists to:
- separate thinking beyond summarization from reporting
- preserve academic rigor without blocking creativity
- enable higher-level insight while maintaining traceability

**Notes**
- This tool does not guarantee novelty in the scientific sense.
- It guarantees:
  - explicit abstraction
  - formal structural representation
  - hypothesis generation grounded in observed evidence