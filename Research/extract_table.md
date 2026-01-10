## Extract Table Tool

This tool is responsible for **extracting a structured table** from raw information sources.
It does not perform search, analysis, evaluation, or workflow decisions.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Extract Table Tool | A tool that extracts a structured table from raw information sources |

---

## Inputs

- raw_information_set: list of objects

Each object should include at least:
- title
- author(s)
- publication_year
- source / venue
- url
- short abstract or summary (if available)

---

## Output Artifacts

- extracted_information_table: table or excel

Each row should include:
- title
- author(s)
- publication_year
- source / venue
- url
- short abstract or summary (if available)

---

## Execution Behavior

### Step 1 — Extract Table
- Read and follow the provided categorization instruction
- Assign **one primary category** to each information item

### Step 2 — Construct Categorized Set
- Produce a structured set with one object per information item
- Ensure table labels are consistent and concise

### Step 3 — Output
- Return the extracted table
- Do not rank, analyze, or judge the quality of categories
