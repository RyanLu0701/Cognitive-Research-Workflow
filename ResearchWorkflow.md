# AgentResearchSkill

## Overview
AgentResearchSkill defines a reusable research workflow that enables an agent to:
1. search information within a given time range
2. organize information into structured categories
3. extract structured tables for validation
4. validate information with the user
5. generate a formal research report
6. iteratively refine results based on confirmation feedback

This skill focuses on **workflow orchestration and output artifacts**.  
User interaction is handled by the agent runtime.

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

---

### Step 2 — Categorization  
(see `Research/categorization.md`)

- Group information into structured categories
- Do not judge quality or completeness

**Output:** categorized_information_set

---

### Step 3 — Table Extraction  
(see `Research/extract_table.md`)

- Extract structured fields from categorized information
- Generate a reviewable table

**Table Schema:**

| category | title | author(s) | publication_year | source / venue | url | abstract / summary |

**Output:** extracted_information_table

---

### Step 4 — Information Confirmation  
(see `Research/information_confirmation.md`)

- Present the extracted table to the user
- Collect confirmation feedback

**Decision:**
- If approved → proceed to Step 5
- If revision requested → return to Step 2 or Step 3 with feedback

---
### Step 4.5 — Contribution Generation
(see `Research/contribution_generation.md`)

Goal:
- generate conceptual, formal, or hypothesis-level contributions
- do NOT introduce new external sources

Output:
- contribution_notes (concepts / equations / hypotheses)

Quality Constraint:
- each contribution must reference confirmed table entries
- speculative elements must be labeled

**Output:** contribution_notes

---
### Step 5 — Report Making  
(see `Research/report_making.md`)

- Generate a draft research report from confirmed information
- Summarize and synthesize table content into a single document
- Do not introduce unconfirmed sources

**Report Structure:**
- Introduction
- Method
- Result
- Analysis
- Conclusion
- Future Work

**Output:** draft_research_report

---

### Step 6 — Report Confirmation  
(see `Research/report_confirmation.md`)

- Present the draft report to the user
- Collect confirmation feedback

**Decision:**
- If approved → terminate workflow
- If revision requested → return to Step 5 with feedback

### Step 7 — Report Output
(see `Research/report_output.md`)

- Format and deliver the approved research report
- Follow user-defined output specification (e.g. pdf, excel, table)
- No content modification is allowed at this stage

**Output:** final_research_report (pdf / excel / table)

---

## Core Capabilities

- Information Search
- Information Categorization
- Information Extraction
- Structured Summarization
- Report Generation
- Human-in-the-loop Validation
- Iterative Refinement

---

## Thinking Layer
(see `Think/orchestrator.md`)

Defines the **thinking modes and evaluation perspectives**
used to guide decisions between workflow steps.

---

## Quality Assurance
(see `QA/quality_assurance.md`)

Defines post-generation quality checks applied to the report output.

## Decision Logic
(see `Think/decision_matrix.md`)

Defines routing decisions based on quality gates.

---
## Potential Issues (Reference for Thinking / QA Layers)

Common issues that may occur during execution include:
1. Excessive or irrelevant information
2. Information outside the intended time range
3. Insufficient information coverage
4. Incomplete representation of topic development

These issues should be handled by:
- Thinking Layer: deciding whether to route back to Search / Categorization
- QA Layer: validating final report completeness and relevance
