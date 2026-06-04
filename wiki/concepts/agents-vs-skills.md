---
title: "Agents vs Skills"
type: concept
created: 2026-05-06
updated: 2026-05-06
tags:
  - "agentic-ai"
  - "skill-design"
  - "architecture"
aliases:
  - "agent-vs-skill"
  - "agent-or-skill"
---

## Summary

The decision framework for choosing between Claude agents, skills, or the combination. The core distinction: skills are reusable operating procedures (what to do), agents are autonomous operators (doing it over time). Highest ROI typically comes from combining both.

## Decision Framework

### Use a Skill when
Repeatability matters more than autonomy. The work is about following standards, templates, or checklists.
- Code review checklist
- Refactoring rules
- Security review SOP
- API documentation format
- Test-writing conventions

**Team signal**: "Please remember to also..." → should become a skill.

### Use an Agent when
Work requires persistence + tool usage + judgment loops. Need to iterate until complete, coordinate multiple steps, maintain state.
- Investigate failing CI pipeline
- Upgrade dependencies across repos
- Trace production bug
- Scan codebase for dead code
- Triage backlog automatically

**Team signal**: "Can you continue until done?" → should become an agent.

### Use Agent + Skill when
Autonomous execution with company standards. Usually highest ROI.
- Security remediation agent + secure coding skill
- Refactor agent + architecture rules skill
- PR review agent + team checklist skill

## Golden Rule

If engineers **repeat instructions**, build a skill.
If engineers **repeat effort**, build an agent.
If both repeat, build **agent + skill**.

## Common Mistakes

1. **Everything = agent** → overengineering, expensive runtime, poor maintainability. If static instructions solve it, use a skill.
2. **Everything = skill** → manual babysitting, repeated prompting, no persistence. If it must keep working independently, use an agent.
3. **Monolithic skill** → one 10K-line "engineering-skill.md". Bad governance. Split into modular skills (backend-review, frontend-review, security-review, testing-standards, docs-style).

## Team Operating Model

- **Layer 1**: Shared Skills Library (eng leads own) — coding standards, PR review, testing, security, architecture
- **Layer 2**: Specialized Agents (platform/devprod own) — review-agent, CI failure agent, dependency agent
- **Layer 3**: Metrics — cycle time reduced, PR review latency, escaped defects, CI failures auto-fixed, eng hours saved

## Key Points

- Skills = reusable operating procedures; Agents = autonomous operators; Agent + Skill = highest ROI
- **Skill** when: repeatability matters more than autonomy (code review, refactoring, security review)
- **Agent** when: work requires persistence + tool usage + judgment loops
- **Agent + Skill** when: autonomous execution with company standards
- Golden rule: repeated instructions → skill; repeated effort → agent; both → agent + skill
- Common mistakes: everything = agent (over-engineering), everything = skill (manual babysitting), monolithic skill (bad governance)
- Team model: Shared Skills Library (L1) → Specialized Agents (L2) → Metrics (L3)
- Starter pack: 5 skills + 3 agents for 20-200 engineer org

## Connections

- Source: [[claude-agents-vs-skills]]
- Related: [[skill-design]]
- Related: [[skills-and-agents-rules]]

## Notes

Most companies don't need "AI agents." They need **3 good agents + 10 disciplined skills**. That produces real operational leverage.
