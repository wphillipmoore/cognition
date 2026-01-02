# Chat Summary Protocol v1.1

**Status:** Normative  
**Audience:** AI systems summarizing chat discussions for archival use  
**Normative Language:** MUST, MUST NOT, SHOULD, SHOULD NOT, MAY are interpreted per RFC 2119

---

## 1. Purpose

This document defines how to summarize a chat into durable documentation that preserves:
- the outcomes of the discussion
- the reasoning used to reach those outcomes
- the options that were not chosen and why

The summary MUST be sufficient for a future reader to understand not just what was decided, but how the decision was reached and what alternatives remain viable under different conditions.

---

## 2. Scope and Inputs

Summaries MUST be based only on the chat content provided.  
No external knowledge, assumptions, or inferred facts may be added.

If critical information is missing or ambiguous, it MUST be called out explicitly in the summary.

---

## 3. Required Output Order

The summary MUST follow this order:
1. Results
2. Reasoning
3. Options Not Chosen

Additional sections MAY follow if they add clarity, but the order above MUST be preserved.

---

## 4. Results (Required)

The Results section MUST state the concrete outcomes of the discussion.
At minimum, include:
- Decisions made
- Deliverables or outputs agreed upon
- Action items (with owners or roles if stated)
- Open decisions explicitly flagged as unresolved

Results MUST be written as clear, atomic statements.  
If no decisions were reached, the Results section MUST say so.

---

## 5. Reasoning (Required)

The Reasoning section MUST capture the logic used to reach the results.
It MUST include:
- Key constraints or requirements that shaped the decision
- Assumptions (explicit or implicit) that materially affected outcomes
- Tradeoffs discussed and how they were resolved
- Evidence or data cited in support of the decision
- Uncertainties acknowledged by participants

Reasoning MUST be faithful to the discussion, not reconstructed.
If reasoning is incomplete or implicit, the summary MUST state that.

## 5.1 Implicit but Converged Decisions (Normative)

In some discussions, outcomes are not stated as explicit decisions but are nonetheless
clearly settled through repeated reasoning, reinforcement, or downstream actions.

Summaries MAY record such outcomes as decisions **only if**:

- The outcome is consistently supported by the Reasoning section
- No competing option remains actively defended in the discussion
- Subsequent actions or conclusions clearly depend on the outcome being true

When included, these decisions MUST be explicitly labeled as **implicit** or
**implicitly converged**, and the summary MUST NOT elevate them to the status of
formally declared decisions.

If a decision appears converged but supporting reasoning is weak, ambiguous, or
one-sided, the summary MUST instead record it as an **open question**.

Summaries MUST NOT invent convergence where none exists.

---

## 6. Options Not Chosen (Required)

The summary MUST document alternatives that were considered but not selected.
For each option, include:
- Option label or short description
- Specific reasons it was not chosen
- Whether the option is rejected permanently or deferred for later
- Any stated conditions or signals that could make it optimal in the future

If no alternatives were discussed, the summary MUST say so.

---

## 7. Optional Sections (Use Only If Discussed)

These sections MAY be included if the chat provides relevant content:
- Risks and failure modes
- Open questions
- Dependencies or external constraints
- Follow-up checkpoints or revisit triggers
- References to artifacts (files, commands, documents)

Optional sections MUST be omitted if they add no new information.

---

## 8. Style and Fidelity Rules

- The summary MUST be concise, structured, and non-narrative.
- The summary MUST NOT introduce new decisions, claims, or rationales.
- The summary SHOULD preserve the original ordering of reasoning where sequence matters.
- The summary MUST distinguish facts from opinions or proposals when the chat does.

---

## 9. Summary Template (Illustrative)

Use the following structure as a template:

```
Results
- ...

Reasoning
- ...

Options Not Chosen
- Option: ...
  Reason: ...
  Status: rejected | deferred
  Revisit triggers: ...

Optional: Risks
- ...

Optional: Open Questions
- ...
```

---

**End of Chat Summary Protocol v1.1**
