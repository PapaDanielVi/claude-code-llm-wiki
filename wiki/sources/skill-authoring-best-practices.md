---
title: "Skill Authoring Best Practices"
source: "https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices"
type: source
created: 2026-05-06
updated: 2026-05-06
description: "Guide for writing effective Skills that Claude can discover and use successfully."
tags:
  - "ai"
  - "claude"
  - "skills"
  - "agent-development"
  - "clippings"
---

## Summary

A practical guide on authoring Claude Skills (formerly Agent Skills) that covers core principles, structure patterns, and development workflows. Emphasizes conciseness, progressive disclosure, and iterative testing.

## Key Points

### Core Principles

1. **Concise is key** — Only add context Claude doesn't already have. At startup, only metadata (name/description) is pre-loaded. SKILL.md is read on-demand when the skill is relevant.

2. **Match specificity to task fragility** — Use high freedom (general guidance) for open-ended tasks; low freedom (exact scripts) for fragile operations like database migrations.

3. **Test with target models** — Skills work differently across Haiku, Sonnet, and Opus. What works for Opus may need more detail for Haiku.

### Skill Structure

- **YAML frontmatter**: `name` (max 64 chars, lowercase/hyphens only) and `description` (max 1024 chars, no XML tags)
- **SKILL.md body**: Keep under 500 lines
- **Naming**: Use gerund form (`processing-pdfs`, `analyzing-spreadsheets`)
- **Description**: Write in third person, include both *what* it does and *when* to use it

### Progressive Disclosure Patterns

1. **High-level guide with references** — SKILL.md as table of contents, link to detailed files
2. **Domain-specific organization** — Split by domain (finance.md, sales.md) to avoid loading irrelevant context
3. **Conditional details** — Show basics, link to advanced content only when needed

### Anti-Patterns

- Avoid Windows-style paths (use forward slashes)
- Don't offer too many options — provide defaults with escape hatches
- Keep references one level deep from SKILL.md
- Avoid time-sensitive information (use "old patterns" section instead)

### Development Workflow

**Build evals first**, then minimal instructions, then iterate:
1. Complete task without skill (identify gaps)
2. Create evaluation scenarios
3. Write just enough to pass evals
4. Test with real Claude instances
5. Observe and refine

### Advanced: Executable Scripts

- Scripts should **solve problems**, not punt to Claude
- Self-document constants with justified values
- Use validation scripts with verbose error messages
- Bundle scripts in `scripts/` alongside instruction files
- Use fully qualified MCP tool names (`ServerName:tool_name`)

## Connections

- [[context-management]] — Progressive disclosure relates to context optimization
- [[skill-design]] — Skill authoring is a form of skill design

## Notes

See also: [Skills overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for conceptual background on how Skills work.

The iterative development pattern (Claude A creates/refines, Claude B tests) mirrors pair-programming concepts applied to skill development.