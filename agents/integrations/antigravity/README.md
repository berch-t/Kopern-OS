# Antigravity Integration

Installs the full Agency roster as Antigravity skills. Each agent is prefixed
with `kopern-os-` to avoid conflicts with existing skills.

## Install

```bash
./scripts/install.sh --tool antigravity
```

This copies files from `integrations/antigravity/` to
`~/.gemini/antigravity/skills/`.

## Activate a Skill

In Antigravity, activate an agent by its slug:

```
Use the kopern-os-frontend-developer skill to review this component.
```

Available slugs follow the pattern `kopern-os-<agent-name>`, e.g.:
- `kopern-os-frontend-developer`
- `kopern-os-backend-architect`
- `kopern-os-reality-checker`
- `kopern-os-growth-hacker`

## Regenerate

After modifying agents, regenerate the skill files:

```bash
./scripts/convert.sh --tool antigravity
```

## File Format

Each skill is a `SKILL.md` file with Antigravity-compatible frontmatter:

```yaml
---
name: kopern-os-frontend-developer
description: Expert frontend developer specializing in...
risk: low
source: community
date_added: '2026-03-08'
---
```
