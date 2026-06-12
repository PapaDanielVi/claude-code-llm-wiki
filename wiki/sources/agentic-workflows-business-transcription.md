---
title: "Agentic Workflows for Business — Video Course Transcription"
type: source
created: 2026-05-07
updated: 2026-06-12
source-type: video-transcription
url: "raw/Agentic-Workflows-Transcription.md"
tags:
  - agentic-workflows
  - ai-business
  - claude-code
  - prompting
  - automation
---

## Summary

A comprehensive video course transcription covering the full landscape of agentic workflows for business — from fundamentals through practical implementation, advanced patterns, deployment, and troubleshooting. The instructor built two AI-based service agencies to $160K/month in combined revenue.

## Key Points

### Fundamentals
- The agentic loop: **planning → tool use → memory → reflection**, with orchestration sitting outside/around the loop, shuttling information between steps
- The human stays in the loop to "steer the ship" — fully removing the human currently degrades workflow quality
- Common problems with agentic workflows and their fixes

### The DO Framework (Directive Orchestration and Execution)
- Workspace organized like a **filing cabinet** with two required folders: `directives/` and `executions/`
- One directive = one markdown file covering **one workflow or capability** (e.g., `scrape_leads.md`) — never one giant "run business" file
- The operator gives high-level instructions; the AI handles the *how*
- Optional folders (e.g., `resources/` for routinely fed files) can be added as needed

### Tooling Landscape
- Claude skills, MCP, and other frameworks: what each does, when to use which, how they fit together

### Validation & Optimization
- Test and validate workflows before trusting them; iterate via reflection output (e.g., the model itself suggests human-in-the-loop review steps, web enrichment, robust JSON handling)
- Best system prompts for agentic workflows
- Making workflows self-annealing (self-healing) — see [[self-annealing]]

### Deployment
- Moving from IDE to cloud
- Webhook and schedule triggers
- Running multiple agents simultaneously
- **Sub-agent pattern**: a *reviewer* sub-agent plus a *documentation* sub-agent significantly increase workflow effectiveness

### Maintenance
- Troubleshooting agentic workflows when things break

## Connections

- [[agentic-workflows]] — Core concept page this source feeds into

## Notes

- This is a raw transcription of a video course — no chapter markers, single long text block
- Source material is dense and covers a full beginner-to-advanced curriculum
- May want to extract key sub-sections into dedicated concept pages (e.g., [[claude-skills]], [[model-context-protocol]])
