# Decision Matrix — Thinking Layer × Quality Gates

This matrix defines how **Thinking Modes** and **Quality Gates**
jointly determine workflow routing decisions.

The matrix does NOT judge correctness.
It only decides whether to:
- proceed
- proceed with warning
- route back for refinement

---

## Legend

- ✅ pass → proceed
- ⚠️ soft_fail → proceed with annotation
- ❌ fail → route back

---

## Step 1 — Search

Thinking Mode: Coverage Thinking  
Quality Gate: Gate A — Coverage Gate

| Condition | Decision | Action |
|--------|--------|--------|
| sources ≥ 10 AND time_range aligned | ✅ pass | proceed to Categorization |
| sources ≥ 10 BUT coverage skewed | ⚠️ soft_fail | proceed + annotate coverage risk |
| sources < 10 OR time_range mismatch | ❌ fail | rerun Search with expanded query |

---

## Step 2 — Categorization

Thinking Mode: Taxonomy Thinking  
Quality Gate: Gate B — Taxonomy Gate

| Condition | Decision | Action |
|--------|--------|--------|
| 3 ≤ categories ≤ 10 AND clear definitions | ✅ pass | proceed to Table Extraction |
| minor overlap but understandable | ⚠️ soft_fail | proceed + annotate taxonomy ambiguity |
| categories vague OR heavily overlapping | ❌ fail | re-categorize with new axis |

---

## Step 3 — Table Extraction

Thinking Mode: Precision Thinking  
Quality Gate: Gate C — Table Integrity Gate

| Condition | Decision | Action |
|--------|--------|--------|
| missing fields ≤ 20% AND duplicates ≤ 10% | ✅ pass | proceed to Information Confirmation |
| metadata partially missing but recoverable | ⚠️ soft_fail | proceed + flag incomplete rows |
| missing fields > 20% OR duplicates > 10% | ❌ fail | return to Search or re-extract |

---

## Step 4 — Information Confirmation

Thinking Mode: Human Feedback Thinking  
Quality Gate: (Human override)

| Condition | Decision | Action |
|--------|--------|--------|
| user approves | ✅ pass | proceed to Report Making |
| user requests revision | ❌ fail | route back per revision_notes |

---

## Step 5 — Report Making

Thinking Mode: Trajectory Thinking  
Quality Gate: Gate D — Report Evidence Gate

| Condition | Decision | Action |
|--------|--------|--------|
| claims grounded in table AND coherent narrative | ✅ pass | proceed to Report Confirmation |
| speculative ideas clearly labeled | ⚠️ soft_fail | proceed + annotate speculative sections |
| ungrounded claims OR generic future work | ❌ fail | re-outline or rewrite weak sections |

---

## Step 6 — Report Confirmation

Thinking Mode: Acceptance Thinking  
Quality Gate: (Human override)

| Condition | Decision | Action |
|--------|--------|--------|
| user approves | ✅ pass | terminate workflow |
| user requests revision | ❌ fail | return to Report Making |

---

## Step 7 — Report Output

Thinking Mode: Output Thinking
Quality Gate: (Human override)

| Condition | Decision | Action |
|--------|--------|--------|
| user approves | ✅ pass | terminate workflow |

---

