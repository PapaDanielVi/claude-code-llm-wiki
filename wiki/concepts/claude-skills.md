---
title: Claude Skills
type: concept
created: 2026-05-07
updated: 2026-06-12
aliases:
  - skill
  - skills
tags:
  - claude-skills
  - agentic-workflows
  - prompting
---

## Summary

Claude Skills are specialized capability modules that extend what Claude can do out of the box. Each skill contains a prompt (or set of prompts), tool configurations, and workflow patterns tailored for a specific type of task. They can be invoked dynamically during a conversation or workflow, giving Claude capabilities without needing to embed complex instructions in every prompt.

Skills are a key building block in agentic workflows — they let you compose specialized sub-capabilities rather than building every skill from scratch.

## Key Points

- **Composable**: Multiple skills can be used together in a single workflow
- **Domain-specific**: Each skill is optimized for a particular task type (e.g., brainstorming, code review, design, debugging)
- **On-demand invocation**: Skills are loaded when needed, not baked into every prompt
- **Tool access**: Skills can be configured with specific tool permissions and tool sets
- **Workflow patterns**: Skills encode best-practice patterns for their domain (how to brainstorm, how to debug, etc.)

## Relationship to Agentic Workflows

In agentic workflows, skills serve as the "vocabulary" the agent uses to tackle different subtasks:

- A parent agent can invoke skills for sub-tasks without spawning a full sub-agent
- Skills provide structured approaches (checklists, workflows) that the agent follows
- The agent decides which skill to invoke based on context — skill selection is part of the reasoning loop

## Relationship to MCP

| Layer | What it provides |
|---|---|
| **MCP** | Tool integration protocol — how Claude talks to external systems |
| **Claude Skills** | Application-layer prompts and patterns — what Claude does with those tools |

MCP provides the transport, Skills provide the direction.

## Source

- [[agentic-workflows-business-transcription]] — Video course covering Claude Skills in the context of the DO framework
- [[agentic-workflows]] — How skills fit into agentic workflow architecture
- [[how-claude-code-works-large-codebases]] — Skills for progressive disclosure on-demand loading
- [[introducing-dynamic-workflows]] — Skills invoked within dynamic workflow agents
- [[anatomy-of-the-.claude-folder]] — Where skills live on disk (`.claude/skills/` vs `~/.claude/skills/`)
- [[claude-skills-technical-report]] — Runtime internals: three-level progressive disclosure, ~100 tokens/skill metadata, sandboxing, Skills API

## Connections

- [[agentic-workflows]] — Skills are building blocks of agentic workflows
- [[model-context-protocol]] — The protocol layer that skills leverage for tool access
- [[harness-engineering-coding-agent-users]] — skills are the main inferential feedforward guide in the user harness (coding conventions, how-tos), and inferential feedback sensors when they encode review instructions

## Notes

- The skills system is what enables "skill composition" — assembling complex workflows from well-tested modules
- Different from system prompts: skills are modular and reusable, not embedded in every conversation

### Dynamic Workflows Integration

Within dynamic workflows, skills serve as the "vocabulary" that parallel subagents use to tackle different subtasks. Each subagent can invoke the same skill set, enabling consistent approaches across all parallel execution paths while maintaining verification and convergence properties.
