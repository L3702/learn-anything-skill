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

**Decision rule (Progressive Reflection — never give the answer on first error):**

- Both correct → proceed to Step 4.
- **T/F wrong (1st attempt):** Do NOT reveal the correct answer. Instead, ask a guiding question that leads the user to discover their own mistake. Examples:
  - "Think about what happens when you try to JOIN three tables — does the statement still hold?"
  - "Remember the analogy we used. Does a pointer hold the data itself, or something else?"
  - Wait for the user to self-correct. Only if they get it wrong again → proceed to 2nd attempt.
- **T/F wrong (2nd attempt):** Give a partial hint — point to the specific part of the concept they're missing, but don't state the full answer. Example: "You're close, but think about what the word 'only' means in that statement."
- **T/F wrong (3rd attempt):** Now re-explain that specific piece, then ask a new T/F.
- **Production answer evaluation:** Use the **Production Answer Rubric** below.
  - Score 3–4 → proceed.
  - Score 1–2 (1st attempt) → Do NOT give the answer. Ask a probing question about the specific criterion they missed. Example: if they lacked specificity, ask "Can you name the exact mechanism instead of describing it generally?"
  - Score 1–2 (2nd attempt) → Give a targeted hint on the weakest criterion, but let them produce the final answer.
  - Score 1–2 (3rd attempt) → Re-teach the Intuition step with a different analogy.

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

### Reflection Principle (applies to ALL error correction)

**Never give the correct answer on the first error.** The goal is to build the user's ability to self-correct, not to memorize corrections.

**Three-tier response to any wrong answer:**

| Attempt | What you do | What you do NOT do |
|---|---|---|
| 1st wrong | Ask a guiding question that leads them to discover their mistake | Reveal the answer, re-explain, or give hints |
| 2nd wrong | Give a partial hint — narrow the search space but let them find the answer | State the full correct answer |
| 3rd wrong | Re-explain the concept, then ask a new question | — |

**Guiding question patterns (use these instead of giving answers):**
- "What made you think that?" — surfaces flawed reasoning
- "Can you think of a counterexample?" — tests if the answer always holds
- "How does this connect to [previous concept]?" — activates prior knowledge
- "What would happen if we changed one variable?" — tests understanding of causality
- "Remember the analogy — does your answer fit?" — bridges back to intuition

**Exception:** If the user explicitly says "just tell me the answer" or shows frustration after 2 attempts, give the answer directly. The reflection process should feel like a puzzle, not a punishment.

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
  "struggling_with": [],
  "homework": {
    "unit_1": {
      "status": "pending",
      "attempts": 0,
      "latest_score": null
    }
  },
  "blocked_on": null,
  "pending_homework": null
}
```

Note: `current_unit` advances to N+1 only after the unit is mastered AND its homework is passed. If homework fails, `current_unit` stays at N until the alternate homework passes.

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
