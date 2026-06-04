---
title: "Optimizing skill descriptions"
type: "source"
created: 2026-05-06
updated: 2026-05-06
tags:
  - "skill-design"
  - "agentic-ai"
  - "prompting"
aliases:
  - "optimizing-skill-descriptions"
  - "skill-triggering"
---

## Summary

Guide on testing and improving a skill's `description` field so it triggers reliably on relevant user prompts. Covers triggering mechanics, writing effective descriptions, designing eval queries (should/should-not trigger), running tests with multiple runs, avoiding overfitting via train/validation splits, and the optimization loop.

## Key Points

### How Triggering Works
- Agents load only `name` + `description` at startup to decide when to load a skill
- Description must convey when the skill is useful — it carries the entire triggering burden
- Skills typically trigger on tasks requiring specialized knowledge (unfamiliar APIs, domain workflows, uncommon formats)

### Writing Effective Descriptions
- **Imperative phrasing**: "Use this skill when..." (not "This skill does...")
- **User intent focus**: describe what user is trying to achieve, not internal mechanics
- **Pushy**: explicitly list contexts, even when user doesn't name the domain directly
- **Concise**: few sentences to short paragraph; 1024 character hard limit

### Designing Eval Queries (~20 queries)
- **Should-trigger (8-10)**: vary phrasing, explicitness, detail, complexity
  - Include non-obvious connections where skill would help but isn't named
- **Should-not-trigger (8-10)**: focus on **near-misses** (share keywords but need different thing)
  - Weak: obviously irrelevant ("weather today?") — tests nothing
  - Strong: shares "spreadsheet" but needs Excel editing (not CSV analysis)

### Testing Approach
- Run each query multiple times (3 runs minimum) due to nondeterminism
- Compute trigger rate = fraction of runs where skill invoked
- Pass threshold: ~0.5 trigger rate for should-trigger; below threshold for should-not

### Avoiding Overfitting
- **Train set (~60%)**: used to guide improvements
- **Validation set (~40%)**: held out to check generalization
- Both sets need proportional mix of should/should-not

### Optimization Loop
1. Evaluate on train + validation sets
2. Identify failures in train set only
3. Revise description — focus on generalizing, not keyword-stuffing
4. Repeat until train set passes or improvement stalls
5. Select best by validation pass rate (not last iteration)

### Tips
- Script the eval — 20 queries × 3 runs = 60 invocations
- Stop runs early once outcome is clear
- Fresh queries (5-10) after selection for honest generalization check

## Connections

- Related to: [[best-practices-for-skill-creators]], [[skill-design]], [[skills-and-agents-rules]]

## Notes

Key insight: The most valuable test queries are **near-misses** — cases where the skill would help but the connection isn't obvious from the query alone. Generic negative examples (obviously irrelevant queries) test nothing.

Another key insight: Best description may not be the last iteration — earlier iterations may have higher validation pass rates.

Source: [agentskills.io](https://agentskills.io/skill-creation/optimizing-descriptions)