---
name: issue-organize-epic
description: Use when user wants to triage, categorize, or group existing Jira issues into epics by problem area, theme, or feature
---

# Organize Issues

Analyze existing Jira issues, identify common themes, and group them into epics.

## Workflow

### Phase 1: Understand the Problem

Ask the user:
- **What problem or theme to group by?** — e.g. "iliac artery measurements", "workspace performance", "UI bugs"
- This is the lens for clustering. Without it, grouping is arbitrary.

### Phase 2: Collect Issues

1. Ask the user for the scope:
   - **Project or board**: which Jira project to scan?
   - **Filters**: status (open only? all?), date range, labels, components
   - **Exclude**: already linked to an epic? specific issue types?
2. Fetch issues using `jira_search` with JQL
3. For large result sets, paginate and collect all matching issues

### Phase 3: Analyze & Cluster

1. Read each issue's summary, description, and labels
2. Filter and group issues **through the lens of the stated problem**
3. Cluster into proposed groups — each group becomes a potential epic
4. Flag issues that are related but don't fit neatly into any cluster
5. Flag issues that are clearly unrelated to the problem

### Phase 4: Present Plan

Show the user a table of proposed epics:

```
Epic: "Iliac Artery Measurements"
  - SCRUM-101: Add tortuosity index calculation
  - SCRUM-115: Fix diameter measurement at bifurcation
  - SCRUM-130: Add iliac angulation

Epic: "EVAR Workspace UX"
  - SCRUM-102: Redesign measurement table
  - SCRUM-118: Add export to PDF

Orphans (no epic):
  - SCRUM-140: Fix typo in report header
```

Ask for approval:
- Rename or merge epics?
- Move issues between groups?
- Skip any group?
- What to do with orphans?

### Phase 5: Create Epics & Link

After approval:

1. **Check for existing epics** — search for epics with similar names to avoid duplicates
2. **Create new epics** via `jira_create_issue` with epic issue type
3. **Link issues to epics** — set parent field on each issue:
   - Try `jira_update_issue` with `parent` field first
   - If that fails, use direct REST API v3:
     ```
     PUT /rest/api/3/issue/{KEY}
     {"fields": {"parent": {"key": "EPIC-KEY"}}}
     ```
4. **Report results** — show which issues were linked, flag any failures

### Phase 6: Summary

Present final report:

| Epic | Issues Linked | Status |
|------|---------------|--------|
| Epic name | 5 | OK |
| Epic name | 3 | 1 failed |

## Tools

- `jira_search` — find issues with JQL
- `jira_get_issue` — read issue details
- `jira_create_issue` — create epics
- `jira_update_issue` — set parent (link to epic)

## Rules

- **Always show the plan before creating anything**
- **Never move issues between epics without approval**
- Epic names and descriptions in **English**
- Communicate with the user in **their language**
- If an issue is already linked to an epic, skip it and report
- Prefer reusing existing epics over creating duplicates
