# Plan: Set Up Personal Skills in ~/.claude/skills/

**Goal:** Create your first personal skill in the user-level skills directory so it auto-loads in every Claude Code session without touching the superpowers core repo.

---

## Task 1 — Create the personal skills directory (2 min)

```bash
mkdir -p ~/.claude/skills
```

Verify it exists:
```bash
ls ~/.claude/skills
```

---

## Task 2 — Pick your first skill topic (2 min)

Choose one real workflow pain point you've experienced in a Claude session — something that went wrong, or that you had to explain from scratch. Good first candidates:

- A deploy or release checklist your agent always forgets steps from
- A code-review checklist specific to your stack or team standards
- A "before opening a PR" routine tailored to your repo's conventions
- A debugging approach for a tool/framework you use constantly (e.g. specific to Rails, Django, Next.js)

Write down **one sentence** describing the problem the skill solves. You'll use this as the `description` field.

---

## Task 3 — Create the skill directory and SKILL.md scaffold (3 min)

Replace `my-skill-name` with your chosen name (letters, numbers, hyphens only):

```bash
mkdir ~/.claude/skills/my-skill-name
```

Create `~/.claude/skills/my-skill-name/SKILL.md` with this scaffold:

```markdown
---
name: my-skill-name
description: Use when [specific triggering conditions — what situation prompts you to need this?]
---

# My Skill Name

## Overview

One or two sentences: what does this skill do and what's the core principle?

## When to Use

- [Situation 1 that triggers this skill]
- [Situation 2]
- NOT when: [counter-case where this skill doesn't apply]

## Steps

1. [First concrete action]
2. [Second concrete action]
3. [Third concrete action]

## Common Mistakes

- [What tends to go wrong + fix]
```

**Frontmatter rules (don't skip):**
- `name`: must match the directory name exactly
- `description`: start with "Use when..." — describe *when* to invoke it, not *what* it does. Max ~500 chars. Written in third person.
- Total frontmatter block: max 1024 characters

---

## Task 4 — Fill in the skill body (5–10 min)

Replace every placeholder with real, specific content from your own experience:

- **Overview:** State the core principle in plain language. If there's a non-obvious decision the agent must make, add a small flowchart (dot syntax). If it's a linear checklist, a numbered list is fine.
- **Steps:** Each step should be concrete enough that an agent reading it cold knows exactly what to do. No "TBD", no "as appropriate".
- **Common Mistakes:** Pull from actual sessions where things went wrong.

---

## Task 5 — Test the skill in a real session (5 min)

Open a new Claude Code session and trigger your skill:

```
/my-skill-name
```

Or describe a scenario that matches the `description` field and see if Claude loads and follows it correctly.

Check:
- Does the agent follow the steps in order?
- Does it stop at decision points correctly?
- Does any step need clarification because the agent interpreted it differently than you meant?

Fix any gaps you find, then re-test.

---

## Task 6 — Iterate on the description if triggering is unreliable (3 min)

If the skill doesn't auto-trigger when you'd expect it to (or triggers when it shouldn't), refine the `description` field:

- Make triggering conditions more specific (add symptoms, error messages, tool names)
- Remove any workflow summary from the description — the description should ONLY say *when*, never *what happens*

Re-test after each change.

---

## Done

Your skill is live. It will auto-load in every future Claude Code session.  
When you have a second skill topic ready, repeat Tasks 2–6. Don't batch-create skills without testing each one — untested skills have gaps you won't notice until the agent goes off the rails in a real session.
