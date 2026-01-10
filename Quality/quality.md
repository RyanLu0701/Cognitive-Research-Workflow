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
- major sections contain no references to table content
- future work is not tied to observed trend
Soft fail if:
- future work is partially speculative but clearly labeled

---
