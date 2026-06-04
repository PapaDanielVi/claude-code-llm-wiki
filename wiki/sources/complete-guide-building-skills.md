---
title: "The Complete Guide to Building Skills for Claude"
type: source
created: 2026-05-07
updated: 2026-05-07
tags:
  - skill-design
  - agentic-ai
  - prompting
aliases:
  - "building-skills-for-claude"
  - "complete-guide-skills"
  - "skill-guide"
---

## Summary

A comprehensive guide to creating, evaluating, and managing skills for Claude Code and compatible agents. Defines skills as file-based instruction sets that transform raw model capability into directed, domain-specific execution. Covers the full lifecycle from writing and organizing skills to evaluating them, with a particular focus on the rigid vs. flexible skill taxonomy, type-aware routing, and bundled resources.

## Key Points

### What is a Skill

A skill is a file — typically `SKILL.md` — containing instructions, constraints, and workflows that tell an agent what to do, how to behave, and when to act. Skills package domain expertise, repeatable procedures, and behavioral rules into portable, composable artifacts. They solve context pollution, token waste, and inconsistency by giving agents structured instructions instead of raw prompting.

**The "Chef's Skill" analogy**: An LLM is a chef that can cook anything. A skill is a recipe — specific instructions for a specific outcome. The chef has all the raw capability, but without recipes, every dish is improvised. Skills transform raw model capability into directed, repeatable, high-quality execution.

### Why Skills Matter

Without skills, you're relying on:
- **Memory** — hoping the model remembers past conversations (it doesn't)
- **Prompting** — pasting instructions into every message (wastes tokens, inconsistent)
- **Training** — fine-tuning the model (expensive, infrequent)

Skills provide a structured, portable, and composable alternative.

### Rigid vs. Flexible Skills

The most fundamental architectural distinction:

| | Rigid | Flexible |
|---|---|---|
| **When** | Specific steps or constraints must always be followed | Multiple valid approaches exist |
| **Instruction** | Exact steps, exact order | Guidelines, heuristics, principles |
| **Analogy** | Cooking recipe | Cooking philosophy |
| **Error handling** | Fail fast, refuse to proceed | Adapt, suggest alternatives |
| **Examples** | Testing workflows, deployment checklists, security reviews | Code review, architecture advice, creative writing |

**Default to rigid.** Start with strict rules and loosen only when needed. Most real-world tasks benefit from structured, repeatable procedures.

### Types of Skills

**File-system skills**: One or more files on disk. Agent reads them to understand the task. The most common type.

**Meta skills (skill-creators)**: Skills that create other skills. They define the structure, frontmatter requirements, and evaluation frameworks for new skills.

**Model-prompt skills**: The skill is a prompt — a set of instructions for how the agent should behave. No files, just prompt-based guidance.

### How Skills Work

1. **Agent discovers the skill** — reads name and description from the skill's frontmatter
2. **Agent decides to use it** — based on the task and the skill's description
3. **Agent reads the skill** — loads `SKILL.md` and any referenced files
4. **Agent executes** — follows the instructions, constrained by the skill's rules

**Frontmatter fields**:
- `name`: skill identifier (max 64 chars)
- `description`: when/why to use this skill (max 1024 chars) — the primary trigger mechanism
- `type`: rigid or flexible (optional)
- `license`, `compatibility`, `metadata`, `allowed-tools`: optional fields

### Native Skills vs. Superpowers Skills

The ecosystem has two families:

**Native Skills** (`native:*`): Built-in skills provided by the platform — file operations, web search, code execution. They're always available and form the baseline capability.

**Superpowers Skills** (`superpowers:*`): Community-created skills that extend platform capability. They're installed by users and enhance specific workflows. Examples: brainstorming, writing plans, debugging, code review.

Both families coexist — native skills provide the foundation, superpowers skills add specialized expertise.

### Skill Routing (Type-Aware Routing)

When multiple skills could match a request, routing determines which one activates:

- **Strict routing**: Exact match only. The skill name or description must precisely match the request.
- **Prefix routing**: Match the beginning of a request. Useful for skill families (e.g., `test-*` skills).
- **Cascade routing**: Try strict first, then prefix, then fallback. The most common pattern.
- **Fallback routing**: If nothing else matches, use a default skill. Prevents "no skill found" errors.

### Triggerless Skills

Some skills don't trigger on tool calls — they activate based on context, patterns, or explicit user invocation (e.g., `/skill-name`). Triggerless skills are useful for:
- Soft skills and coaching (communication, leadership)
- Meta-skills (skill creation, evaluation)
- Workflow orchestration (planning, brainstorming)

### Skill Evaluation

A 4-step method for testing whether a skill works:

1. **Should-Trigger Test**: Does the skill activate when it should? Run ~10 varied queries that the skill should handle.
2. **Constraint Test**: Does the skill follow its own rules? Test edge cases and boundary conditions.
3. **Ask Test**: Does the skill ask for clarification when needed? Test with ambiguous or incomplete inputs.
4. **Bad Behavior Test**: Does the skill refuse to do things outside its scope? Test with irrelevant or adversarial queries.

**Evaluation guardrails**:
- **Human-required tests**: Tasks that need human judgment (taste, context, ethics)
- **Agent-required tests**: Tasks that need tool access or computation
- **Constrained-language tests**: Tasks where the output must match a specific format or vocabulary

### Skill Archetypes

**Dialectic Skills**: Engage in back-and-forth refinement. The skill asks questions, proposes alternatives, and iterates. Best for: brainstorming, planning, design exploration.

**Maximalist Skills**: Try to do everything at once. The skill takes a broad task and attempts full coverage. Best for: comprehensive reviews, audits, documentation generation.

### Session Lifecycle

Skills operate within a session lifecycle:
1. **Auth** — verify permissions and access
2. **Ignite** — load skill, read instructions, initialize context
3. **Operational** — execute the skill's workflow
4. **Checkpoint** — save state, log progress
5. **Cleanup** — release resources, finalize output

### Error Posture

Defines default behavior when something goes wrong:
- **Fail-fast**: Stop immediately, report the error
- **Graceful degradation**: Continue with reduced functionality
- **Retry with backoff**: Attempt again with increasing delays
- **Human escalation**: Stop and ask for human intervention

### Bundled Resources

Skills can bundle dependencies alongside their instructions:
- `references/` — documentation, examples, API specs
- `scripts/` — helper scripts, utilities
- `assets/` — templates, images, resources

Bundled resources keep skills self-contained and portable.

### Communication Skills

Skills aren't limited to technical tasks. Communication skills help agents:
- Draft professional emails with appropriate tone
- Structure status updates and standups
- Deliver feedback constructively
- Navigate conflicts and negotiations

## Connections

- **Concept**: [[skill-design]] — core skill creation principles and methodology
- **Concept**: [[skill-evaluation]] — detailed evaluation frameworks and testing methods
- **Source**: [[skills-and-agents-rules]] — operational rules and skill folder structure
- **Source**: [[best-practices-for-skill-creators]] — grounding skills in real expertise
- **Source**: [[optimizing-skill-descriptions]] — description optimization and triggering
- **Source**: [[claude-code-skill-patterns]] — skill authorship patterns and workflows
- **Concept**: [[agents-vs-skills]] — decision framework for skills vs agents
- **Concept**: [[context-management]] — progressive disclosure and token optimization
- **Concept**: [[soft-skills]] — applying skills to communication and career growth

## Notes

Key insight from the PDF: "Default to rigid. Start with strict rules and loosen only when needed." Most real-world tasks benefit from structured, repeatable procedures. Flexible skills are the exception, not the rule.

Another key insight: The "Chef's Skill" analogy captures the essence — an LLM without skills is like a chef without recipes. Every dish is improvised, quality varies, and nothing is repeatable. Skills are the recipes that make execution consistent.

The 4-step eval method (should-trigger, constraint, ask, bad-behavior) is a practical framework that goes beyond simple trigger testing. Most existing eval approaches only test should-trigger; the constraint and bad-behavior tests catch edge cases that pure trigger testing misses.

---
Source: [The Complete Guide to Building Skills for Claude](../raw/The-Complete-Guide-to-Building-Skill-for-Claude.pdf)
