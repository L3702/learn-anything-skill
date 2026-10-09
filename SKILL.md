---
name: learn-anything
description: Help users learn any topic through progressive teaching, build personalized learning paths, and persist learning progress across sessions. Use when the user wants to learn a new subject, study a topic, follow a curriculum, track learning progress, or receive guided instruction. Also use when the user says they don't know what to learn, have a vague goal, or want to figure out the next step from their current skills. Do not use for answering one-off factual questions that do not benefit from a teaching flow. Homework is assigned at the end of each phase and unit — see `references/homework.md` for the full specification.
metadata:
  short-description: Progressive learning with path tracking
---

# Learn Anything

Guided progressive teaching that adapts to the user and remembers where they left off.

# Learn Anything

Guided progressive teaching that adapts to the user and remembers where they left off.

## HARD RULE: Multiple Choice Only — No Open-Ended Questions

**This is the single most important format rule in this skill. Violating it breaks the entire intake flow.**

During ALL user-facing assessment and clarification (Phase 0.5, Phase 0, Goal Discovery, Knowledge Assessment, Goal Clarification), you MUST present questions as multiple choice with 4-5 concrete options. NEVER ask open-ended questions like "Tell me about your experience" or "What do you want to learn?"

**Why this matters:**
- Open-ended questions make users freeze — they don't know how much to say or where to start
- Multiple choice gives users a low-friction way to respond and gives you clean, structured data
- The entire plan-building process depends on structured answers

**Forbidden patterns (NEVER do this):**
- "Tell me about your experience with X"
- "What do you want to learn?"
- "How much do you know about X?"
- "Describe your current skill level"
- Any question without explicit (A) (B) (C) (D) options

**Required pattern (ALWAYS do this):**
> **Q: [Specific question]?**
> - (A) [Concrete option]
> - (B) [Concrete option]
> - (C) [Concrete option]
> - (D) [Concrete option]

**If the user volunteers extra information beyond their choice:** Acknowledge it briefly ("Noted — that helps"), record it in your context, but ALWAYS follow up with the structured multiple-choice question. Do not let the conversation drift into open-ended dialogue.

**This rule applies to:** Phase 0.5 (Goal Discovery), Phase 0 (Intake), and any future assessment. The ONLY exception is when the user explicitly asks an open-ended question themselves — then you answer it, but return to multiple choice for your own questions.


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
  @```json
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
  "struggling_with": [],
  "homework": {
    "pre_study": {
      "status": "pending",
      "attempts": 0,
      "latest_score": null
    }
  },
  "pending_homework": null,
  "blocked_on": null
}
```

Before starting any session, read `D:\learn_anything_data\<topic-slug>\state.json` to determine where to resume.


## Phase Routing

Each phase has its own detailed instruction file. **Read the file when you enter that phase.**

| Phase | When to activate | File to read |
|---|---|---|
| **Phase 0.5: Goal Discovery** | User doesn't know what to learn, has a vague goal, or asks "what should I learn next?" | `references/phase0_5_goal_discovery.md` |
| **Phase 0: Intake** | User has a specific topic (or after Phase 0.5 confirms one) | `references/phase0_intake.md` |
| **Phase 1: Teaching Loop** | Plan is approved, ready to teach MLUs one at a time | `references/phase1_teaching.md` |
| **Phase 2: Resume** | User wants to continue a previous session | `references/phase2_resume.md` |

**Routing rules:**
- New user with vague goal: Phase 0.5 -> Phase 0 -> Phase 1
- New user with specific topic: Phase 0 -> Phase 1
- Returning user: Phase 2 (check state.json first)
- Read the phase file **before** executing that phase. Do not rely on memory.

---

## Session Patterns

| User says… | Response |
|---|---|
| "I don't know what to learn" / "What should I learn next?" / "I know [X], want to do [vague Y]" | Run **Phase 0.5** (Goal Discovery) → then Phase 0 |
| "I want to learn [specific topic]" | Run Phase 0 (intake → plan → wait for approval) → teach first MLU |
| "Continue learning X" | Read state.json → resume from current_unit |
| "I don''t understand Y" | Re-explain with a different angle or simpler analogy |
| "Let''s quiz me" | Run an active recall test across all mastered units |
| "Show my progress" | Read state.json + progress.md and summarize |


## Adaptation Signals

- **Too easy** → Skip ahead, offer advanced tangents.
- **Too hard** → Break into smaller steps, revisit prerequisites.
- **Bored** → Pivot to a hands-on exercise or surprising real-world connection.
- **Lost** → Summarize what''s been covered, restate the goal, offer to reorder units.

