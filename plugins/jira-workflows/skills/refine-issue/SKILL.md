---
name: refine-issue
description: Use when user asks to improve, refine, or enhance an existing Jira issue with better structure, clinical context, or PubMed references
---

# Refine Issue

Enhance existing Jira issues with research, proper structure, and clinical context.

## Workflow

1. **Fetch the issue** — read current content via `jira_get_issue`
2. **Identify gaps:**

   | Gap | Enhancement |
   |-----|-------------|
   | No clinical context | PubMed research + thresholds |
   | Vague requirements | Structured bullet list |
   | No acceptance criteria | Testable conditions |
   | No references | Citations with DOI/PMID |
   | Poor formatting | Markdown structure |

3. **Research** — PubMed search and/or codebase analysis as needed
4. **Show before/after** — present proposed changes to the user
5. **Wait for approval** — apply only after explicit confirmation
6. **Update the issue** — apply changes via `jira_update_issue`

## Safety

- **Always show changes before applying**
- **Wait for explicit approval**
- Do not change assignee or status
- Do not remove existing content — only add and restructure

## Tools

- `jira_get_issue` — fetch current issue
- `jira_update_issue` — apply changes
- `pubmed_search_articles` — find literature
- `pubmed_fetch_contents` — get article details
