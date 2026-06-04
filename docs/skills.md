# Skills Management

nanobot supports agent skills following the [agentskills.io](https://agentskills.io) v1 open standard. Skills extend the agent's capabilities with specialized instructions, tools, and workflows.

## Built-in Skills

Nanobot ships with 12 built-in skills: `clawhub`, `cron`, `github`, `image-generation`, `long-goal`, `memory`, `my`, `skill-creator`, `summarize`, `tmux`, `update-setup`, `weather`.

Skills can be enabled/disabled per agent via `disabledSkills` in the config or through the WebUI.

## Managing Skills via WebUI

The **Settings → Skills** section provides:

- **List & search**: view all installed skills (builtin + workspace), with source badges and toggle switches
- **Create**: full SKILL.md editor with all standard fields (name, description, license, allowed-tools, always active, body)
- **View & edit**: inspect and edit workspace skills (builtin skills are read-only). Full syntax-highlighted markdown editor
- **Delete**: remove workspace skills
- **Enable/disable**: toggle any skill on/off without uninstalling

### AI-Powered Generation

Describe a skill in natural language and the configured LLM provider will generate a complete SKILL.md following the agentskills.io v1 standard. The generated content is pre-filled in the editor for review before saving.

## Multi-Registry Search

Search and install skills from 10 registries simultaneously:

| Registry | Type | Coverage |
|----------|------|----------|
| **ClawHub** (clawhub.ai) | CLI (`npx clawhub`) | 3K–13K skills |
| **skills.sh** (Vercel) | CLI (`npx skills`) | Universal cross-agent installer |
| **SkillsMP** (skillsmp.com) | REST API | 1.6M+ indexed files |
| **GitHub skill-md topic** | GitHub API | 576+ repos |
| **npm skill-md keyword** | npm Registry API | 91+ packages |
| **Anthropic Official** | GitHub API | `anthropics/skills` (146K★) |
| **addyosmani agent-skills** | GitHub API | Production-grade (48K★) |
| **LobeHub Marketplace** | CLI (`@lobehub/market-cli`) | 332K+ skills |
| **OpenPackage** | CLI (`opkg search`) | Universal packages |
| **AutoSkills (midudev)** | CLI (`npx autoskills`) | Auto-detected curated skills |

Registries can be enabled/disabled individually in `~/.nanobot/config.json` under `tools.skill_registries`.

## SKILL.md Format

Skills follow the standard SKILL.md format:

```yaml
---
name: my-skill           # lowercase, hyphens only, max 64 chars
description: >-          # what it does AND when to use it
  Description here.
license: MIT             # optional
allowed-tools: read_file write_file  # optional
always: false            # optional, nanobot extension
---

# Instructions (markdown body)
Step-by-step instructions for the agent.
```

## File Locations

- **Built-in skills**: `<package>/nanobot/skills/`
- **Workspace skills**: `~/.nanobot/workspace/skills/`
- Workspace skills override built-in skills with the same name
