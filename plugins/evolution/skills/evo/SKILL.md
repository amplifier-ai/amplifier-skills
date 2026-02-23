---
name: evo
description: Use when the user identifies a mistake, says "/evo", or wants to analyze an error and evolve project guidelines to prevent future recurrence
---

# EVO: Error Analysis & Self-Improvement

Analyze mistakes, extract lessons, and update project guidelines to prevent recurrence.

## Workflow

### 1. Identify the Error

If not already clear, ask the user to describe or reference the mistake. Review recent conversation context. Classify:

- **Code error**: incorrect logic, syntax, wrong API usage
- **Process error**: skipped validation, didn't run tests, ignored pre-commit
- **Communication error**: misunderstood requirements, made assumptions
- **Safety error**: destructive action, lost work, broke existing functionality
- **Style error**: violated project conventions

### 2. Root Cause Analysis

Identify the **root cause**, not the symptom:
- What assumption was wrong?
- What step was skipped that would have caught this?
- What information was missing?
- Was there a recognizable pattern?

### 3. Formulate the Lesson

Write a concise, actionable rule. It must be:
- **Specific** — addresses the exact failure mode
- **Actionable** — clear steps to follow
- **Testable** — can verify compliance
- **Minimal** — no unnecessary process

### 4. Find the Guidelines File

Locate the project guidelines file to update:

1. Check if `AGENTS.md` exists in the repo root — if yes, use it
2. Otherwise, use `CLAUDE.md`

Read the file and find the appropriate section for the new rule.
Check if a similar rule already exists that should be updated instead.

### 5. Propose the Update

Show the user the proposed addition/modification. Explain why this rule would have prevented the error. **Get explicit approval before making changes.**

### 6. Apply the Update

After approval:
1. Edit the guidelines file with the approved change
2. Run `pre-commit run --files <file>` to validate formatting (if pre-commit is configured)
3. Summarize the change

### 7. Log the Evolution

If `EVOLUTION_LOG.md` exists, append an entry using **Context / Action / Goal** format:

```markdown
## YYYY-MM-DD: Brief title

**Context:** What went wrong and why.

**Action:** What rule was added/modified.

**Goal:** What this change prevents in the future.
```

Run `pre-commit run --files EVOLUTION_LOG.md` to validate (if pre-commit is configured).

### 8. Confirm Understanding

Restate the lesson learned. Acknowledge the error and commit to following the new rule.

## Example

User says "/evo" after forgetting to run tests before proposing a change.

Lesson: "Always run relevant tests (`pytest <path>`) before proposing code changes that modify behavior. If tests cannot be run, explicitly state why and outline validation plan."
