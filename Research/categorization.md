# Information Categorization Tool

This document defines the **Information Categorization Tool** used within the AgentResearchSkill workflow.

This tool is responsible only for **structuring and grouping raw information sources**
according to a provided categorization instruction.
It does not perform search, analysis, evaluation, or workflow decisions.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Information Categorizer | A tool that groups raw information sources into structured categories |

---

## Inputs

- raw_information_set: list of objects
- categorization_instruction: string  
  (e.g. "group by research method", "group by problem domain", "group by data type")

Each object in `raw_information_set` should include at least:
- title
- author(s)
- publication_year
- source / venue
- url
- short abstract or summary (if available)

---

## Output Artifacts

- categorized_information_set: list of objects

Each object should include:
- category
- title
- author(s)
- publication_year
- source / venue
- url
- short abstract or summary (if available)

---

## Execution Behavior

### Step 1 — Apply Categorization Instruction
- Read and follow the provided categorization instruction
- Assign **one primary category** to each information item

### Step 2 — Construct Categorized Set
- Produce a structured set with one object per information item
- Ensure category labels are consistent and concise

### Step 3 — Output
- Return the categorized set
- Do not rank, analyze, or judge the quality of categories
