---
title: "Best practices for skill creators"
type: "source"
created: 2026-05-06
updated: 2026-05-06
tags:
  - "skill-design"
  - "agentic-ai"
  - "prompting"
aliases:
  - "agentskills-best-practices"
---

## Summary

Guide on writing well-scoped, calibrated skills for AI agents. Focuses on grounding skills in real domain expertise, iterative refinement, context optimization, and prescriptive vs. flexible instruction patterns.

## Key Points

### Source from Real Expertise
- Skills grounded in specific domain context outperform generic ones
- Extract patterns from hands-on task execution (steps that worked, corrections made, I/O formats)
- Synthesize from project artifacts: runbooks, API specs, code review comments, incident reports

### Refine with Real Execution
- First draft needs revision — execute, then iterate
- Read execution traces for patterns: vague instructions, irrelevant instructions, too many options
- Aim for "execute-then-revise" cycles, especially for complex domains

### Spend Context Wisely
- Add what agent lacks, omit what it knows
- Focus on: project conventions, domain procedures, edge cases, specific tools/APIs
- Keep SKILL.md under 500 lines / 5,000 tokens; use `references/` for detailed content

### Calibrate Control
- **Freedom**: multiple valid approaches, task tolerates variation → explain *why*
- **Prescriptive**: fragile operations, consistency matters, specific sequence required → exact steps
- Provide defaults over menus; procedures over declarations

### Effective Instruction Patterns
- **Gotchas**: concrete corrections for mistakes agents make without being told
- **Templates**: concrete output format examples (better than prose descriptions)
- **Checklists**: for multi-step workflows with dependencies
- **Validation loops**: do work → validate → fix → repeat until passing
- **Plan-validate-execute**: for batch/destructive operations

## Connections

- Related: [[skill-design]], [[optimizing-skill-descriptions]], [[skills-and-agents-rules]]

## Notes

High-value insight: The "gotchas" section is often the most valuable content — concrete environment-specific corrections that prevent agent mistakes.

Another key insight: Write reusable *methods* (generalizable approaches) rather than specific *answers* (only useful for one task).

---
Source: [agentskills.io](https://agentskills.io/skill-creation/best-practices)