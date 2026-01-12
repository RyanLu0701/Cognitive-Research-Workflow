# AgentResearchSkill

## Overview
AgentResearchSkill defines a reusable research workflow that enables an agent to:
1. search information within a given time range
2. organize information into structured categories
3. extract structured tables for validation
4. validate information with the user
5. generate a formal research report
6. iteratively refine results based on confirmation feedback

This skill focuses on **workflow structure and output artifacts**.  
Execution control and routing decisions are handled externally by the orchestration layer.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| AgentResearchSkill | A structured research workflow skill that searches, categorizes, validates, and reports information |

---

## Inputs

- topic: string  
- time_range: string or number (e.g. "last 5 years")
- output_format: table / excel / pdf (default: pdf)

---

## Output Artifacts

1. information_table (table or excel)
2. research_report (pdf or document)

---

## Execution Workflow

### Step 1 — Search  
(see `Research/search.md`)

- Search information related to the given topic
- Filter results based on the specified time range
- Collect representative and relevant sources

**Output:** raw_information_set  
Run: Gate A — Coverage Gate

---

### Step 2 — Categorization  
(see `Research/categorization.md`)

- Group information into structured categories
- Do not judge quality or completeness

**Output:** categorized_information_set  
Run: Gate B — Taxonomy Gate

---

### Step 3 — Table Extraction  
(see `Research/extract_table.md`)

- Extract structured fields from categorized information
- Generate a reviewable table

**Table Schema:**

| category | title | author(s) | publication_year | source / venue | url | abstract / summary |

**Output:** extracted_information_table  
Run: Gate C — Table Integrity Gate

---

### Step 4 — Information Confirmation  
(see `Research/information_confirmation.md`)

- Present the extracted table to the user
- Collect confirmation feedback

**Decision:**
- If approved → proceed to Step 4.2
- If revision requested → return to Step 2 or Step 3

---

### Step 4.2 — Academic Framing  
(see `Research/academic_framing.md`)

Goal:
- explicitly articulate why this review must exist academically

Actions:
- identify existing survey / overview works
- analyze their limitations and blind spots
- formulate a clear review gap statement
- position the proposed review relative to existing surveys

Constraints:
- no new external sources
- all claims traceable to confirmed entries

**Output:** academic_framing_notes

---

### Step 4.5 — Contribution Generation  
(see `Research/contribution_generation.md`)

Goal:
- generate conceptual, formal, or hypothesis-level contributions
- contributions MUST address gaps identified in academic_framing_notes

Constraints:
- no new external sources
- speculative elements explicitly labeled
- all contributions mapped to confirmed entries

**Output:** contribution_notes

---

### Step 5 — Report Making  
(see `Research/report_making.md`)

- Follow the Survey / Review report specification
- Generate a draft report based on:
  - confirmed_information_table
  - academic_framing_notes
  - contribution_notes

The report MUST explicitly reflect:
- the identified review gap
- the organizing perspective
- the taxonomy rationale

**Output:** draft_research_report  
Run: Gate D — Report Evidence Gate  
Run: Gate E — Academic Adequacy Gate

---

### Step 6 — Report Confirmation  
(see `Research/report_confirmation.md`)

- Present the draft report to the user
- Collect confirmation feedback

**Decision:**
- If approved → proceed to Step 7
- If revision requested:
  - writing/structure issues → Step 5
  - framing issues → Step 4.2
  - contribution issues → Step 4.5

---

### Step 7 — Report Output  
(see `Research/report_output.md`)

- Format and deliver the approved report
- Follow user-defined output specification
- No content modification allowed

**Output:** final_research_report

---

## Orchestration Integration (Non-Step)

This workflow is executed under an external orchestration loop:

- Strategy-level thinking: `Think/orchestrator.md`
- Runtime routing logic: `Think/orchestrator_runtime.md`
- Routing rules: `Think/decision_matrix.md`

The orchestrator is **not** a workflow step.  
It wraps the workflow and determines next-step routing based on gate results and user feedback.

---

## Core Capabilities

- Information Search
- Information Categorization
- Information Extraction
- Academic Framing
- Contribution Generation
- Structured Report Synthesis
- Human-in-the-loop Validation
- Iterative Refinement

---

## Quality Assurance
(see `Quality/quality_assurance.md`)

Defines post-generation quality checks applied to report outputs.

---

## Potential Issues (Handled by Thinking & QA Layers)

Common issues include:
1. Insufficient or skewed information coverage
2. Weak or unclear taxonomy
3. Incomplete or inconsistent metadata
4. Unclear academic motivation or review gap
5. Misaligned or weak research contributions
6. Narrative or presentation issues

These issues are handled by:
- **Thinking Layer**: deciding refinement strategy and routing
- **Decision Matrix**: determining where to route
- **QA Layer**: validating output adequacy
