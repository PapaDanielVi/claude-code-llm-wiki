---
title: "Claude Code Dynamic Workflow Patterns"
type: source
created: 2026-06-04
updated: 2026-06-04
tags:
  - claude-code
  - agentic-workflows
  - dynamic-workflows
---

## Summary

Six core design patterns for using Claude Code dynamic workflows effectively, derived from an analysis of the official Anthropic masterclass on dynamic workflows. These patterns address common problems like agent laziness, self-preference bias, and goal drift in long-running AI sessions.

## Key Points

### Core Problems Dynamic Workflows Solve

- **Agent laziness**: In long sessions (600K+ tokens), agents often fail to complete all assigned tasks
- **Self-preference**: Single-agent evaluation of its own output is inherently biased
- **Goal drift**: Long conversations lose the original detailed goal through auto-compaction and summarization

### Six Core Patterns

#### 1. Classify and Act
- Acts like a receptionist routing incoming tasks to appropriate handlers
- Useful for inbox triaging: classify email as bug, refund request, upgrade, spam, or duplicate
- Strategy: reader agent → classifier → quarantine → trusted agent acts

#### 2. Fan Out and Synthesize
- Break task into micro parts, assign to mutually exclusive agents, then merge results
- Ideal for deep research or due diligence where documents shouldn't cross-contaminate
- Strategy: individual context windows per item → barrier synthesize step → cited output

#### 3. Adversarial Verification
- Multiple skeptics/devil's advocates verify output against a rubric/checklist
- Essential for fact-checking AI-generated content
- Strategy: extract claims → spin up separate agents to verify each → return failures with reasons

#### 4. Generate and Filter
- Overgenerate ideas quickly, then filter/synthesize down to best options
- Better to go from 1000 ideas to 3 than 10 to 3
- Strategy: generator agents → judge agents → rubric-based scoring → synthesized picks

#### 5. Tournament (Pairwise Comparison)
- Compares ideas head-to-head through fresh agents until final bracket emerges
- Avoids bias from evaluating all options in a single context window
- Strategy: divide decision space → fresh context each round → deterministic loop holds bracket

#### 6. Loop Until Done
- Keep iterating until specific outcome achieved (no fixed pass count)
- Useful for hunting flaky tests or reproducing intermittent bugs
- Strategy: form theories → adversarially test each in isolated worktree → repeat

### Stacking Patterns
Patterns can be combined for complex workflows (e.g., fan out to find issues → adversarial verify → loop until clean pass).

## Source

- Video transcription: "Every Claude Code Dynamic Workflow (& When to Use Each)"
- Date: 2026-06-04

## Connections

- [[introducing-dynamic-workflows]] — Core dynamic workflows feature
- [[agentic-workflows]] — Parent concept for all workflow patterns
- [[claude-skills]] — Skills used within workflow agents

## Notes

- When to NOT use workflows: basic UI changes (button color, animation) don't need agent swarms
- Workflows consume substantial tokens — use for complex, multi-layer tasks only
- Sharing workflows: JavaScript file saved via `/workflows` command during execution