## Quality Gates 

The quality gates are used to decide routing (not to judge truth).
The quality gates are a self-imposed constraint to ensure the quality of the output.

Quality gates may result in:
- pass: proceed normally
- soft_fail: proceed with warning and annotation
- fail: route back according to thinking rules

---

## Quality Gates (v0)

### Gate A — Coverage Gate (after Step 1)
Fail if:
- sources < 10
- time_range mismatch in majority of sources

### Gate B — Taxonomy Gate (after Step 2)
Fail if:
- categories < 3 or > 10
- categories are undefined or overlapping heavily

### Gate C — Table Integrity Gate (after Step 3)
Fail if:
- missing year/venue/url for > 20% entries
- duplicates > 10%

### Gate D — Report Evidence Gate (after Step 5)
Fail if:
- major sections contain no references to confirmed table content
- **[DEPTH] technical mechanisms are mentioned without technical substance**
  (e.g., missing algorithmic steps, objective functions, or mathematical definitions when present in sources / Step 4.5)
- future work is not tied to observed trends

Soft fail if:
- future work is partially speculative but clearly labeled
- minor depth gaps exist but can be fixed without restructuring

---

### Gate E — Academic Adequacy Gate (after Step 5)
Fail if:
- Introduction does not explicitly state:
  - limitations of existing surveys
  - the unique organizing perspective of this work
- Scope & Methodology does not justify inclusion/exclusion criteria
- Taxonomy section lacks rationale ("why this taxonomy")
- **[ACADEMIC] Academic-mode report does not integrate required outputs from Step 4.2 and Step 4.5**
  (e.g., missing gap statement positioning / missing formalization / missing hypotheses when required)
- **[ACADEMIC] Report violates required report_specification or technical_depth_policy defined in `Research/report_making.md`**
- **[ACADEMIC] Significant information loss compared to confirmed base**
  (e.g., ≥ 30% taxonomy categories in the confirmed table are not discussed in findings/trends)

Soft fail if:
- limitations are mentioned but not concretely specified
- taxonomy rationale is present but weak or implicit
- report is noticeably weaker than `Examples/Example_Academic_Research_Report.md` (use as exemplar reference only)

On fail:
- route back to Report Making with academic revision instructions

---
