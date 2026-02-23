# CLAUDE.md

This is a Claude Code **plugin marketplace** repository. It contains shared plugins with skills.

## Repository Structure

```
amplifier-skills/
├── .claude-plugin/
│   └── marketplace.json              # marketplace catalog (lists all plugins)
├── CLAUDE.md                         # this file
├── README.md                         # public docs with install instructions
└── plugins/
    └── <plugin-name>/
        ├── .claude-plugin/
        │   └── plugin.json           # plugin manifest (name, version, description)
        ├── README.md                 # plugin docs (workflow descriptions, invoke commands)
        └── skills/
            └── <skill-name>/
                └── SKILL.md          # skill definition (YAML frontmatter + instructions)
```

## Versioning

Format: `YYYY.MM.DD.HHmm` — generate with `date +"%Y.%m.%d.%H%M"`.

When changing a plugin, bump the version in **both** files:
1. `plugins/<plugin-name>/.claude-plugin/plugin.json`
2. `.claude-plugin/marketplace.json` (same plugin entry)

Also update the version in the root `README.md` plugins table.

## How to Add a New Skill to an Existing Plugin

1. Create `plugins/<plugin-name>/skills/<skill-name>/SKILL.md`
2. Write YAML frontmatter + skill content (see Skill Format below)
3. Add the skill to `plugins/<plugin-name>/README.md`
4. Bump plugin version (see Versioning)
5. Commit and push

## How to Add a New Plugin

1. Create the directory:
   ```
   mkdir -p plugins/<plugin-name>/.claude-plugin
   mkdir -p plugins/<plugin-name>/skills/<skill-name>
   ```

2. Create `plugins/<plugin-name>/.claude-plugin/plugin.json`:
   ```json
   {
     "name": "<plugin-name>",
     "version": "<YYYY.MM.DD.HHmm>",
     "description": "What this plugin does"
   }
   ```

3. Create `plugins/<plugin-name>/skills/<skill-name>/SKILL.md` (see Skill Format)

4. Create `plugins/<plugin-name>/README.md` with:
   - Plugin description
   - List of skills with workflow summaries and invoke commands
   - Install instructions

5. Register in `.claude-plugin/marketplace.json` — add to the `"plugins"` array:
   ```json
   {
     "name": "<plugin-name>",
     "description": "What this plugin does",
     "version": "<YYYY.MM.DD.HHmm>",
     "source": "./plugins/<plugin-name>",
     "category": "productivity"
   }
   ```

6. Add to the plugins table in root `README.md`

7. Commit and push

## Skill Format (SKILL.md)

```yaml
---
name: skill-name
description: Use when [specific triggering conditions]
---

# Skill Title

Brief description of what the skill does.

## Workflow

### Phase 1: ...
### Phase 2: ...

## Tools

- `tool_name` — what it does

## Rules

- Safety rules and constraints
```

### Skill Conventions

- **Frontmatter**: only `name` and `description` fields
- **`name`**: letters, numbers, hyphens only — must match directory name
- **`description`**: starts with "Use when..." — describe triggering conditions, NOT the workflow
- **Content**: English
- **Generic**: no hardcoded project-specific names, paths, or assignees
- **Safety**: always show plan before destructive actions, always ask for approval

## Installation (for users)

```bash
# Inside a Claude Code session:
/plugin marketplace add amplifier-ai/amplifier-skills
/plugin install <plugin-name>@amplifier-ai-amplifier-skills

# Update to latest:
/plugin marketplace update amplifier-ai-amplifier-skills

# Skills require session restart to take effect
```

## Naming Conventions

- **Plugin names**: noun or noun-phrase (`evolution`, `jira-workflows`)
- **Skill names**: verb-noun or noun-verb (`issue-create`, `issue-refine`, `evo`)
- Group related skills with a common prefix (`issue-create`, `issue-refine`, `issue-organize-epic`)
