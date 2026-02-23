# CLAUDE.md

## Versioning

Version format: `YYYY.MM.DD.HHmm` (`date +"%Y.%m.%d.%H%M"`).

Bump the version in `.claude-plugin/plugin.json` **and** `.claude-plugin/marketplace.json` when changing skills.

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
