# amplifier-skills

Shared Claude Code skills for Amplifier.AI projects.

## Skills

| Skill | Description |
|-------|-------------|
| `evo` | Error analysis & self-improvement — analyze mistakes and evolve AGENTS.md |

## Installation

### Option 1: Clone and register (recommended)

```bash
git clone git@github.com:amplifier-ai/amplifier-skills.git
claude plugin add /path/to/amplifier-skills
```

Skills become available as `/amplifier-skills:evo`.

### Option 2: One-time launch

```bash
claude --plugin-dir /path/to/amplifier-skills
```

### Option 3: Add to project settings

Add to your project's `.claude/settings.json`:

```json
{
  "pluginDirs": ["/path/to/amplifier-skills"]
}
```

## Usage

Once installed, invoke skills with the plugin prefix:

```
/amplifier-skills:evo
```

## Adding new skills

1. Create `skills/<skill-name>/SKILL.md`
2. Add YAML frontmatter with `name` and `description`
3. Commit and push

```
skills/
└── my-skill/
    └── SKILL.md
```
