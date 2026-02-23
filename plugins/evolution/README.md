# evolution

Error analysis and self-improvement skills for Claude Code agents.

## Skills

### evo

Analyze mistakes, extract root causes, and evolve AGENTS.md to prevent recurrence.

**Workflow:**
1. Identify and classify the error (code, process, communication, safety, style)
2. Root cause analysis — what assumption was wrong? what step was skipped?
3. Formulate an actionable, testable rule
4. Propose an update to AGENTS.md (with user approval)
5. Log the evolution to EVOLUTION_LOG.md

**Invoke:** `/evolution:evo`

## Install

```bash
/plugin marketplace add amplifier-ai/amplifier-skills
/plugin install evolution@amplifier-ai-amplifier-skills
```
