# Report Making Tool

This document defines the **Report Making Tool** used within the AgentResearchSkill workflow.

This tool is responsible for **generating a draft research report**
based on confirmed information and a provided report specification.
It does not evaluate accuracy, relevance, or quality.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Report Maker | A tool that generates a draft research report from confirmed information |

---

## Inputs

- confirmed_information_table: table or excel

- report_specification: object  
  Defines the required structure and intent of the report.

The report_specification may include sections such as:
- introduction
- method
- result
- analysis
- conclusion
- future_work

Each section should specify:
- purpose: string  
- constraints: list of strings (optional)

---

## Output Artifacts

- draft_research_report: document  
  (e.g. markdown, PDF, or other renderable format)

---

## Execution Behavior

### Step 1 — Generate Draft Report
- Generate a research report based on the confirmed information table
- Follow the provided report specification strictly
- Do not introduce new sources beyond the confirmed information
- Combine the information in the table into a single document.Summarize the information in the table. (see `Research/summarize.md`)
- Make a draft research report.
- Make a complete description of all structured information. 

### Step 2 — Output
- Return the draft research report
- Do not evaluate or revise the content
