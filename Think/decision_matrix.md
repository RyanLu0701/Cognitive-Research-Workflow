# Decision Matrix — Thinking Layer × Quality Gates (v1.1)

This matrix defines how **Thinking Modes**, **Quality Gates**, and **Human Feedback**
jointly determine workflow routing decisions.

The matrix does NOT judge correctness or truth.
It only decides whether to:
- proceed
- proceed with annotation
- route back for refinement

---

## Legend

- ✅ pass → proceed
- ⚠️ soft_fail → proceed with annotation
- ❌ fail → route back

---

## Step 1 — Search

Thinking Mode: Coverage Reasoning  
Quality Gate: Gate A — Coverage Gate

| Condition | Decision | Action |
|--------|--------|--------|
| sources ≥ 10 AND time range aligned | ✅ pass | proceed to Categorization |
| sources ≥ 10 BUT coverage skewed | ⚠️ soft_fail | proceed + annotate coverage risk |
| sources < 10 OR time range mismatch | ❌ fail | rerun Search with expanded or revised query |

---

## Step 2 — Categorization

Thinking Mode: Structural Reasoning  
Quality Gate: Gate B — Taxonomy Gate

| Condition | Decision | Action |
|--------|--------|--------|
| 3 ≤ categories ≤ 10 AND clear rationale | ✅ pass | proceed to Table Extraction |
| minor overlap but interpretable | ⚠️ soft_fail | proceed + annotate taxonomy ambiguity |
| categories vague OR heavily overlapping | ❌ fail | re-categorize with revised organizing axis |

---

## Step 3 — Table Extraction

Thinking Mode: Integrity Reasoning  
Quality Gate: Gate C — Table Integrity Gate

| Condition | Decision | Action |
|--------|--------|--------|
| missing fields ≤ 20% AND duplicates ≤ 10% | ✅ pass | proceed to Information Confirmation |
| metadata partially missing but recoverable | ⚠️ soft_fail | proceed + flag incomplete entries |
| missing fields > 20% OR duplicates > 10% | ❌ fail | return to Search or re-extract table |

---

## Step 4 — Information Confirmation

Thinking Mode: Human Feedback Reasoning  
Quality Gate: Human Override

| Condition | Decision | Action |
|--------|--------|--------|
| user approves | ✅ pass | proceed to Academic Framing |
| user requests revision | ❌ fail | route to Step 2 or Step 3 per revision notes |

---

## Step 4.2 — Academic Framing

Thinking Mode: Academic Framing Reasoning  
Quality Gate: Gate E — Academic Adequacy Gate

| Condition | Decision | Action |
|--------|--------|--------|
| clear review gap AND justified perspective | ✅ pass | proceed to Contribution Generation |
| gap stated but weakly justified | ⚠️ soft_fail | proceed + annotate framing weakness |
| no clear gap OR no justification | ❌ fail | rework Academic Framing |

---

## Step 4.5 — Contribution Generation

Thinking Mode: Contribution Alignment Reasoning  
Quality Gate: Gate E (Contribution Alignment)

| Condition | Decision | Action |
|--------|--------|--------|
| contributions address identified gaps | ✅ pass | proceed to Report Making |
| speculative elements clearly labeled | ⚠️ soft_fail | proceed + annotate speculative scope |
| contributions misaligned or unsupported | ❌ fail | regenerate contributions |

---

## Step 5 — Report Making

Thinking Mode: Synthesis & Trajectory Reasoning  
Quality Gates: Gate D + Gate E

| Condition | Decision | Action |
|--------|--------|--------|
| framing, contributions, and evidence aligned | ✅ pass | proceed to Report Confirmation |
| speculative sections labeled but uneven | ⚠️ soft_fail | proceed + annotate weak sections |
| generic narrative OR missing framing | ❌ fail | return to Step 4.2 or Step 4.5 |

---

## Step 6 — Report Confirmation

Thinking Mode: Acceptance Reasoning  
Quality Gate: Human Override

| Condition | Decision | Action |
|--------|--------|--------|
| user approves | ✅ pass | proceed to Report Output |
| revision requested (writing) | ❌ fail | return to Step 5 |
| revision requested (framing / contribution) | ❌ fail | return to Step 4.2 or Step 4.5 |

---

## Step 7 — Report Output

Thinking Mode: Output Integrity Reasoning  
Quality Gate: Human Override

| Condition | Decision | Action |
|--------|--------|--------|
| user approves | ✅ pass | terminate workflow |
| format issue only | ❌ fail | rerun Report Output only |

---

## Priority Resolution Rules

When multiple failures occur simultaneously:
1. Resolve Integrity issues first
2. Resolve Academic Framing before Contribution refinement
3. Resolve Contribution alignment before Writing clarity
4. Writing and presentation issues are resolved last

---

## Notes

- Soft failures may proceed with annotation, depending on context.
- The decision matrix only determines **workflow routing**, not content correctness.
