# amplifier-skills

Shared Claude Code plugin marketplace for Amplifier.AI.

## Plugins

| Plugin | Version | Skills | Description |
|--------|---------|--------|-------------|
| [evolution](./plugins/evolution/) | 2026.02.23.1607 | `evo` | Error analysis and self-improvement — evolve project guidelines from mistakes |
| [jira-workflows](./plugins/jira-workflows/) | 2026.02.23.1609 | `issue-create`, `issue-refine`, `issue-organize-epic` | Jira issues with PubMed research and clinical context |

## Quick Start

```bash
# 1. Install Claude Code (if not installed)
npm install -g @anthropic-ai/claude-code

# 2. Start a Claude Code session
claude

# 3. Inside the session, add the marketplace (one time)
/plugin marketplace add amplifier-ai/amplifier-skills

# 4. Install plugins
/plugin install evolution@amplifier-ai-amplifier-skills
/plugin install jira-workflows@amplifier-ai-amplifier-skills

# 5. Restart the session
/exit

# 6. Start a new session and use the skills
claude
/evolution:evo
/jira-workflows:issue-create
/jira-workflows:issue-refine
/jira-workflows:issue-organize-epic
```

## Managing plugins

```bash
# Update to latest version
/plugin marketplace update amplifier-ai-amplifier-skills

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
