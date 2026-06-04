---
title: "Claude.md Best Practices (Karpati Skills)"
type: source
source-type: video-transcript
raw-path: raw/Claude.md Best Practices.md
created: 2026-05-07
updated: 2026-05-07
tags: [claude-code, agent-best-practices, prompting, karpati-skills, youtube]
aliases: [karpati-skills, andre-karpati-claude-code]
---

## Summary

A YouTube tutorial by RoboNuggets/Jay analyzing Andre Karpati's viral insights on working with AI agents. Forest created a single `CLAUDE.md` file (the "Karpati Skills" repo) implementing these principles, which gained 43k stars in one week. The video demonstrates live comparisons between vanilla Claude Code and Claude Code with Karpati Skills installed, showing dramatic differences in task completion.

## Key Points

### Andre Karpati's 4 Principles

**1. Think Before Coding (Ask Questions)**
- Without rule: Claude assumes what you want
- With rule: Claude asks first, confirms intent
- Problem it solves: wrong assumptions, unmanaged confusion, unsurfaced inconsistencies
- Example: light mode toggle — vanilla failed silently; Karpati asked clarifying questions and delivered working implementation

**2. Put Simplicity First**
- Without rule: AI overbuilds with bloated, brittle code (1000+ lines)
- With rule: Claude writes minimum viable code (100 lines or less)
- Problem it solves: production-trained models default to complex patterns even for simple tasks
- Example: search bar filter — vanilla added complex logic tracking visible tabs; Karpati added only 20 targeted lines

**3. Make Surgical Changes**
- Without rule: Claude reformats, reorganizes, improves things you didn't ask for
- With rule: Claude changes only what you want
- Problem it solves: wasted tokens, unnecessary reformatting, broken formatting
- Example: font change — vanilla reformatted declarations, Google fonts URLs; Karpati only swapped font family values

**4. Goal-Driven Execution**
- Without rule: imperative commands ("do X, then Y")
- With rule: declarative success criteria ("achieve X")
- Problem it solves: getting stuck in loops, not recognizing completion
- Insight: LLMs are exceptionally good at looping until they meet specific goals

### Karpati Skills CLAUDE.md Structure

The repo provides a drop-in CLAUDE.md that:
- Prompts Claude to ask clarifying questions before building
- Enforces simplicity as the default
- Restricts changes to what's explicitly requested
- Encourages declarative success criteria over imperative instructions

### Live Demo Results

| Task | Vanilla Claude Code | With Karpati Skills |
|------|---------------------|---------------------|
| Add light mode toggle | Failed (claimed success) | Worked immediately |
| Add filter search bar | Failed (claimed success) | 20 lines, minimal complexity |
| Change font family | Burned tokens fixing errors | One-shot, surgical |

### Key Insight

The Karpati Skills repo is essentially a single CLAUDE.md file that addresses the most common failure modes of AI agents. The principles apply regardless of whether you use the repo directly.

## Notes

The Karpati Skills repo ([GitHub](https://github.com/forest-protocols/karpati-skills)) is essentially a single CLAUDE.md file that addresses the most common failure modes of AI agents. The principles apply regardless of whether you use the repo directly — they're about changing *how you think about prompting*, not just what tools you use.

## Connections

- Related: [[agentic-workflows]]
- Related: [[skill-design]]
- Related: [[context-management]]
- Related: [[soft-skills]]
- See also: [Andre Karpati Skills GitHub](https://github.com/forest-protocols/karpati-skills)