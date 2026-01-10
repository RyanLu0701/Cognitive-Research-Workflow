# Report Confirmation Tool

This document defines the **Report Confirmation Tool** used within the AgentResearchSkill workflow.

This tool is responsible for **presenting a draft research report for confirmation**
and **collecting structured user feedback**.
It does not evaluate accuracy, relevance, or quality.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Report Confirmator | A tool that presents a draft research report for confirmation and collects feedback |

---

## Inputs

- draft_research_report: document  
  (e.g. markdown, PDF, or other renderable format)
- confirmation_prompt: string  
  (e.g. "Please review the following report and indicate approval or required revisions")

---

## Output Artifacts

- confirmation_result: object

The confirmation_result should include:
- status: approved | revision_requested
- revision_notes: string (optional)
- confirmed_report_reference

---

## Execution Behavior

### Step 1 — Present Report
- Display the draft research report for review
- Follow the provided confirmation prompt

### Step 2 — Collect Feedback
- Capture user feedback in a structured form
- Do not interpret, summarize, or evaluate the feedback

### Step 3 — Output
- Return confirmation_result
- Do not modify the report content
