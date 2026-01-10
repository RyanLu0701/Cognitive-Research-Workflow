# Summarize Tool

This document defines the **Summarize Tool** used within the AgentResearchSkill workflow.

This tool is responsible for **converting structured information into a readable textual summary**.
It does not perform search, analysis, evaluation, validation, or workflow decisions.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Summarizer | A tool that converts structured information into descriptive text |

---

## Inputs

- structured_information: table or object  
  (e.g. confirmed_information_table or categorized_information_table)

- summary_instruction: string  
  (e.g. "summarize the key methods", "describe the main findings without interpretation")

---

## Output Artifacts

- summarized_text: string

The summarized_text should:
- Reflect only the provided structured information
- Preserve factual content without adding new sources
- Avoid interpretation, evaluation, or speculation

---

## Execution Behavior

### Step 1 — Generate Summary
- Generate a textual description based strictly on the structured information
- Follow the provided summary instruction

### Step 2 — Output
- Return summarized_text
- Do not introduce new information or claims
