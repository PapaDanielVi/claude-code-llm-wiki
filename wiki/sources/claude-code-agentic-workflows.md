---
title: "Claude Code: Build Your First AI Agent"
type: source
source-type: video-transcript
raw-path: raw/Claude Code Build Your First AI Agent.md
created: 2026-05-07
updated: 2026-05-07
tags: [agentic-ai, claude-code, workflow-design, prompt-engineering, vscode]
aliases: [claude-code-agentic-workflows, build-first-agent, teachers-tech-agent]
---

## Summary

A YouTube tutorial by Teachers Tech (Jamie) demonstrating how to build agentic workflows in Claude Code using VS Code. Covers the three levels of AI interaction (chat → building → agentic), the critical role of `CLAUDE.md` for project context, plan mode for dry-run design, and a live demo building a research report workflow from scratch. The workflow reads plain English markdown files, asks clarifying questions, researches via built-in web search, and produces structured reports — all without writing code.

## Key Points

### Three Levels of AI Interaction

1. **Chat** — ask a question, get an answer. One-and-done (ChatGPT-style).
2. **Building** — tell AI what to create, guide step-by-step, AI writes code. You're the director. (previous video)
3. **Agentic** — describe the goal, AI figures out steps, makes decisions, adapts, asks questions. Goal-driven autonomy.

The agentic level has three characteristics:
- Follows a process (series of steps, not single question)
- Makes decisions (pivots when approach isn't working)
- Asks before it assumes (clarifying questions before starting)

### CLAUDE.md — The Non-Negotiable Setup

A markdown file in the project root that Claude Code reads on every startup. Acts as an onboarding document:

- **Project Context** — what the workspace is for
- **About Me** — who you are, audience, preferences
- **Rules** — guardrails (ask questions before complex tasks, show plans, concise output, cite sources)
- **Project Structure** — where workflows, output, and resources live

Impact: without CLAUDE.md → generic wall of text. With CLAUDE.md → organized bullets, clear sections, sources cited, files saved to correct locations.

### The Three Layers

1. **Workflows** — plain English markdown files describing a process step-by-step (like a recipe)
2. **Agent** — Claude Code itself; reads workflows, thinks through steps, makes decisions
3. **Tools** — built-in: read/write files, terminal commands, web search. Extensible via MCP (Gmail, Notion, databases)

Key insight: a well-written workflow with basic tools outperforms a sloppy prompt with every plugin. The workflow is where the magic lives.

### Plan Mode

Toggle with `Shift+Tab` (twice in VS Code). In plan mode, Claude Code thinks and plans but doesn't change files. Like a dry run.

- Design workflow before building
- Shape approach with follow-up instructions (it folds new requirements in, doesn't restart)
- Extra 30 seconds of planning saves significant wasted effort

### Workflow Structure (Research Report Example)

The generated workflow file contains:
1. **Objective** — clear statement of what the workflow does
2. **Clarifying questions** — asks about scope, audience, depth, format before starting
3. **Plan confirmation** — confirms research plan with user before executing
4. **Research phase** — structured web search with quality rules (avoid opinion posts, prefer recent sources)
5. **Writing phase** — tone rules, formatting guidelines
6. **Output** — saves to designated folder
7. **Error handling** — flags topics too broad, asks user to narrow

### Iteration Pattern

Instead of restarting, give targeted feedback on existing output:
- "Trim the executive summary to 3 bullet points" → finds and edits that section
- "Add a comparison table of top 5 tools mentioned" → scans its own research, creates table
- Agent remembers context and builds on what's already there

### Common Mistakes

1. Skipping CLAUDE.md — 2 min setup saves hours
2. Being too vague — specificity produces quality
3. Not using plan mode — plan first, build second
4. Not telling it to ask questions — assumptions lead to mediocre output
5. Building everything at once — start with one workflow, refine, then expand

### Pro Tips

- Keep workflow files in a `workflows/` folder
- Read the agent's to-do list and reasoning as it works
- Give targeted feedback ("fix X") instead of restarting
- Save best CLAUDE.md and workflow files as templates
- Use conversation rollback to undo file changes and rephrase
- Effort levels: `effort low/medium/high` controls thinking depth

## Notes

The video demonstrates the full agentic workflow lifecycle in a single session — no code writing required. Key takeaway: the workflow file is the core asset, not the prompts themselves. A well-structured workflow with basic tools outperforms verbose prompts with every plugin enabled.

## Connections

- Related: [[agentic-workflows]]
- Related: [[agentic-data-analysis]] — Part 3 applies this pattern to business data analysis
- Related: [[context-management]]
- Related: [[skill-design]]
- Related: [[agents-vs-skills]]
- See also: [[karpati-claude-best-practices]] — Andre Karpati's CLAUDE.md principles
- Source: [[claude-agents-vs-skills]]
