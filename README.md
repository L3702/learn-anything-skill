# learn-anything

A Codex skill for progressive, personalized learning with homework tracking.

## What It Does

`learn-anything` turns Codex into a structured tutor. Tell it "I want to learn X" and it guides you through:

1. **Intake** — Multiple-choice assessment of your current knowledge, goals, and learning style
2. **Planning** — A customized learning path broken into 5–10 minimum learnable units (MLUs)
3. **Teaching** — Each unit follows a fixed sequence: Motivation → Analogy → Intuition → Definition
4. **Verification** — Socratic checks (T/F + production), hands-on practice, teach-back, active recall
5. **Homework** — Auto-assigned after each phase with quantitative rubrics and remediation protocols
6. **Persistence** — All progress saved to `D:\learn_anything_data\<topic>\` for seamless session resumption

## Structure

```
learn-anything/
├── SKILL.md                          # Core instructions
├── agents/
│   └── openai.yaml                   # UI metadata
├── references/
│   ├── methodology.md                # Teaching methodology & rubrics
│   └── homework.md                   # Homework specification & scoring
└── assets/                           # Supporting files directory
```

## Data Storage

Learning records are stored per topic:

```
D:\learn_anything_data\
└── <topic-slug>\
    ├── plan.md          # Approved learning plan
    ├── progress.md      # Session-by-session progress log
    ├── state.json       # Machine-readable state for resuming
    └── assets/          # Topic-specific supporting files
```

## Key Features

- **Quantitative rubrics** — Every homework and assessment uses 0–4 scoring criteria, eliminating subjective judgment
- **Homework gates** — Units are locked until their homework passes; prevents advancing with shaky foundations
- **Dual-gate resume** — Warm-up HW (recall) and Unit HW (application) are independent; one never substitutes for the other
- **Remediation protocol** — Up to 3 homework failures trigger escalating intervention (review → re-teach → mandatory review session)
- **Adaptive difficulty** — Homework adjusts to user level (beginner → expert) and learning style (reading / hands-on / visual / mix)

## Installation

Copy the `learn-anything` folder to your Codex skills directory:

```bash
cp -r learn-anything $CODEX_HOME/skills/
```

Or clone this repo directly:

```bash
git clone https://github.com/L3702/learn-anything-skill.git $CODEX_HOME/skills/learn-anything
```

## Usage

```
You: I want to learn Python decorators
Codex: [Phase 0 intake → multiple-choice assessment]
Codex: [Presents learning plan for approval]
You: Looks good!
Codex: [Assigns Pre-study HW]
You: [Submits HW]
Codex: [Unit 1 teaching → Socratic check → Hands-on → Recall test]
Codex: [Unit HW assigned, state.json saved]
...
You: Continue learning Python decorators
Codex: [Reads state.json → Warm-up HW → resumes from checkpoint]
```