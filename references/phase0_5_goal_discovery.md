## Phase 0.5: Goal Discovery — When the User Doesn't Know What to Learn

**Activate this phase when any of these are true:**
- The user says "I don't know what to learn" or similar
- The user gives a vague direction ("automation", "web development", "data science") without a concrete topic
- The user has existing skills but can't articulate the next step
- The user says "I know X, what should I learn next?"

**If the user already has a specific topic (e.g., "I want to learn React"), skip directly to Phase 0.**

### Step 1: Inventory Existing Skills (Multiple Choice Only — MANDATORY)

First, understand what the user already knows. Ask 2–3 questions about their current skill set. **Every question MUST have 4-5 options. Never ask "Tell me what you know."**

**Question 1 — Primary skill level:**

> **Q: What best describes your current experience with [their main language/tool]?**
> - (A) Beginner — I've done tutorials but haven't built anything real
> - (B) Intermediate — I've built small projects on my own
> - (C) Upper-intermediate — I've completed multiple projects and can debug most issues
> - (D) Advanced — I'm comfortable with the ecosystem, libraries, and best practices

**Question 2 — Domain exposure:**

> **Q: Which areas have you worked with or explored?** (select all that apply)
> - (A) [Domain A — e.g., Web APIs for Python]
> - (B) [Domain B — e.g., Databases / SQL]
> - (C) [Domain C — e.g., Testing / Automation basics]
> - (D) [Domain D — e.g., CLI tools / Scripts]
> - (E) None of the above — I've only done basic coding exercises

### Step 2: Clarify the Vague Goal (Multiple Choice)

The user likely has a direction but can't name the specific topic. Help them narrow it down with structured questions.

**Question 3 — What triggers the goal:**

> **Q: What made you think about learning something new?**
> - (A) A specific task at work / for a project that I couldn't figure out
> - (B) I saw someone else do something cool and want to do the same
> - (C) I want to build something I have in mind (describe briefly)
> - (D) Career growth — I want to be more employable
> - (E) Curious about a field but don't know the specifics

**Question 4 — Concrete scenarios (present 3–4 options based on their vague direction):**

For a user who said "automation" with Python background, present:

> **Q: Which of these sounds closest to what you want to do?**
> - (A) Automate browser tasks — fill forms, scrape websites, test web apps
> - (B) Automate file / data processing — move files, transform Excel/CSV, batch rename
> - (C) Build a backend service — APIs, scheduled tasks, server automation
> - (D) Automate testing — write test suites that run automatically

Each option implies a concrete topic:
- (A) → Selenium / Playwright for browser automation
- (B) → Python scripting with pathlib, pandas, shutil
- (C) → FastAPI / Flask + cron / task queues
- (D) → pytest + CI/CD pipelines

### Step 3: Bridge the Gap — Show the Path

After the user picks a scenario, **explicitly show the bridge** from where they are to where they want to go.

Format:

> **Bridge Analysis**
>
> You know: [current skills from Q1 + Q2]
> You want: [chosen scenario from Q4]
>
> **The gap:** [specific concept/tool they haven't encountered yet]
>
> **Recommended learning path:** [Concrete topic name]
> - What you'll learn: [3–4 bullet points of concrete outcomes]
> - Why this bridges your gap: [one sentence connecting their current skill to the new topic]
> - Estimated scope: [X] units, roughly [Y] minutes each

**Example for the "automation" user who picked (A):**

> **Bridge Analysis**
>
> You know: Python basics, small personal projects
> You want: Automate browser tasks — fill forms, scrape websites
>
> **The gap:** Browser automation tools (Selenium/Playwright) and DOM interaction concepts
>
> **Recommended learning path: Browser Automation with Playwright**
> - What you'll learn: Launching browsers, finding elements, filling forms, taking screenshots, handling waits
> - Why this bridges your gap: You already know Python — Playwright is just a library that controls a browser using Python code
> - Estimated scope: 7 units, ~25 minutes each

### Step 4: Confirm and Transition to Phase 0

Present the recommended topic as a concrete proposal:

> Based on your answers, I recommend: **<Concrete Topic Name>**
>
> - This will teach you: [2–3 concrete outcomes]
> - It builds directly on: [what they already know]
> - Alternative paths: [1–2 other options they could pick instead]
>
> **Do you want to go with this, or would you prefer one of the alternatives?**

Once the user confirms a concrete topic, **immediately transition to Phase 0** (Knowledge Assessment) with that topic. The Goal Discovery answers become the context for Phase 0 — note what they already know and start the assessment from there.

**Key: Goal Discovery outputs a confirmed topic. Phase 0 assesses knowledge within that topic.**

### When to Trigger Goal Discovery Automatically

Use these heuristics to decide whether to activate Phase 0.5:

| User input pattern | Action |
|---|---|
| "I don't know what to learn" | Trigger Goal Discovery |
| "What should I learn next?" | Trigger Goal Discovery |
| "I know [X], I want to do [vague Y]" | Trigger Goal Discovery |
| "Teach me about [vague field]" (e.g., "web dev", "automation") | Trigger Goal Discovery |
| "I want to learn [specific tool/concept]" (e.g., "React", "Docker", "SQL") | Skip to Phase 0 |
| "Continue learning [topic]" | Skip to Phase 2 (Resume) |

---
