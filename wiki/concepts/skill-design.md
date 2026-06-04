---
title: "Skill Design"
type: "concept"
created: 2026-05-06
updated: 2026-05-07
tags:
  - "skill-design"
  - "agentic-ai"
  - "prompting"
aliases:
  - "skill-creation"
  - "skill-authoring"
---

## Summary

Skill design is the practice of creating reusable instruction sets (skills) that guide AI agents toward consistent, high-quality outputs in specific domains. Effective skill design requires grounding in real expertise, iterative refinement, and calibration of how prescriptive or flexible instructions should be. The "Chef's Skill" analogy captures the essence: an LLM without skills is like a chef without recipes — every dish is improvised, quality varies, and nothing is repeatable.

## Key Principles

### Real Expertise Foundation
Skills should be grounded in actual domain knowledge rather than generic best practices. See: [[best-practices-for-skill-creators]]

### Context Optimization
Focus on what the agent *wouldn't know* — project conventions, domain procedures, edge cases, specific tools. Omit what the agent already knows.

### Rigid vs. Flexible

The most fundamental architectural distinction. **Default to rigid** — start with strict rules and loosen only when needed.

| | Rigid | Flexible |
|---|---|---|
| **When** | Specific steps or constraints must always be followed | Multiple valid approaches exist |
| **Instruction** | Exact steps, exact order | Guidelines, heuristics, principles |
| **Analogy** | Cooking recipe | Cooking philosophy |
| **Error handling** | Fail fast, refuse to proceed | Adapt, suggest alternatives |
| **Examples** | Testing workflows, deployment checklists, security reviews | Code review, architecture advice, creative writing |

### Calibration Spectrum
- **Flexible**: when multiple approaches are valid and explaining *why* helps
- **Prescriptive**: when fragile operations, consistency matters, or specific sequence required

### Progressive Disclosure
Keep core instructions in SKILL.md (under 500 lines / 5,000 tokens). Move detailed references to separate files, loaded on demand.

### Description Optimization
The `description` field in frontmatter is the primary trigger mechanism. Key principles:
- **Imperative phrasing**: "Use this skill when..." (not "This skill does...")
- **User intent focus**: what user is trying to achieve, not internal mechanics
- **Pushy**: explicitly list contexts, even without explicit keywords
- **Concise**: 1024 character hard limit

Testing descriptions:
- Design ~20 eval queries (8-10 should-trigger, 8-10 should-not-trigger)
- Include **near-misses** for should-not: share keywords but need different thing
- Run multiple times (3+) due to nondeterminism
- Avoid overfitting: use train/validation split (60/40)
- Select best iteration by validation pass rate, not last iteration

See: [[optimizing-skill-descriptions]]

## Effective Patterns

- **Gotchas**: concrete corrections for agent mistakes
- **Templates**: concrete output examples (better than prose)
- **Checklists**: for multi-step workflows
- **Validation loops**: do → validate → fix → repeat
- **Plan-validate-execute**: for batch operations

## Skill Architecture

### Types of Skills

**File-system skills**: One or more files on disk. The most common type — agent reads them to understand the task.

**Meta skills (skill-creators)**: Skills that create other skills. Define structure, frontmatter requirements, and evaluation frameworks.

**Model-prompt skills**: The skill *is* a prompt — a set of instructions for how the agent should behave. No files, just prompt-based guidance.

### Capability vs Workflow Skills

A taxonomy orthogonal to rigid/flexible — answers "WHAT should I build?" rather than "HOW prescriptive should instructions be?"

| | Capability Skills | Workflow Skills |
|---|---|---|
| **Purpose** | Teach Claude HOW to do something it can't do well | Capture YOUR specific process, standards, brand rules |
| **Obsolescence** | Become unnecessary as models improve | Never obsolete — about your standards, not Claude's ability |
| **Examples** | Create Word docs, fill PDFs, format spreadsheets | YouTube description format, content repurposing pipeline, pricing reply SOP |
| **Priority** | Build second | Build first — lasting value |

As Claude gets smarter, capability skills retire. Workflow skills compound. Build workflow skills first.

This axis is orthogonal to rigid/flexible: a workflow skill can be rigid (exact formatting rules) or flexible (adaptable tone). A capability skill can also be either. Capability/workflow answers "what to build"; rigid/flexible answers "how to write it."

### Skill Families

**Native Skills** (`native:*`): Built-in platform skills — file operations, web search, code execution. Always available, form the baseline.

**Superpowers Skills** (`superpowers:*`): Community-created skills that extend platform capability. Installed by users, add specialized expertise.

### Routing

When multiple skills could match a request:

- **Strict**: Exact match only
- **Prefix**: Match the beginning of a request (useful for skill families like `test-*`)
- **Cascade**: Try strict → prefix → fallback (most common)
- **Fallback**: Default skill when nothing else matches

### Skill Archetypes

**Dialectic Skills**: Back-and-forth refinement. Asks questions, proposes alternatives, iterates. Best for brainstorming, planning, design.

**Maximalist Skills**: Attempts full coverage of a broad task. Best for comprehensive reviews, audits, documentation.

### Session Lifecycle

Skills operate within: **Auth** → **Ignite** (load skill, read instructions) → **Operational** (execute workflow) → **Checkpoint** (save state) → **Cleanup** (finalize output).

### Error Posture

Default behavior when something goes wrong:
- **Fail-fast**: Stop immediately, report error
- **Graceful degradation**: Continue with reduced functionality
- **Retry with backoff**: Attempt again with increasing delays
- **Human escalation**: Stop and ask for help

### Triggerless Skills

Some skills activate based on context or explicit invocation (e.g., `/skill-name`) rather than tool calls. Useful for soft skills, meta-skills, and workflow orchestration.

### Bundled Resources

Skills can bundle dependencies: `references/` (docs, examples), `scripts/` (helper scripts), `assets/` (templates, resources). Keeps skills self-contained.

## Key Points

- **Rigid vs Flexible**: Default to rigid (strict rules) — loosen only when needed
- **Capability vs Workflow Skills**: Capability = how to do something; Workflow = your specific process. Build workflow skills first.
- **Description optimization**: Imperative phrasing, user-intent focus, under 1024 chars; test with ~20 eval queries (near-misses included)
- **Progressive disclosure**: Core instructions in SKILL.md (under 500 lines), details in separate loaded files
- **Session lifecycle**: Auth → Ignite → Operational → Checkpoint → Cleanup
- **Error posture**: Fail-fast, graceful degradation, retry with backoff, or human escalation

## Source

- [[best-practices-for-skill-creators]] — Guide for writing effective Skills
- [[optimizing-skill-descriptions]] — Trigger mechanism and description best practices
- [[claude-code-skill-patterns]] — Authorship patterns and triggering
- [[how-claude-code-works-large-codebases]] — Plugin distribution, organizational rollout patterns
- [[introducing-dynamic-workflows]] — Workflow orchestration at scale with parallel subagents

## Connections

- Related: [[context-management]], [[skill-authoring-best-practices]], [[agents-vs-skills]], [[skill-evaluation]]
- Sources: [[skills-and-agents-rules]], [[claude-code-skill-patterns]], [[claude-agents-vs-skills]], [[complete-guide-building-skills]], [[claude-skills-build-first-assistant]]

## Notes

Core insight: Write reusable *methods* (generalizable approaches) not specific *answers* (one-time solutions).

**Plugin distribution**: Plugins bundle skills, hooks, and MCP configurations into installable packages. Essential for organizational scale — prevents tribal knowledge and ensures consistent setup across all developers. One retail org built a skill connecting to internal analytics and distributed via plugin before broad rollout.

### Dynamic Workflows Integration

Workflow skills become especially powerful within dynamic workflows, where parallel subagents can each invoke the same skill set to tackle subtasks with consistent approaches. The orchestration layer manages convergence while skills provide the domain-specific "vocabulary" each agent uses.