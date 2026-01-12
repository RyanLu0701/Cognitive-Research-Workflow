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
- title
- abstract
- keywords
- introduction
- scope_methodology
- background
- taxonomy
- findings_trends
- benchmarks_evaluation
- applications_use_cases
- challenges_limitations
- future_directions
- conclusion
- references

Each section should specify:
- purpose: string  
- constraints: list of strings (optional)

Default report_specification (Survey / Review format):
```json
{
  "title": {
    "purpose": "Define a precise, academic review title with time range.",
    "constraints": ["Single sentence", "No marketing language"]
  },
  "abstract": {
    "purpose": "Summarize scope, method, core findings, and contributions.",
    "constraints": ["150-250 words", "No citations"]
  },
  "keywords": {
    "purpose": "Provide 5-8 keywords for indexing.",
    "constraints": ["Comma-separated", "Use domain terms"]
  },
  "introduction": {
    "purpose": "State motivation, scope, and contributions of the review.",
    "constraints": [
    "Must explicitly state limitations of existing surveys",
    "Must clearly articulate the unique organizing perspective of this review"]
  },
  "scope_methodology": {
    "purpose": "Define time range, inclusion criteria, and organization method.",
  "constraints": [
    "Must justify inclusion and exclusion criteria",
    "Must explicitly acknowledge potential bias"]
  },
  "background": {
    "purpose": "Provide minimal definitions and context needed to read the survey.",
    "constraints": ["Avoid tutorial depth"]
  },
  "taxonomy": {
    "purpose": "Present the organizing categories used in the review.",
    "constraints": ["Stable category names", "Explain assignment logic"]
  },
  "findings_trends": {
    "purpose": "Synthesize advances by category with traceable sources.",
    "constraints": ["Use confirmed sources only", "Cite source IDs"]
  },
  "benchmarks_evaluation": {
    "purpose": "Summarize evaluation setups, metrics, and benchmark practices.",
    "constraints": ["Only when applicable in sources"]
  },
  "applications_use_cases": {
    "purpose": "Describe representative real-world applications.",
    "constraints": ["Grounded in confirmed sources"]
  },
  "challenges_limitations": {
    "purpose": "Identify open challenges and limitations reported in sources.",
    "constraints": ["No new claims beyond sources"]
  },
  "future_directions": {
    "purpose": "Summarize plausible next steps and gaps.",
    "constraints": ["Label speculative statements"]
  },
  "conclusion": {
    "purpose": "Recap the most important insights and takeaways.",
    "constraints": ["No new information"]
  },
  "references": {
    "purpose": "List confirmed sources with stable identifiers.",
    "constraints": ["Use confirmed table entries only", "Stable identifiers required"]
  },
  "technical_depth_policy": {
    "constraints": [
      "Every core finding must include its technical mechanism or mathematical  foundation",
      "Academic-mode reports must incorporate all conceptual/formal contributions from Step 4.5",
      "Academic-mode reports MUST follow the structural depth and formatting established in `Examples/Example_Academic_Research_Report.md`",
      "Avoid high-level summaries without specific metric analysis (e.g., explain FID as Wasserstein-2 distance)"]
  }
}
```
The default report_specification targets a Survey / Review / Overview paper format.
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
- Synthesize information from the confirmed table into a coherent narrative
- Perform structured summarization where required (see `Research/summarize.md`)
- **[CRITICAL]** Maintain the full depth of technical information: if a metric or mechanism is described in the sources or Step 4.5, it MUST appear in the draft.
- Ensure the draft is comprehensive and avoids over-simplification.

### Step 2 — Output
- Return the draft research report
- Do not evaluate or revise the content
