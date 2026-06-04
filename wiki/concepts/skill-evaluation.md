---
title: "Skill Evaluation"
type: concept
created: 2026-05-07
updated: 2026-05-07
tags:
  - skill-design
  - agentic-ai
  - evaluation
aliases:
  - "skill-testing"
  - "skill-eval"
---

## Summary

Skill evaluation is the systematic testing of whether a skill triggers correctly, behaves within constraints, and refuses inappropriate tasks. Goes beyond simple trigger testing to include constraint validation, clarification behavior, and scope enforcement.

## Key Points

- **4-Step Eval**: Should-trigger → Constraint → Ask → Bad Behavior
- **Should-Trigger**: ~10 varied queries covering explicit, implicit, edge cases
- **Constraint**: Boundary conditions, conflicting instructions, format requirements
- **Ask**: Incomplete or contradictory requests; flexible skills need stronger ask tests
- **Bad Behavior**: Irrelevant, adversarial, out-of-scope queries; critical for rigid skills
- **Evaluation guardrails**: Human-required, agent-required, constrained-language tests
- **Testing best practices**: 3+ runs, 60/40 train/validation split, select by validation pass rate

## Connections

- **Concept**: [[skill-design]] — creating skills that pass evaluation
- **Source**: [[complete-guide-building-skills]] — 4-step eval method and guardrails
- **Source**: [[optimizing-skill-descriptions]] — trigger testing and description optimization
- **Source**: [[best-practices-for-skill-creators]] — execute-then-revise refinement cycles

## Notes

Most existing eval approaches only test should-trigger. The constraint and bad-behavior tests catch edge cases that pure trigger testing misses — especially important for rigid skills where violating constraints has consequences.
