# Report Output Tool

This document defines the **Report Output Tool** used in the final stage
of the AgentResearchSkill workflow.

---

## Role Definition

This tool is responsible for:
- formatting the approved report
- exporting it to the user-defined format

This tool does NOT:
- modify content
- introduce new information
- perform reasoning or validation

---

## Inputs

- approved_research_report: document
- output_specification: pdf | excel | table

---

## Output

- final_research_report (pdf / excel / table)

---

## Execution Behavior

1. Receive approved research report
2. Apply formatting according to output specification
3. Deliver final artifact to the user

---

## Notes

This is a deterministic IO step.
No thinking, routing, or quality judgment occurs at this stage.
