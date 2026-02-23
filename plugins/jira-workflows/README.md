# jira-workflows

Jira issue workflows with medical research context and PubMed citations.

## Skills

### issue-create

Create well-structured Jira issues with clinical context, team assignments, and PubMed references.

**Workflow:**
1. Parse request and identify domain (clinical or technical)
2. Research — PubMed for clinical, codebase search for technical
3. Clarify requirements with the user
4. Determine structure — single issue or epic with linked issues
5. Create with proper sections: overview, requirements, acceptance criteria, references

**Invoke:** `/jira-workflows:issue-create`

### issue-refine

Enhance existing Jira issues with research, proper structure, and acceptance criteria.

**Workflow:**
1. Fetch the issue and identify gaps
2. Research — PubMed and/or codebase analysis
3. Show before/after comparison for approval
4. Apply changes only after explicit confirmation

**Safety:** never changes assignee/status, never removes existing content.

**Invoke:** `/jira-workflows:issue-refine`

### issue-organize-epic

Analyze existing issues, identify common themes, and group them into epics.

**Workflow:**
1. Fetch issues by project/board with JQL filters
2. Cluster by theme, problem area, or feature
3. Present proposed epics with issue grouping for approval
4. Create epics and link issues

**Safety:** always shows the plan before creating anything.

**Invoke:** `/jira-workflows:issue-organize-epic`

## Install

```bash
/plugin marketplace add amplifier-ai/amplifier-skills
/plugin install jira-workflows@amplifier-ai-amplifier-skills
```
