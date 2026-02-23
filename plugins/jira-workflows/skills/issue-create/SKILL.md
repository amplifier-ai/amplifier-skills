---
name: issue-create
description: Use when user asks to create a Jira issue, says "create task", or needs a well-structured issue with clinical context and PubMed references
---

# Create Issue

Create well-researched Jira issues with proper structure, team assignments, and clinical references.

## Workflow

### Phase 1: Understand & Research

1. Parse the request — extract core intent
2. Identify domain: clinical (EVAR, TAVI, LAAC) or technical?
3. If clinical — search PubMed for relevant literature:
   - Use `pubmed_search_articles` to find papers
   - Use `pubmed_fetch_contents` for details
   - Collect citations with DOI/PMID links
4. If technical — search the codebase to understand current implementation

### Phase 2: Clarify Requirements

Ask the user if anything is unclear:

- Scope: single task or multi-team epic?
- Does it involve UI/visualization (Unity team)?
- Clinical validation needed?
- Priority level
- Acceptance criteria

### Phase 3: Determine Structure

| Teams Involved | Structure |
|----------------|-----------|
| 1 team | Single issue |
| 2+ teams | Epic + linked issues per team |

### Phase 4: Team Assignment

Assign based on domain:

| Team | Scope |
|------|-------|
| **Backend/Algorithms** | Measurements, algorithms, workspaces, data pipelines |
| **Frontend/UI** | Visualization, 3D rendering, user interface |
| **Design** | UX, mockups, user flows |
| **Clinical** | Validation, radiology review |

Ask the user for specific assignees if not obvious from project context.

### Phase 5: Create the Issue

**Required sections:**

- **Overview** — What and why (2-3 sentences)
- **Requirements** — Bullet list of deliverables
- **Acceptance Criteria** — Testable conditions

**Optional sections (add when relevant):**

- **Clinical Context** — Medical background, thresholds, guidelines
- **Technical Details** — Affected modules, APIs, data structures
- **References** — PubMed citations with DOI/PMID

### Issue Template

```markdown
## Overview
[Brief description of what needs to be done and why]

## Clinical Context
[Medical background, relevant thresholds, guideline references]

## Requirements
- [ ] Requirement 1
- [ ] Requirement 2
- [ ] Add tests with edge cases
- [ ] Google-style docstrings with references

## Acceptance Criteria
- [ ] Tests pass
- [ ] Pre-commit clean
- [ ] Measurements match published values (if clinical)

## References
- Author et al. Title. Journal. Year.
  https://doi.org/10.xxxx/xxxxx
```

## Tools

- `jira_create_issue` — create issues
- `jira_create_issue_link` — link related issues
- `pubmed_search_articles` — find literature
- `pubmed_fetch_contents` — get article details

## Rules

- Issue content is always in **English**
- Communicate with the user in **their language**
- Always ask clarifying questions before creating
- Show the proposed issue structure for approval before submitting
