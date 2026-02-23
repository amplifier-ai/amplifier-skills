# amplifier-skills

Shared Claude Code plugin marketplace for Amplifier.AI.

## Plugins

### evolution

Error analysis and self-improvement skills for Claude Code agents.

| Skill | Description |
|-------|-------------|
| `evo` | Analyze mistakes, extract lessons, and update AGENTS.md to prevent recurrence |

## Installation

```bash
# Add marketplace (one time)
/plugin marketplace add amplifier-ai/amplifier-skills

# Install plugin
/plugin install evolution@amplifier-ai-amplifier-skills
```

Skills become available as `/evolution:evo`.

## Usage

```
/evolution:evo
```

## Adding new skills

1. Create `plugins/evolution/skills/<skill-name>/SKILL.md`
2. Add YAML frontmatter with `name` and `description`
3. Commit and push
