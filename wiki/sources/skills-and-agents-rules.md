---
title: Skills and Agents Rules
type: source
created: 2026-05-06
updated: 2026-05-06
tags: [skill-design, agentic-ai, agentic-workflows, context-management]
aliases: [skills-rules, agents-rules, gathered-skills-rules]
---

# Skills and Agents Rules

## Summary

A comprehensive guide covering the philosophy, mechanics, and best practices for building and managing AI Agent Skills — portable, version-controlled knowledge packages that agents load on demand. Covers progressive disclosure architecture, skill folder structure, SKILL.md format, and operational rules for effective agentic workflows.

## Key Points

### Why Agent Skills?
Skills package procedural knowledge and context into portable folders that agents load on demand, providing:
- **Domain expertise**: Capture specialized knowledge (legal review, data analysis, presentation formatting)
- **Repeatable workflows**: Turn multi-step tasks into consistent, auditable procedures
- **Cross-product reuse**: Build once, use across any skills-compatible agent

### How Agent Skills Work — Progressive Disclosure (3 stages)
1. **Discovery**: Agents load only name + description at startup
2. **Activation**: Full `SKILL.md` instructions loaded when task matches skill description
3. **Execution**: Agent follows instructions, optionally running bundled scripts

### Operational Rules (19 rules)
1. Always write back learned rules to `.claude/rules/` — learn from mistakes
2. Write back context given by developer to prevent incomplete context
3. Divide CLAUDE.md/GEMINI.md/CODEX.md into multiple files (context, rules, etc.) and reference them — reduces token usage
4. Skills = evolution of SOPs. If you have a SOP, you have a Skill. Skills self-improve over time.
5. Memory is very important in AI. Every project must have memory.
6. Avoid long chat sessions. Compact and move to new session to prevent high token usage.
7. Put context and memory to prevent higher token usage
8. Always instruct AI to update memory, context, and rules to prevent fact drift
9. Model stacking — don't use expensive models for easy tasks
10. Always plan before coding — use plan mode first, then code
11. Test skills with smallest models first. If skill works on small model, it's solid. Smaller models = basic eval, not flagship.
12. Tool splitting — use the right tool for the purpose: Claude Code, Claude Cowork, Claude Design, Claude Chat
13. Use multiple providers — Grok for news, GPT for brainstorming, Gemini for search/deep search
14. Always tell AI to ask questions rather than speculate
15. Use WisprFlow for voice dictation (optional)
16. Agent teams — sub-agents can communicate, but this is experimental, high token cost. Use git worktrees to avoid conflicts.
17. Always compact and switch sessions — lower token usage
18. Install and use `rtk` (Rust Token Killer) for reduced token usage on bash commands. Check with `rtk gain`
19. Always install and enable Caveman to reduce token usage

### Skill Folder Structure
```
.claude/skills/<skill-name>/
├── SKILL.md           # Instructions (required)
├── TEMPLATE.md        # Optional template
├── FORMS.md           # Supplemental guidance
├── REFERENCE.md       # Detailed APIs or examples
├── assets/            # Templates, resources
├── references/       # Docs or sample data (guide.md, etc.)
└── scripts/          # fill_form.py, utility.py, helper.sh
```

### SKILL.md Frontmatter Fields
| Field | Required | Constraints |
|---|---|---|
| `name` | Yes | Max 64 chars, lowercase/numbers/hyphens only |
| `description` | Yes | Max 1024 chars, describes what/when to use |
| `license` | No | License name or bundled license file |
| `compatibility` | No | Max 500 chars, environment requirements |
| `metadata` | No | Arbitrary key-value mapping |
| `allowed-tools` | No | Space-separated pre-approved tools (experimental) |

### Skills + Context Window Architecture
- Built-in skills: pptx, xlsx, docx, pdf, etc.
- Built-in agents: Bash, Glob, Grep, Read, Write, Edit, etc.
- Model stacking integration
- Claude Code CLI integration

## Connections

- **Concept**: [[skill-design]] — skill creation methodology
- **Concept**: [[context-management]] — context preservation strategies
- **Source**: [[skill-authoring-best-practices]] — guide for writing effective skills
- **Source**: [[best-practices-for-skill-creators]] — creator workflow best practices

## Notes

- Skills evolve from SOPs — capture institutional knowledge as portable instructions
- Progressive disclosure keeps many skills available with minimal context footprint
- File references should stay one level deep from SKILL.md to avoid nested chains
- Agent teams feature is experimental, high token cost — use git worktrees for parallel agent work

## Open Source Resources

- [agentskills/agentskills](https://github.com/agentskills/agentskills)
- [anthropics/skills](https://github.com/anthropics/skills)
- [garrytan/gstack](https://github.com/garrytan/gstack)
- [rtk-ai/rtk](https://github.com/rtk-ai/rtk) — token optimization
- [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) — token reduction
- [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) — memory for Claude Code