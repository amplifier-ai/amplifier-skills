# amplifier-skills

Shared Claude Code plugin marketplace for Amplifier.AI.

## Plugins

### evolution

Error analysis and self-improvement skills for Claude Code agents.

| Skill | Description |
|-------|-------------|
| `evo` | Analyze mistakes, extract lessons, and update AGENTS.md to prevent recurrence |

## Installation

### Prerequisites

- [Claude Code](https://claude.com/claude-code) CLI installed
- GitHub SSH access configured (`ssh -T git@github.com` should work)

### Step 1: Add the marketplace

Run inside any Claude Code session:

```
/plugin marketplace add amplifier-ai/amplifier-skills
```

This registers the marketplace globally. You only need to do this once.

### Step 2: Install a plugin

```
/plugin install evolution@amplifier-ai-amplifier-skills
```

### Step 3: Verify

Start a new Claude Code session. The skill should appear in the available skills list.
Invoke it with:

```
/evolution:evo
```

### Updating

To get the latest version of plugins:

```
/plugin marketplace refresh amplifier-ai-amplifier-skills
```

### Uninstalling

```
/plugin uninstall evolution@amplifier-ai-amplifier-skills
/plugin marketplace remove amplifier-ai-amplifier-skills
```

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
