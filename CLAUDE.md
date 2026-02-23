# CLAUDE.md

## Versioning

Bump the plugin version in `.claude-plugin/plugin.json` when changing skills:
- **patch** (1.0.0 → 1.0.1): typos, wording fixes
- **minor** (1.0.0 → 1.1.0): new skills, workflow changes
- **major** (1.0.0 → 2.0.0): breaking changes to skill names or behavior

## Structure

```
plugins/<plugin-name>/
├── .claude-plugin/plugin.json    # name, version, description
├── README.md                     # plugin docs
└── skills/<skill-name>/SKILL.md  # skill definition
```

When adding a new plugin, also register it in `.claude-plugin/marketplace.json`.

## Skill Conventions

- YAML frontmatter: `name` and `description` only
- `description` starts with "Use when..." — triggering conditions, not workflow summary
- Skill content in English
- Keep skills generic — no hardcoded project-specific names or paths
