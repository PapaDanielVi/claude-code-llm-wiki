---
title: "Anatomy of the .claude folder"
type: source
created: 2026-05-15
updated: 2026-05-15
tags:
  - technology
  - self
aliases:
  - ".claude folder anatomy"
source: "https://x.com/akshay_pachaar/status/2035341800739877091"
author: "@akshay_pachaar"
published: 2026-03-21
---

# Anatomy of the .claude folder

A complete guide to CLAUDE.md, custom commands, skills, agents, and permissions.

## Summary

A complete guide to CLAUDE.md, custom commands, skills, agents, and permissions in the `.claude` folder. Covers project-level vs global directories, the role of CLAUDE.md as the primary instruction file, modular rules in `.claude/rules/`, deterministic behavior via hooks, reusable skills, agent subdirectories, and permission management through settings.json.

## Key Points

- **Project-level** `.claude/` — team configuration, committed to git
- **Global** `~/.claude/` — personal preferences, session history, auto-memory
- **CLAUDE.md** — loaded into system prompt; keep under 200 lines; include build/test commands, architectural decisions, non-obvious gotchas
- **CLAUDE.local.md** — personal overrides per project, auto-gitignored
- **`.claude/rules/`** — modular instructions with optional YAML `paths:` scoping
- **`.claude/hooks/`** — deterministic behavior control via events and exit codes
- **`.claude/skills/`** — reusable workflows with YAML frontmatter, auto-invoked or explicit
- **`.claude/agents/`** — specialized subagent personas with isolated context windows
- **settings.json** — `allow`/`deny` permission lists; `$schema` for VS Code autocomplete
- **5-step setup progression**: `/init` → settings.json → commands → rules → global CLAUDE.md

## Connections

- [[claude-skills]] — Skills directory and their relationship to CLI-installed skills
- [[model-context-protocol]] — MCP configuration can live in `.claude/`
- [[skill-design]] — Skill structure mirrors `.claude/skills/` pattern
- [[context-management]] — CLAUDE.md is the primary context management tool

## Notes

- The `.claude folder` is a protocol for telling Claude who you are, what your project does, and what rules to follow
- CLAUDE.md is the highest-leverage file — get that right first
- Personal skills go in `~/.claude/skills/`, project skills in `.claude/skills/`