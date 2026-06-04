---
title: "You're Wasting 40% Of Your AI Time On Something Fixable"
type: source
created: 2026-05-10
updated: 2026-05-10
tags: [ai-futures, technology]
source-type: video/transcript
author: "Simon Willison"
---

# You're Wasting 40% Of Your AI Time On Something Fixable

## Summary

A comprehensive explainer on the "agentic scaffold" - the middleware layer surrounding LLMs that determines whether AI actually gets real work done. The core thesis: most people blame the model when work fails, but the real issue is the harness/scaffolding around it. Covers the hierarchy from prompts → skills → plugins → MCPs/connectors, and the role of hooks and scripts.

## Key Points

### The Scaffold Mental Model
- LLMs are like Transformers or Darth Vader's mech suit - they need external scaffolding to accomplish meaningful work
- The "suit" includes: prompts, skills, plugins, MCPs, connectors, hooks, and scripts
- A generic LLM with heavy prompting can give useful high-level advice; a properly scaffolded agent can review work against your standards and actually get done

### Prompt vs Skill vs Plugin Hierarchy

| Component | Purpose | Example |
|-----------|---------|---------|
| **Prompt** | One-off, temporary, highly specific tasks | Complex email to one client with custom backstory |
| **Skill** | Reusable process you want consistently across your team | PR review process, marketing doc structure, outbound email format |
| **Plugin** | Entire workflow package with skills + integrations + scripts + assets | Weekly business report pulling from spreadsheets, Slack, docs, dashboards |
| **MCP/Connector** | Live data access from external systems | Salesforce, Figma, GitHub - plugging into where work lives |

### Skills Are Just Markdown
- A skill is simply a detailed markdown document describing how to perform a work process
- Skills should be reusable and tool-agnostic (work with any LLM)
- The 80/20 rule applies: 20% of your skills provide 80% of value - focus on high-frequency, high-sensitivity workflows
- Power law distribution: find the skills that are repeated constantly with high stakes

### Plugins: The Real Workflow Package
- A plugin packages up: skills, app integrations, MCP servers, hooks, assets, commands, metadata
- Plugins make workflows installable and shareable across teams
- You don't need to be an engineer to build one in 2026
- **Warning**: Resist making everything a plugin - not every workflow needs this overhead
- Workflow boundary identification is a valuable skill: knowing where to draw edges around a workflow

### MCPs and Connectors
- MCP (Model Context Protocol) servers are how agents access live data from external systems
- Think of them as "universal plugs" - you plug in and get data back
- Many SaaS tools are now building their own MCPs
- A plugin *can* contain an MCP, but a plugin is larger - it's the whole workflow, not just data access

### Hooks and Scripts
- For deterministic, repeatable checks that should NOT be left to model judgment
- Examples: code formatting, schema validation, running tests, JSON validity checks
- A good agent workflow separates: deterministic scripts (don't ask the model to "imagine running the test") from model judgment tasks
- Hooks/scripts fit inside plugins as part of the workflow package

### The "Human Plugin" Pattern
- Most people already do plugin work manually: copy from app → paste to chat → ask model to reason → go get more data → check result → repeat
- If you're the human plugin, consider building an actual plugin to automate that workflow

### The Plugin Marketplaces Are Wrong Analogy
- App store analogy understates what's happening
- Better framing: think of plugins as **workflow packaging** - repeatable structures with clear boundaries
- Ask: "What part of my work has enough repeatable structure that the agent should inherit it?"
- Not "what can I install?" but "what repeatable work needs packaging?"

## Core Decision Framework

- **Prompt**: Do it once (one-off)
- **Skill**: Do it repeatedly (reusable process)
- **Plugin**: Workflow needs to travel / other people need to install it / needs tools, assets, or connectors
- **MCP/Connector**: Need access to another system (live data)
- **Script/Hook**: Workflow must be verified deterministically

## Connections

- [[model-context-protocol]] — MCP is the protocol for tool connections
- [[claude-skills]] — skills as reusable instruction sets
- [[agentic-workflows]] — the broader context of goal-driven AI processes
- [[automation]] — packaging repeatable work into plugins

## Notes

- Author notes that 2026 is the first year where non-engineers can realistically build plugins
- Domain experts (non-technical) have an advantage: they know what good work looks like, which sources matter, when output is wrong, what steps are forgotten
- The judgment about workflow boundaries (what constitutes a "good unit of work" for a plugin) is a high-value skill
- Leadership/CEO understanding of this hierarchy is important for organizational AI adoption

## Source

https://simonwillison.net/2026/May/6/ai-scaffold/
