# amplifier-skills

Shared Claude Code plugin marketplace for Amplifier.AI.

## Plugins

### evolution

Error analysis and self-improvement skills for Claude Code agents.

| Skill | Description |
|-------|-------------|
| `evo` | Analyze mistakes, extract lessons, and update AGENTS.md to prevent recurrence |

## Quick Start

```bash
# 1. Install Claude Code (if not installed)
npm install -g @anthropic-ai/claude-code

# 2. Start a Claude Code session
claude

# 3. Inside the session, add the marketplace (one time)
/plugin marketplace add amplifier-ai/amplifier-skills

# 4. Install the evolution plugin
/plugin install evolution@amplifier-ai-amplifier-skills

# 5. Restart the session
/exit

# 6. Start a new session and use the skill
claude
/evolution:evo
```

## Managing plugins

```bash
# Update to latest version
/plugin marketplace refresh amplifier-ai-amplifier-skills

# Uninstall
/plugin uninstall evolution@amplifier-ai-amplifier-skills

# Remove marketplace entirely
/plugin marketplace remove amplifier-ai-amplifier-skills
```

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- GitHub SSH access configured (verify: `ssh -T git@github.com`)

## Contributing

### Adding a skill to an existing plugin

1. Create `plugins/<plugin-name>/skills/<skill-name>/SKILL.md`
2. Add YAML frontmatter:
   ```yaml
   ---
   name: skill-name
   description: Use when [triggering conditions]
   ---
   ```
3. Commit and push

### Adding a new plugin

1. Create `plugins/<plugin-name>/.claude-plugin/plugin.json`:
   ```json
   {
     "name": "plugin-name",
     "version": "1.0.0",
     "description": "What this plugin does"
   }
   ```
2. Add skills under `plugins/<plugin-name>/skills/`
3. Register the plugin in `.claude-plugin/marketplace.json` under `"plugins"`
4. Commit and push
