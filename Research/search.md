# Information Search Tool

This document defines the **Information Search Tool** used within the AgentResearchSkill workflow.

This tool is responsible only for **collecting raw, relevant information sources**
based on given input parameters.  
It does not perform categorization, analysis, or quality judgment.

---

## Skill Metadata

| name | description |
| ---- | ----------- |
| Information Searcher | A tool that searches and collects raw information sources related to a given topic |

---

## Inputs

- topic: string  
- time_range: string or number (e.g. "last 5 years")

---

## Output Artifacts

- raw_information_set: list of objects

Each object should include at least:
- title
- author(s)
- publication_year
- source / venue
- url
- short abstract or summary (if available)

---

## Execution Behavior

### Step 1 — Query Construction
- Generate search queries based on the given topic
- Include common synonyms or closely related terms

### Step 2 — Source Retrieval
- Search for information using public internet sources
- Prefer academic papers, surveys, and authoritative technical articles

### Step 3 — Time Filtering
- Filter results to match the specified time range
- If publication year is unclear, mark it as "unknown"

### Step 4 — Source Collection
- Collect a diverse set of representative sources
- Avoid duplicate content
- Avoid purely promotional or low-credibility sources

### Step 5 — Output
- Return the collected sources as `raw_information_set`
- Do not rank, analyze, or categorize the sources
