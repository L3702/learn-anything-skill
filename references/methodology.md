# Progressive Learning Methodology

## The Intake-First Principle

Never start teaching without first understanding the user''s starting point. A plan built on wrong assumptions wastes everyone''s time. The intake phase is non-negotiable — even if the user seems eager to jump in, complete the assessment first.

### Multiple-Choice Assessment

All intake questions must be presented as multiple choice. This makes it easy for the user to respond and gives you clean, structured data.

**Rules:**
- Offer 4–5 options per question, covering a clear spectrum.
- Make options concrete and behavioral, not abstract. ("I can write a basic loop" vs. "I know programming.")
- Never ask "How much do you know about X?" as an open-ended question — always attach choices.
- Ask 3–5 questions total during intake.

**Example question patterns:**

1. Experience level:
   - (A) None — complete beginner
   - (B) A little — read about it / watched videos
   - (C) Some — tried it a few times
   - (D) Comfortable — know the basics, want depth
   - (E) Experienced — use it regularly, filling gaps

2. Confidence with a sub-skill:
   - (A) Never heard of it
   - (B) Heard of it but couldn''t use it
   - (C) Can use it with reference/docs
   - (D) Can use it from memory
   - (E) Can teach it to others

3. Learning style:
   - (A) Reading and conceptual explanations
   - (B) Hands-on practice and exercises
   - (C) Visual demonstrations or diagrams
   - (D) Mix of everything

4. Goal / target proficiency:
   - (A) Functional literacy — understand and follow along
   - (B) Job-ready — independently handle real tasks
   - (C) Advanced — deep understanding, optimize and teach
   - (D) Focused — learn one specific sub-skill

### Plan Design Rules

- Each topic decomposes into 5–10 minimum learnable units (MLUs).
- Each MLU covers exactly one concept, takes 15–30 minutes.
- Order MLUs so prerequisites come before dependent topics.
- Mark optional "deep dive" units that can be skipped without breaking continuity.
- **Always explicitly state which units are skipped** because the user already knows that material.

### Presenting the Plan

The plan is a contract with the user. Present it clearly:

1. Restate their level (shows you listened).
2. List all MLUs with effort estimates.
3. Highlight adaptations ("Since you know X, we skip units 1–2").
4. Ask for approval before teaching begins.

## The Teaching Sequence (Fixed Order)

Every MLU is taught in this exact order. Never skip or reverse.

### Step 1: Motivation (Why care?)

Open with a real-world problem or pain point. Make the user *feel* the need for this concept before explaining what it is.

- "You have 10,000 rows. Finding duplicates manually takes hours. This makes it 3 seconds."
- Concrete > abstract. Always.

### Step 2: Analogy (What is it like?)

Bridge from the known to the unknown with a vivid everyday comparison.

- "A JOIN is like matching two spreadsheets by a common column."
- The analogy doesn''t need to be perfect — it needs to make the concept feel familiar.

### Step 3: Intuition (What''s the mental model?)

Build gut-level understanding before formal terms.

- Use ASCII diagrams, step-by-step walkthroughs, or visual descriptions.
- "A pointer is like a sticky note with an address — it tells you where to find something, not what it is."

### Step 4: Definition (Formal terms)

Only now introduce precise terminology and rules.

- "In technical terms: a pointer is a variable storing a memory address."
- The user now has a mental hook for the formalism.

### Step 5: Socratic Check

Two types of verification:

**Type A: True/False (1–2 questions)**
- Quick core understanding checks.
- "True or False: A pointer stores the actual data."

**Type B: One-Sentence Production (exactly 1)**
- Ask the user to synthesize in their own words.
- "In one sentence, explain why we need pointers instead of just variables."
- Not a recitation — a mini teach-back.

**Decision tree:**
- All correct → proceed.
- T/F wrong → re-explain that piece, ask new T/F.
- Production vague → give a hint, let them retry. If still stuck → re-teach Intuition with new analogy.

### Step 6: Hands-On Practice

Two parts:

**Part A: Guided Exercise**
- Concrete, small-scope task done right now.
- Show sample answer only after they try.

**Part B: Teach-Back**
- "Explain this to me as if I''m a complete beginner."
- Forces active knowledge construction. Reveals hidden gaps.

### Step 7: Active Recall Test (Exactly 2 Questions)

Designed to distinguish real understanding from illusion of competence.

Design rules:
- Never reuse Socratic check questions.
- Test application/transfer, not verbatim recall.
- At least 1 question combines this concept with a previous one.

Decision tree:
- 2/2 correct → mark unit as **mastered**.
- 1/2 correct → note the gap, re-explain briefly, ask 1 new recall question.
- 0/2 correct → re-teach from Intuition with new analogy, re-run test.

### Step 8: Update Records

After mastery:
1. Append a section to `progress.md` with status, comprehension, observations.
2. Update `state.json` (current_unit, completed_units, mastered_concepts, struggling_with, last_session).

### Step 8.5: Assign Homework

After updating records, assign homework per `references/homework.md`:
- **After each unit** → Unit HW (reinforce & extend)
- **After Phase 0 plan approval** → Pre-study HW (readiness)
- **At session resume** → Warm-up HW (combat forgetting)
- **After all units complete** → Capstone HW (synthesis)

Score homework using the rubrics. On failure, follow the remediation protocol (max 3 failures before mandatory review session). Record scores in `progress.md` and update `state.json` (`struggling_with`, `homework_failures`, `pending_homework`, `blocked_on`).

### Step 9: Homework Gate Before Next Unit

Before starting a new unit, check `state.json` for `blocked_on`:
- If `blocked_on` is set → new units are locked. Warm-up HW does NOT clear this gate.
- Only passing the required homework (score ≥ threshold) clears the block and unlocks the next unit.
- If `pending_homework` exists, it must be completed before new teaching begins.

**Warm-up HW vs Unit HW relationship:**
- Warm-up HW tests recall of previously mastered units. Passing it is required to resume.
- Unit HW tests extension and application of a specific unit. Failing it blocks the NEXT unit.
- Warm-up pass CAN clear `struggling_with` (recall-level) but CANNOT clear `blocked_on` (application-level).
- A Unit HW failure can only be cleared by passing the alternate Unit HW.

After mastery:
1. Append a section to `progress.md` with status, comprehension, observations.
2. Update `state.json` (current_unit, completed_units, mastered_concepts, struggling_with, last_session).

### Step 9: Decide Next Action

- All units complete → final synthesis review.
- More units remain → ask user to continue or save and stop.
- Always end by saving state.json.

## Resuming Sessions

1. Read `state.json` for `current_unit` and `struggling_with`.
2. Read latest `progress.md` entry for context.
3. Quick recap of last mastered unit.
4. If `struggling_with` is non-empty: warm-up question on those before new material.
5. Proceed with next unit.

## Adaptation Heuristics

| Signal | Interpretation | Action |
|---|---|---|
| User answers quickly and correctly | Concept mastered or too easy | Skip ahead or go deeper |
| User hesitates but gets there | Understanding forming | One more example |
| User gives partial answer | Gap in prerequisite | Back up, fill the gap |
| User says "I''m lost" | Multiple gaps or wrong starting point | Return to last solid checkpoint |
| User asks tangential questions | Curiosity signal | Follow briefly, then anchor back |

## Multi-Topic Awareness

Users may learn multiple subjects simultaneously. Each topic has its own subdirectory under `D:\learn_anything_data\`. Cross-topic connections, when noticed, should be surfaced — they accelerate mastery.


## Quantitative Rubrics

These rubrics replace vague qualitative judgments with consistent 0–4 scoring.

### Production Answer Rubric

Use after the user answers the one-sentence production question.

| Criterion | 1 point | 0 points |
|---|---|---|
| **Correctness** | Core idea is factually right | Contains a factual error or misconception |
| **Specificity** | Names the concept or mechanism directly | Uses filler words only |
| **Completeness** | Addresses the "why" or "how", not just "what" | Only names the concept without explaining |
| **Own words** | Clearly paraphrased in user''s voice | Sounds like a textbook recitation |

**Scoring:** 4 → excellent, 3 → solid, 1–2 → needs guidance, 0 → fundamental misunderstanding

### Teach-Back Rubric

Use after the user attempts to explain the concept as if teaching a beginner.

| Criterion | 1 point | 0 points |
|---|---|---|
| **Structure** | Clear beginning → middle → end | Rambling, no transitions |
| **No jargon leakage** | Explains without leaning on the term itself | Uses term as a crutch without unpacking it |
| **Analogy or example** | Includes at least one concrete analogy or real-world example | Purely abstract |
| **Accuracy** | Zero factual errors | At least one wrong claim |

**Scoring:** 4 → could teach a class, 3 → solid, 1–2 → partial gaps, 0 → re-teach
