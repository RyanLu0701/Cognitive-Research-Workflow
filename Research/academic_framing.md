# Academic Framing Tool

This document defines the **Academic Framing Tool** used within the `AgentResearchSkill` workflow.

This tool is responsible for **explicitly articulating the academic necessity** of a review or survey paper.

It exists to prevent the workflow from producing engineering-style overviews that lack academic justification.

---

## Goal

Force the system to answer the following question:

> **Why does this review need to exist, given existing surveys?**

---

## Role Definition

### This tool DOES:
- analyze existing survey-level works within the confirmed information set
- identify limitations and blind spots of existing reviews
- articulate the academic gap this review addresses
- position the proposed contributions relative to prior surveys

### This tool does NOT:
- introduce new external sources
- evaluate correctness of individual methods
- generate taxonomy or contributions directly
- write report prose

---

## Inputs

- `confirmed_information_table`: table or excel
  (validated and approved in previous workflow steps)

---

## Output Artifacts

### `academic_framing_notes` (object)

The output MUST include all of the following fields:

```json
{
  "existing_surveys_summary": {
    "description": "Summary of existing survey or overview works identified in the confirmed sources.",
    "source_mapping": ["row_id_1", "row_id_4"]
  },
  "limitations_of_existing_surveys": {
    "description": "Explicit limitations, blind spots, or biases of existing surveys.",
    "source_mapping": ["row_id_1", "row_id_4"]
  },
  "review_gap_statement": {
    "description": "Clear statement of what is missing in existing surveys that motivates this review.",
    "derived_from": ["limitations_of_existing_surveys"]
  },
  "proposed_contribution_positioning": {
    "description": "How this review positions its contributions relative to existing surveys.",
    "addresses_gap": true
  }
}
```

---

## Execution Behavior

**Step 1 — Identify Existing Surveys**
- Scan the confirmed information table for survey, review, or overview papers
- Summarize their stated scope and focus

**Step 2 — Analyze Limitations**
Identify:
- scope limitations
- methodological bias
- missing dimensions (e.g., deployment, scalability, integration)

Explicitly state how these limitations affect the field

**Step 3 — Articulate Review Gap**
Formulate a concise gap statement:
- what is missing
- why it matters academically
- why existing surveys cannot address it

**Step 4 — Position Contributions**
Explain how the upcoming taxonomy and contributions are designed to address the identified gap

**Step 5 — Output**
Return `academic_framing_notes`

Do NOT merge content into the report directly

---

## Quality Constraints

This tool FAILS if:
- no existing survey-level works are identified when they exist in the data
- limitations are vague or generic (e.g. "not comprehensive enough")
- gap statement does not logically follow from identified limitations
- contribution positioning does not clearly address the stated gap

---

## Position in Workflow

This tool MUST be executed:
- after Information Confirmation
- before Contribution Generation

Subsequent steps MUST:
- reference `academic_framing_notes` explicitly
- align taxonomy and contributions with the identified review gap

---

## Design Rationale

Academic survey papers are judged not by completeness alone, but by the clarity of their necessity.

This tool enforces that necessity explicitly, before any conceptual or structural contributions are generated.
