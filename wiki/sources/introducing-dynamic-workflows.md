---
title: "Introducing Dynamic Workflows"
type: source
created: 2026-06-04
updated: 2026-06-04
tags:
  - claude-code
  - agentic-workflows
  - dynamic-workflows
---

## Summary

Dynamic workflows in Claude Code enable end-to-end handling of the most challenging tasks by executing across 10s to 100s of parallel subagents, with work verified before reaching the user. Available in research preview for Max, Team, and Enterprise plans, as well as on Claude API, Amazon Bedrock, Vertex AI, and Microsoft Foundry.

## Key Points

- **Parallel execution**: Workflows run tens to hundreds of parallel subagents in a single session
- **Verification before output**: Independent verification on every finding so reports surface real issues
- **Convergence loop**: Agents address problems from independent angles, others try to refute findings, iteration continues until answers converge
- **Progress persistence**: Jobs that are interrupted pick up where they left off instead of starting over
- **Use cases include**: codebase-wide bug hunts, profiler-guided optimization audits, security audits, large migrations and modernization, critical work needing adversarial verification

## Case Study: Bun Rewrite

- Jarred Sumner used dynamic workflows to port Bun from Zig to Rust
- Achieved 99.8% test suite passing across ~750,000 lines of Rust
- Eleven days from first commit to merge
- Workflow mapped Rust lifetimes for every struct field, wrote behavior-identical ports, drove build/test fixes
- Overnight workflow addressed unnecessary data copies with PRs for final review

## How It Works

1. Claude plans dynamically based on prompt, breaks into subtasks
2. Fans work out across parallel subagents
3. Results are checked before folding in
4. Independent attempts from different angles with adversarial agents refuting results
5. Coordination happens outside conversation, plan stays on track regardless of task scale

## Getting Started

- Available on Max/Team plans and API by default
- Enterprise plans: off by default, admin can enable in settings
- Can trigger via explicit request ("Create a workflow") or by enabling `ultracode` setting
- Turning on auto mode recommended for best experience

## Source

- Original: https://claude.com/blog/introducing-dynamic-workflows-in-claude-code
- Published: May 28, 2026

## Connections

- [[agentic-workflows]] — Core workflow concept extended by dynamic workflows
- [[claude-skills]] — Skills invoked within dynamic workflow agents
- [[claude-code-dynamic-workflow-patterns]] — Six core design patterns for applying dynamic workflows

## Notes

- Consumes substantially more tokens than typical session — start with scoped tasks
- Organization admins can disable workflows through managed settings
- Coordination layer handles tracking and reduces human intervention for large tasks