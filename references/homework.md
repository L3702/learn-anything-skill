# Homework Specification

This document defines the homework system for `learn-anything`. Homework is assigned at the end of each phase and unit, with quantitative scoring rubrics for consistent evaluation.

## Homework Schedule

| Trigger | When | Type |
|---|---|---|
| Phase 0 complete | After plan approval | **Pre-study HW** — readiness & motivation |
| Each MLU complete | After Active Recall Test passes | **Unit HW** — reinforce & extend |
| Phase 2 resume | Start of continuation session | **Warm-up HW** — combat forgetting |
| All units complete | After final unit mastered | **Capstone HW** — synthesis project |

---

## Pre-study HW (Phase 0)

Assigned immediately after the learning plan is approved. Due before the first teaching session.

### Purpose
Activate prior knowledge, set mental hooks, and surface hidden gaps before teaching begins.

### Assignment Template

> **Pre-study HW: Preparation for <Topic>**
>
> Complete the following before our next session (estimated: 15–20 min):
>
> 1. **Concept Map**: List 3–5 things you already know or think you know about <Topic>. Draw connections between them (even if some are wrong — that''s fine).
> 2. **Question Generation**: Write 3 questions you want answered about <Topic>. At least one must start with "why" or "how", not "what".
> 3. **Self-efficacy Check**: On a scale of 1–10, how confident are you that you could explain <Topic> to a friend right now? What would it take to move that number up by 2?

### Scoring Rubric (Pre-study HW)

| Criterion | 2 points | 1 point | 0 points |
|---|---|---|---|
| **Concept Map Quality** | 3+ concepts with meaningful connections | 3+ concepts listed but no connections | Fewer than 3 concepts |
| **Question Depth** | At least 1 "why/how" question + questions are specific | Questions present but all are "what" level | Vague or off-topic questions |
| **Self-awareness** | Numeric rating + specific, actionable plan for improvement | Rating given but no plan | No rating or no reflection |

**Pass threshold:** ≥ 4 / 6 points
**Below threshold:** Explain the specific gaps and ask the user to micro-resubmit the deficient part (not the full HW). If the micro-resubmission passes, proceed. If it fails again, address the gaps directly and proceed anyway — Pre-study HW is a readiness check, not a blocker. Never delay teaching more than one retry for Pre-study.

---

## Unit HW (Each MLU)

Assigned immediately after the unit is marked as **mastered** (Active Recall passed). Due before the next unit.

### Purpose
Prevent forgetting through spaced retrieval, extend understanding to novel contexts, and build transfer skills.

### Assignment Template

> **Unit N HW: <Concept Name>**
>
> Complete the following before Unit N+1 (estimated: 20–30 min):
>
> 1. **Active Recall (no notes)**: Write down everything you remember about <Concept>. Then check against your notes and highlight what you missed.
> 2. **Novel Application**: Solve this problem that requires using <Concept> in a way we haven''t practiced:
>    - [Insert a fresh problem that requires combining this concept with real-world context or another concept]
> 3. **Error Analysis**: Find one example of a common mistake beginners make with <Concept>. Explain why it happens and how to avoid it.

### Scoring Rubric (Unit HW)

| Criterion | 2 points | 1 point | 0 points |
|---|---|---|---|
| **Recall Completeness** | Recalls ≥ 80% of key points without notes | Recalls 50–80% of key points | Recalls < 50% or needed notes |
| **Application Correctness** | Novel problem solved with correct reasoning | Correct approach but minor execution error | Wrong approach or unsolved |
| **Error Analysis Depth** | Identifies a real beginner error + explains cause + gives prevention strategy | Identifies error but analysis is shallow | No error identified or analysis is incorrect |
| **Effort & Completeness** | All 3 parts fully completed | 2 of 3 parts completed | 1 or fewer parts completed |

**Pass threshold:** ≥ 6 / 8 points
**Below threshold:** Revisit the unit from Intuition step before moving on; the concept is added to `struggling_with` in `state.json`.

---

## Warm-up HW (Phase 2 Resume)

Assigned at the start of every continuation session, before new teaching begins.

### Purpose
Combat the forgetting curve and reactivate neural pathways from previous sessions. Research shows that retrieval practice within 24–72 hours dramatically improves long-term retention.

### Assignment Template

> **Warm-up HW: Resuming <Topic>**
>
> Before we start Unit N, complete this 5–10 minute refresher:
>
> 1. **Flash Recall (3 min)**: Without looking at notes, write down:
>    - The main concept from the last 2 units you completed
>    - One thing that confused you or felt tricky
>    - One real-world connection you can make
> 2. **Mini-problem**: [Insert 1 short problem combining the last 2 units'' concepts]
> 3. **Confidence Check**: Rate your readiness to continue (1–10). If below 6, say why.

### Scoring Rubric (Warm-up HW)

| Criterion | 2 points | 1 point | 0 points |
|---|---|---|---|
| **Flash Recall Accuracy** | 2 main concepts correctly recalled + valid real-world connection | 1 concept correct or connection is vague | No concepts recalled correctly |
| **Mini-problem** | Solved correctly in under 5 minutes | Solved with hints or took > 5 min | Not attempted or incorrect |
| **Metacognition** | Honest confidence rating + specific reason if < 6 | Rating given without reasoning | No rating |

**Pass threshold:** ≥ 4 / 6 points
**Below threshold:** Spend extra time reviewing previous unit before starting new material. Run a quick re-teach of the weakest concept.

---

## Capstone HW (All Units Complete)

Assigned after all MLUs are marked as **mastered**. This is the final synthesis assessment.

### Purpose
Demonstrate holistic understanding by combining all concepts into a coherent deliverable. Serve as the "graduation" artifact.

### Assignment Template

> **Capstone HW: <Topic> Mastery Project**
>
> You''ve completed all units! Now prove your mastery with one of the following (choose your path):
>
> **Option A: Teach It** — Record yourself (or write a document) explaining the entire topic to a complete beginner. Must cover all MLUs in a logical flow.
>
> **Option B: Build It** — Create a working project that uses every concept from the path. Include a README explaining which concept each part uses.
>
> **Option C: Debug It** — Given a broken piece of code/scenario, identify all issues, fix them, and explain why each fix works.
>
> **Deliverable Requirements:**
> - Must reference at least 8 of the 10 units
> - Must include at least 1 diagram or visual aid
> - Must include a self-assessment: what are you still unsure about?

### Scoring Rubric (Capstone HW)

| Criterion | 3 points | 2 points | 1 point | 0 points |
|---|---|---|---|---|
| **Coverage** | ≥ 8 units referenced meaningfully | 5–7 units | 3–4 units | < 3 units |
| **Integration** | Concepts woven together with clear relationships shown | Concepts present but siloed | Minimal integration | No connection between concepts |
| **Correctness** | Zero factual errors in content/demonstration | Minor errors that don''t affect understanding | Multiple errors | Fundamentally flawed |
| **Communication** | Could genuinely teach a beginner; clear visuals | Understandable but not beginner-friendly | Confusing in places | Incomprehensible |
| **Self-assessment** | Identifies specific remaining gaps honestly | General reflection | Superficial ("I''m good!") | None |

**Pass threshold:** ≥ 12 / 15 points
**Below threshold:** Identify weakest areas and run a focused review cycle on those units before re-submitting.

---

## Homework Integration with State

When homework is assigned and scored, update `progress.md` and `state.json`:

### progress.md addition

When homework is assigned (before submission):
```markdown
### Homework Assigned: <Type> for <Unit/Phase> — <Date>
- **Status**: pending
- **Due**: before next unit / session
- **Tasks**: <brief list>
```

When homework is scored:
```markdown
### Homework Scored: <Type> for <Unit/Phase> — <Date>
- **Score**: X / Y
- **Passed**: Yes / No
- **Weak areas identified**: <list>
- **Action taken**: <if failed, what was done>
```

### state.json update

Use the `homework` object to track per-assignment lifecycle:

On Unit HW failure:
```json
{
  "current_unit": 3,
  "homework": {
    "unit_2": {
      "status": "retry_pending",
      "attempts": 1,
      "latest_score": 4
    }
  },
  "struggling_with": ["wrapper return path", "replacement model"],
  "pending_homework": "unit_2_alternate_hw",
  "blocked_on": "unit_2_homework_retry"
}
```

On Unit HW pass:
```json
{
  "current_unit": 3,
  "homework": {
    "unit_2": {
      "status": "passed",
      "attempts": 1,
      "latest_score": 7
    }
  },
  "struggling_with": [],
  "pending_homework": null,
  "blocked_on": null
}
```

On homework pass:
- Remove related concept from `struggling_with` if present.
- Clear `blocked_on` and `pending_homework` when the passing homework matches the blocked requirement.
- Add to `mastered_concepts` only if it was a novel extension (not just the same unit).

**`current_unit` does NOT increment when Unit HW fails.** It only advances after both mastery AND homework pass.

---

## Failure Remediation Protocol

When homework score is below the threshold:

| Failures in a row | Action |
|---|---|
| 1 | Targeted review of weak areas, retry homework |
| 2 | Re-teach the unit from Intuition with new analogy, then assign alternate homework |
| 3 | Pause progress; schedule a "review session" covering all `struggling_with` items before moving forward |

Never advance to a new unit while the previous unit''s homework has failed 3 times without intervention.

---

## Adaptive Homework Design

Adjust homework difficulty based on the user''s assessed level:

| User level | Homework adjustment |
|---|---|
| Complete beginner | More scaffolding, simpler problems, more time |
| Some exposure | Standard problems as written |
| Comfortable / Advanced | Remove scaffolding, add open-ended challenges, reduce time estimate |
| Experienced (filling gaps) | Skip warm-up HW; assign only gap-targeted problems |

The learning_style from Phase 0 also adjusts format:
- **Reading** → More written explanation tasks
- **Hands-on** → More coding/building tasks
- **Visual** → Include diagram/drawing requirements
- **Mix** → Rotate between types