# Information Confirmation Tool

This document defines the **Information Confirmation Tool** used within the AgentResearchSkill workflow.

This tool is responsible for **presenting categorized information for confirmation**
and **collecting structured feedback**.
It does not evaluate accuracy, relevance, or quality.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Information Confirmator | A tool that presents information for confirmation and collects user feedback |

---

## Inputs

- categorized_information_table: table or excel
- confirmation_prompt: string  
  (e.g. "Please review the following information and indicate approval or required revisions")

---

## Output Artifacts

- confirmation_result: object

The confirmation_result should include:
- status: approved | revision_requested
- revision_notes: string (optional)
- confirmed_information_table

---

## Execution Behavior

### Step 1 — Present Information
- Display the categorized information table for review
- Follow the provided confirmation prompt

### Step 2 — Collect Feedback
- Capture user feedback in a structured form
- Do not interpret or evaluate the feedback

### Step 3 — Output
- Return confirmation_result
- Do not modify the information content
