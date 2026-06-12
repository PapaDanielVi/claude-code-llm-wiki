---
title: "Agentic Workflows"
type: concept
created: 2026-05-07
updated: 2026-06-12
aliases:
  - "agentic AI"
  - "AI agents"
  - "autonomous AI"
tags:
  - agentic-workflows
  - ai-futures
  - automation
---

## Summary

Agentic workflows are AI systems that operate autonomously through feedback loops — perceiving their environment, reasoning about actions, executing tasks, and self-correcting based on results. Unlike simple prompt-response interactions, agentic workflows maintain persistent state, use tools, and can handle multi-step tasks with minimal human intervention.

The fundamental mechanism is the **loop** (sometimes called the OODA loop or observe→orient→decide→act): the agent senses input, forms a plan, takes action, evaluates the result, and adapts. This creates self-sustaining automation that can handle complex, multi-step business processes.

## Key Points

- **Loop-based operation**: Plan → Act → Evaluate → Adapt (repeats until goal achieved or timeout)
- **Tool use**: Agents use tools (APIs, file system, web search, code execution) to interact with environment
- **State persistence**: Unlike stateless prompts, agents maintain context across steps
- **Self-correction**: Errors trigger adaptation — the workflow "heals itself" when things break
- **Business applicability**: Can automate service agencies, consulting workflows, content pipelines, and more

## Core Components

### The DO Framework (Directive Orchestration)

A structured approach to orchestrating agentic workflows:

- **Directive**: Clear instruction or goal for the agent
- **Orchestration**: Managing the flow between steps, loops, and sub-agents

### Claude Skills

Pre-packaged capabilities that can be loaded into Claude for specialized tasks. Skills extend Claude's base capabilities without writing custom code for every use case.

### Model Context Protocol (MCP)

Anthropic's protocol for connecting Claude to external tools and data sources. Enables agents to interact with files, databases, APIs, and other systems in a standardized way.

### Sub-agents

Spawning child agents from a parent agent for parallel or nested task execution. Enables handling complex workflows by decomposing them into parallel sub-tasks.

## Common Patterns

- **Self-annealing**: Workflows that detect and recover from errors automatically
- **Webhooks**: Triggering workflows via HTTP callbacks from external systems
- **Scheduled triggers**: Running workflows on cron-like schedules
- **Parallelization**: Running multiple agents simultaneously for throughput

## Source

- [[agentic-workflows-business-transcription]] — Comprehensive video course covering fundamentals to advanced patterns
- [[how-claude-code-works-large-codebases]] — Large codebase patterns, CLAUDE.md layering, progressive disclosure architecture
- [[introducing-dynamic-workflows]] — Dynamic workflows: parallel subagents, convergence loops for large-scale tasks
- [[claude-code-dynamic-workflow-patterns]] — Six core patterns: classify-and-act, fan-out-and-synthesize, adversarial verification, generate-and-filter, tournament, loop-until-done

## Connections

- [[claude-skills]] — Extends agentic capabilities
- [[model-context-protocol]] — Protocol for tool integration
- [[automation]] — Related automation concepts
- [[ai-scaffold-hierarchy]] — Scaffold hierarchy: prompts → skills → plugins → MCPs
- [[agentic-frameworks]] — Open-source orchestration frameworks (LangChain, LangGraph, AutoGen, CrewAI) that implement the agentic loop outside Claude Code

## Notes

- Agentic workflows are positioned as "one of the largest wealth transfers in human history" — a bold claim that reflects the disruptive potential of AI automation
- The business focus is practical: working systems generating revenue now, not theoretical future applications
- **Large codebase optimization**: Initialize in subdirectories, not at root — Claude walks up the tree and loads every CLAUDE.md file along the way. Root context is never lost, but subdirectory scoping prevents overwhelming context.
- **Plugin distribution**: Successful rollouts have dedicated infrastructure investment before broad access. One engineer built plugins for the whole business unit before rollout.

### Dynamic Workflows

- **Parallel execution**: 10s to 100s of subagents running concurrently on complex tasks
- **Convergence loops**: Agents work from independent angles; adversarial agents refute findings; iteration continues until answers converge
- **Usecases**: Codebase-wide bug hunts, migrations, critical work needing verification (e.g., Bun port achieved 750k lines with 99.8% test passing in 11 days)
- **Activation**: Use `ultracode` setting or explicitly request "create a workflow"

#### Six Core Design Patterns

1. **Classify and Act**: Receptionist-style routing (reader agent → classifier → quarantine → trusted agent acts)
2. **Fan Out and Synthesize**: Break task into micro parts with separate context windows, then merge (ideal for due diligence/research)
3. **Adversarial Verification**: Multiple skeptics verify output against rubric (essential for fact-checking)
4. **Generate and Filter**: Overgenerate 1000 ideas, filter to best 3 (better than 10→3)
5. **Tournament**: Pairwise comparison through fresh agents until final bracket emerges (avoids single-window bias)
6. **Loop Until Done**: Iterate until specific outcome achieved (no fixed pass count, good for flaky tests)

Patterns can be stacked (e.g., fan out → adversarial verify → loop until clean).
