---
title: "Model Context Protocol (MCP)"
type: concept
created: 2026-05-07
updated: 2026-05-07
aliases:
  - "MCP"
  - "Anthropic MCP"
tags:
  - model-context-protocol
  - agentic-workflows
  - tool-integration
---

## Summary

The Model Context Protocol (MCP) is Anthropic's open protocol for connecting AI assistants to external tools and data sources. It provides a standardized interface that allows agents to interact with files, databases, APIs, web browsers, and other systems without custom integration code for each tool.

MCP is a key enabler of agentic workflows — it forms the "nervous system" that allows an AI agent to perceive and act upon its environment.

## Key Points

- **Standardized interface**: One protocol, many tool integrations — avoids bespoke API integration per tool
- **Tool discovery**: Agents can discover available tools dynamically rather than having them hardcoded
- **Security layer**: MCP servers can enforce permissions and audit tool usage
- **Bidirectional**: Supports both tool invocation (agent → external) and context retrieval (external → agent)

## How It Fits in Agentic Workflows

```
Agent (Claude)
    ↓
MCP Server (tool host)
    ↓
External Systems (files, APIs, DBs, browsers, etc.)
```

MCP sits between the agent and external systems, translating agent requests into tool calls and returning results back to the agent.

## Relationship to Claude Skills

While MCP handles tool integration at the protocol level, Claude Skills provide pre-packaged capabilities (prompts, workflows, tool configurations) that can leverage MCP. Skills are the "application layer," MCP is the "transport layer."

## Source

- [[agentic-workflows-business-transcription]] — Video course covering MCP in context of agentic workflows
- [[agentic-workflows]] — Broader concept that MCP enables

## Connections

- [[agentic-workflows]] — What MCP enables
- [[claude-skills]] — Built on top of MCP

## Notes

- MCP replaces the need for custom tool-wrapping code for each integration
- Key differentiator from simpler agentic systems: standardized, discoverable tool interfaces rather than hardcoded integrations
