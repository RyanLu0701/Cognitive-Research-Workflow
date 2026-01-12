# Runtime Orchestrator

This document defines the **runtime-level orchestration logic**
for AgentResearchSkill.

The Runtime Orchestrator is responsible for:
- tracking execution state
- interpreting quality gate results and user feedback
- consulting the Decision Matrix
- selecting the next workflow step to execute

It does NOT:
- generate content
- modify artifacts
- evaluate correctness or truth
- replace human confirmation

---

## 1. Role in the Architecture

The Runtime Orchestrator sits between:

- **Strategy Layer**
  - `Think/orchestrator.md`
- **Decision Rules**
  - `Think/decision_matrix.md`
- **Execution Layer**
  - Research tools (Search, Categorization, Report, etc.)

Its sole responsibility is **step routing**.

---

## 2. Core Responsibilities

At each execution cycle, the Runtime Orchestrator MUST:

1. Identify the current workflow step
2. Collect execution signals
3. Aggregate gate outcomes
4. Interpret user feedback (if any)
5. Determine the next step via the Decision Matrix
6. Emit a routing decision with justification

---

## 3. Runtime State Representation

The orchestrator maintains a minimal runtime state.

### Required State Fields

```json
{
  "current_step": "Step ID",
  "completed_steps": ["Step IDs"],
  "artifacts": {
    "raw_information_set": "...",
    "confirmed_information_table": "...",
    "academic_framing_notes": "...",
    "contribution_notes": "..."
  },
  "gate_results": {
    "GateA": "pass | soft_fail | fail",
    "GateB": "pass | soft_fail | fail",
    "GateC": "pass | soft_fail | fail",
    "GateD": "pass | soft_fail | fail",
    "GateE": "pass | soft_fail | fail"
  },
  "user_feedback": {
    "status": "approved | revision_requested | null",
    "revision_notes": "string | null"
  },
  "profile": "review | academic",
  "thinking_state": "execution | exploration"
}
```

This state may be implicit (mental model) or explicit (structured data),
depending on implementation.

---

## 4. Execution Cycle

The Runtime Orchestrator operates in discrete cycles.

Execution Loop (Conceptual)

Execute current step tool

Receive output artifacts

Run associated Quality Gates

Capture gate outcomes

Capture user feedback (if required)

Consult Decision Matrix

Select next step

Repeat until termination

---

## 5. Gate Interpretation Rules

Gate Outcomes

pass

No routing change required

soft_fail

Proceed to next step

Annotate weakness for later stages

fail

Must route back according to Decision Matrix

The Runtime Orchestrator must not override gate outcomes.

---

## 6. User Feedback Interpretation

User feedback is treated as a routing signal, not a quality judgment.

Supported Feedback Types

Feedback Pattern | Interpreted As | Typical Routing
--- | --- | ---
"missing information" | coverage issue | Step 1
"taxonomy unclear" | structural issue | Step 2
"table inaccurate" | integrity issue | Step 3
"purpose unclear" | framing issue | Step 4.2
"contribution weak" | contribution issue | Step 4.5
"writing unclear" | presentation issue | Step 5

If feedback is ambiguous, default routing is:

Step 5 (Report Making)

---

## 7. Routing Decision Logic

The Runtime Orchestrator MUST:

Aggregate all gate failures

Apply priority resolution rules

Select a single next step

Provide a routing justification

Priority Resolution Order

Integrity failures (Gate C)

Academic framing failures (Gate E)

Contribution alignment failures

Structural failures (Gate B)

Coverage failures (Gate A)

Writing / presentation issues

---

## 8. Routing Decision Output

Each decision must be explicit.

Example Output

```json
{
  "next_step": "Step 4.2 — Academic Framing",
  "reason": "Gate E failed: review gap not clearly articulated",
  "context": {
    "failed_gates": ["GateE"],
    "profile": "academic"
  }
}
```

This output is consumed by:

the agent runtime

or a supervising controller

or logged for traceability

---

## 9. Termination Conditions

The workflow terminates when:

Step 7 (Report Output) completes successfully

user explicitly accepts final output

After termination:

no further gates are evaluated

no further routing decisions are made

---

## 10. Implementation Notes

This orchestrator may be implemented as:

code

a controller agent

a prompt-based decision module

or human-in-the-loop reasoning

The specification is implementation-agnostic

The orchestrator MUST remain stateless with respect to content

---

## 11. Design Intent

The Runtime Orchestrator exists to ensure:

decisions are systematic, not ad-hoc

failures result in meaningful refinement, not repetition

academic rigor is enforced structurally, not heuristically

It is a decision engine, not a thinker.
