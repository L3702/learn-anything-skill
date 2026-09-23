---
name: learn-anything
description: Help users learn any topic through progressive teaching, build personalized learning paths, and persist learning progress across sessions. Use when the user wants to learn a new subject, study a topic, follow a curriculum, track learning progress, or receive guided instruction. Do not use for answering one-off factual questions that do not benefit from a teaching flow. Homework is assigned at the end of each phase and unit — see `references/homework.md` for the full specification.
metadata:
  short-description: Progressive learning with path tracking
---

# Learn Anything

Guided progressive teaching that adapts to the user and remembers where they left off.

## Data Storage

All learning records are stored externally at `D:\learn_anything_data\` (create if it does not exist).

**Directory structure:**

```
D:\learn_anything_data\
└── <topic-slug>\
    ├── plan.md          ← The approved learning plan
    ├── progress.md      ← Session-by-session progress log
    ├── state.json       ← Machine-readable progress state for resuming
    └── assets\          ← Any supporting files for this topic
```

- `<topic-slug>` is a URL-safe, lowercase, hyphenated version of the topic (e.g., `rust-programming`, `sql-data-analysis`).
- If the directory or any file does not exist yet, create it when first needed.
- `state.json` structure:

```json
{
  "topic": "SQL for Data Analysis",
  "started": "2026-09-23",
  "last_session": "2026-09-23",
  "starting_level": "beginner",
  "target_proficiency": "job-ready",
  "learning_style": "hands-on",
  "current_unit": 1,
  "total_units": 8,
  "completed_units": [],
  "mastered_concepts": [],
  "struggling_with": []
}
```

Before starting any session, read `D:\learn_anything_data\<topic-slug>\state.json` to determine where to resume.

## Phase 0: Intake — Before Teaching Begins

**Always complete this phase before presenting a learning plan or teaching anything.**

### Step 1: Knowledge Assessment (Multiple Choice Only)

Assess the user with structured multiple-choice questions. Let the user pick an option rather than asking open-ended questions. Ask 3–5 questions covering experience, confidence, and prerequisites.

**Format each question like this:**

> **Q: How much experience do you have with [topic]?**
> - (A) None — complete beginner
> - (B) A little — I''ve read about it or watched a video
> - (C) Some — I''ve tried it a few times but it feels shaky
> - (D) Comfortable — I know the basics and want to go deeper
> - (E) Experienced — I use it regularly but want to fill gaps

Cover these dimensions across your questions:

1. **Overall experience** — "How much experience do you have with [topic]?"
2. **Confidence with basics** — "Which best describes your comfort with the fundamentals?"
3. **Prerequisite check** — For key prerequisites, ask similarly structured questions.
4. **Practical exposure** — "Which statement matches your hands-on experience?"

### Step 2: Goal Clarification (Multiple Choice)

Ask the user to choose their goal from options:

> **Q: What''s your target proficiency?**
> - (A) Functional literacy — understand and follow along
> - (B) Job-ready — can independently handle real tasks
> - (C) Advanced — deep understanding, can optimize and teach others
> - (D) Focused — I want to learn one specific sub-skill

Also ask about learning style preference:

> **Q: How do you learn best?**
> - (A) Reading and conceptual explanations
> - (B) Hands-on practice and exercises
> - (C) Watching demonstrations or visual walkthroughs
> - (D) Mix of everything

### Step 3: Present the Learning Plan

Synthesize all answers into a concrete, written plan. Present it to the user for approval **before teaching starts**.

The plan must include:

1. **Starting point** — Where the user is now (based on assessment).
2. **End goal** — What success looks like.
3. **Milestone list** — 5–10 ordered units, each with:
   - A clear objective
   - Estimated effort (time)
   - Whether it is required or optional (deep dive)
4. **Adaptations** — Anything skipped, reordered, or added based on what the user already knows. Explicitly say: "Since you already know X, we''re starting from unit 3 instead of 1."
5. **First step** — What the very first session will cover.

Ask the user: "Does this plan look good, or would you like to adjust anything?" Wait for approval.

**Only after the user approves the plan should teaching begin.**

Save the approved plan to `D:\learn_anything_data\<topic-slug>\plan.md`, initialize `progress.md`, and create `state.json`.

## Phase 1: Unit-by-Unit Teaching Loop

After the plan is approved, teach **one unit at a time**. Each unit follows this fixed sequence — never skip steps or reverse the order.

### Step 1: Decompose Into Minimum Learnable Units

Break the topic into 5–10 **minimum learnable units (MLUs)**. Each MLU should:
- Cover exactly one core concept or skill
- Be learnable in 15–30 minutes
- Have a clear, verifiable outcome (the user can do X after learning it)
- Build on previous MLUs but be independently understandable

Present the full list of MLUs to the user with the plan.

### Step 2: Teach a Single MLU (Fixed Order)

**Never reverse this sequence. Always go: Motivation → Analogy → Intuition → Definition.**

#### 2a. Motivation (Why should I care?)

Start with **why** this concept matters. Use a real-world problem, a pain point, or a "before/after" scenario. Make the user feel the need to learn it.

- "Imagine you have 10,000 rows and need to find duplicates. Without this, you''d do it manually for hours. With it, it takes 3 seconds."
- Keep it concrete. No abstract "This is important in computer science."

#### 2b. Analogy (What is it like?)

Bridge from the known to the unknown with a vivid, everyday analogy.

- "A SQL JOIN is like matching two spreadsheets by a common column — like looking up a student''s name in one table and their grades in another."
- The analogy doesn''t need to be perfect; it needs to make the concept *feel familiar*.

#### 2c. Intuition (What''s the mental model?)

Build the user''s gut feeling for how it works before introducing formal terms.

- "Think of a pointer as a sticky note with an address on it — it doesn''t hold the actual object, it tells you where to find it."
- Use diagrams (ASCII), step-by-step walkthroughs, or visual descriptions.

#### 2d. Definition (What''s the precise meaning?)

Only now give the formal definition, terminology, and rules.

- "In programming terms, a *pointer* is a variable that stores a memory address."
- The user now has a mental hook to hang the formal definition on.

### Step 3: Socratic Check

After teaching the MLU, verify understanding with two types of questions:

**First: True/False (1–2 questions)**

Quick checks that the user grasped the core idea:

- "True or False: A JOIN can only combine two tables at a time."
- "True or False: A pointer stores the actual data it points to."

**Second: One-Sentence Production Question (exactly 1)**

Ask the user to produce an answer in their own words — not recite, but synthesize:

- "In one sentence, explain why we need JOINs instead of putting everything in one table."
- "In one sentence, what problem do pointers solve that raw variables don''t?"

**Decision rule:**
- Both correct → proceed to Step 4.
- T/F wrong → re-explain that specific piece, then ask a new T/F.
- Production answer evaluation: use the **Production Answer Rubric** below. Score 3–4 → proceed. Score 1–2 → give a guiding hint, let them retry. Score 1–2 again on second attempt → re-teach the Intuition step with a different analogy.

### Production Answer Rubric

Score the user''s one-sentence production answer on these 4 criteria (1 point each):

| Criterion | 1 point | 0 points |
|---|---|---|
| **Correctness** | Core idea is factually right | Contains a factual error or misconception |
| **Specificity** | Names the concept or mechanism directly | Uses filler words only ("it does stuff", "important for coding") |
| **Completeness** | Addresses the "why" or "how", not just "what" | Only names the concept without explaining |
| **Own words** | Clearly paraphrased in user''s voice | Sounds like a textbook recitation or copy-paste |

**Scoring:** 4 = excellent, 3 = solid, 1–2 = needs guidance, 0 = fundamental misunderstanding

### Teach-Back Rubric

Score the user''s teach-back explanation on these 4 criteria (1 point each):

| Criterion | 1 point | 0 points |
|---|---|---|
| **Structure** | Has a clear beginning and end (sets up the problem → explains → wraps up) | Rambling, jumps between ideas without transitions |
| **No jargon leakage** | Explains without using the concept''s name as a crutch (e.g., doesn''t say "pointers point to things") | Hides behind terminology without explaining what it means |
| **Analogy or example** | Includes at least one concrete analogy, metaphor, or real-world example | Purely abstract restatement |
| **Accuracy** | Zero factual errors in the explanation | Contains at least one wrong claim or implication |

**Scoring:** 4 = could teach a class, 3 = solid understanding, 1–2 = partial gaps, 0 = re-teach needed


### Step 4: Hands-On Practice

Two-part practice to move from "I get it" to "I can use it."

#### 4a. Guided Exercise

Give a concrete, small-scope task the user can complete right now:

- "Write a SELECT query that returns the 5 most recent orders from this sample table."
- "Write a function that takes a pointer and prints the value it points to."

Provide a sample answer only after the user tries.

#### 4b: Teach-Back

Ask the user to explain the concept as if teaching a beginner:

- "Pretend I know nothing about JOINs. Explain it to me in your own words."
- "How would you describe pointers to someone who just started programming?"

This forces active construction of knowledge and reveals gaps the T/F questions might miss.

**Decision rule:**
- Clean teach-back → proceed.
- Teach-back has holes → identify the specific gap, re-explain, and ask a mini teach-back on just that part.

### Step 5: Active Recall Test (2 Questions)

End each unit with exactly 2 recall questions. These are designed to distinguish **real understanding** from **recognition/illusion of competence**.

Design principles:
- Do NOT reuse questions from the Socratic check.
- Test application or transfer, not verbatim recall.
- Include at least 1 question that combines this concept with a previous one.

Examples:

1. "You have a table of orders and a table of customers. You need the total spend per customer. Which JOIN type do you use, and what''s the aggregation?"
2. "If two pointers point to the same memory address and one modifies the data, does the other see the change? Why?"

**Decision rule:**
- Both correct → mark unit as **mastered**, update `state.json` (add to `mastered_concepts`, increment `current_unit`).
- 1 wrong → add the concept to `struggling_with` in `state.json`, briefly re-explain, then ask 1 new recall question on that spot.
- Both wrong → the unit was not truly understood. Re-teach from Intuition with a new analogy, then re-run Step 5 with fresh questions.

### Step 6: Update Records

After the unit is mastered:

1. **Update `progress.md`** — append a section for this unit:

```markdown
### Unit N: <Concept Name> — <Date>
- **Status**: ✅ Mastered
- **Socratic check**: Passed on first/second try
- **Teach-back**: Clean / needed one hint
- **Recall test**: X/2 correct
- **Notes**: <observations about what clicked, what was hard, learning style insights>
```

2. **Update `state.json`**:

```json
{
  "current_unit": 2,
  "completed_units": [1],
  "mastered_concepts": ["JOIN basics"],
  "struggling_with": []
}
```

### Step 6.5: Assign Homework

After updating records for a mastered unit, assign homework per `references/homework.md`:

- **After each unit** → Unit HW (reinforce & extend)
- **After Phase 0 plan approval** → Pre-study HW (readiness)
- **At session resume** → Warm-up HW (combat forgetting)
- **After all units complete** → Capstone HW (synthesis)

Score homework using the rubrics in `references\homework.md`. On failure, follow the remediation protocol (max 3 failures before mandatory review session). Record scores in `progress.md` and update `state.json` (`struggling_with`, `homework_failures`).

### Step 7: Decide Next Action

After updating records:

- **All units complete** → run a final synthesis review (cross-unit connections, mini-project suggestion).
- **More units remain** → ask the user: "Ready to move on to Unit N+1, or would you like more practice on this one?" If the user seems tired or rushed, offer to save and continue later.

**Always end a session by saving state.json with `last_session` updated.**

## Phase 2: Resuming Sessions

When the user wants to continue:

1. Read `state.json` to find `current_unit` and `completed_units`.
2. Read the latest entry in `progress.md` for context.
3. Briefly recap the last mastered unit (1–2 sentences).
4. If there are items in `struggling_with`, do a quick 1-question warm-up on those before starting the next unit.
5. Proceed with Phase 1 (Step 2 onward) for the next unit.

## Session Patterns

| User says… | Response |
|---|---|
| "I want to learn X" | Run Phase 0 (intake → plan → wait for approval) → teach first MLU |
| "Continue learning X" | Read state.json → resume from current_unit |
| "I don''t understand Y" | Re-explain with a different angle or simpler analogy |
| "Let''s quiz me" | Run an active recall test across all mastered units |
| "Show my progress" | Read state.json + progress.md and summarize |

## Adaptation Signals

- **Too easy** → Skip ahead, offer advanced tangents.
- **Too hard** → Break into smaller steps, revisit prerequisites.
- **Bored** → Pivot to a hands-on exercise or surprising real-world connection.
- **Lost** → Summarize what''s been covered, restate the goal, offer to reorder units.
