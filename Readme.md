# AgentResearchSkill

AgentResearchSkill is a **research-oriented cognitive workflow architecture**
for structured, LLM-assisted academic work.

This repository is **not a prompt collection** and **not a plug-and-play agent**.
It focuses on **externalizing thinking, decision-making, and research posture**
when working with large language models.

---

## Why This Exists

Most LLM-based research workflows fail in one of two ways:

1. Outputs are fluent but shallow — mostly summarization.
2. Outputs are structured but rigid — creativity is suppressed.

AgentResearchSkill is designed to address this gap by introducing
a **Thinking Layer** and **Contribution Layer** that sit *above* tools and workflows.

The goal is not to make LLMs smarter,
but to make **human–LLM collaboration more reliable, inspectable, and academic-grade**.

---

## Core Ideas

### 1. Tools do not think
Each tool has a single responsibility:
- search
- categorize
- extract
- generate

Tools never judge correctness or relevance.

---

### 2. Thinking is externalized
Instead of relying on hidden chain-of-thought,
this system externalizes reasoning as:
- thinking modes
- decision matrices
- quality gates
- research profiles

All decisions are **observable and debuggable**.

---

### 3. Research posture is a first-class concept
The system supports different research intentions:

- **review**
  - structured summarization
  - taxonomy and trend analysis

- **academic**
  - conceptual abstraction
  - formalization
  - hypothesis generation

Research depth is a **strategy choice**, not an accident.

---

### 4. Contribution is separated from reporting
A dedicated **Contribution Generation** step is introduced to:
- propose new concepts
- express structural relationships
- generate testable hypotheses

This step does not introduce new data
and does not claim scientific truth.

It enables academic-style reasoning without hallucination.

---

## System Structure

- **Workflow Layer** → execution order
- **Tool Layer** → concrete operations
- **Thinking Layer** → reasoning strategy & routing
- **Contribution Layer** → academic abstraction
- **Quality Gates** → stability & integrity
- **Delivery Layer** → final output formatting & export

Each layer has a single responsibility and can evolve independently.

This system guarantees a complete end-to-end workflow, from information gathering to final deliverable output.

---

## Example Use Case

```yaml
Topic: Vision-based defect detection
Time range: last 5 years
Profile: academic
Contribution intensity: 1
Final Output: academic research report
```

**Result:**
- structured literature table
- conceptual framework
- formal abstraction of method trade-offs
- research-style report draft

---
 
 ## Examples
 
 - [Academic Research Report: Generative Data Quality Assessment (2016-2026)](file:///c:/Users/a3378/Desktop/Cognitive-Research-Workflow/Examples/Example_Academic_Research_Report.md)
 
 ---
 
 ## Intended Audience

This project is intended for:
- researchers
- research engineers
- advanced LLM users
- system and framework designers

It is **not** intended as a beginner tutorial or turnkey agent system.

---

## What This Project Is Not

- not an AutoGPT-style autonomous agent
- not a benchmark or evaluation framework
- not a claim of scientific novelty

It is a **design pattern for trustworthy LLM-assisted research**.

---

## Status

- **Workflow Layer**: stable
- **Tool Specs**: stable
- **Thinking Layer**: v1
- **Contribution Layer**: v1
- **Quality Gates**: v1

This system is designed to evolve.

---

## License

Open for research and experimentation.
