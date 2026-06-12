---
title: "Context Management"
type: "concept"
created: 2026-05-06
updated: 2026-06-12
tags:
  - "context-management"
  - "agentic-ai"
  - "token-optimization"
aliases:
  - "context-window-management"
  - "llm-context-management"
---

## Summary

Context management is the practice of controlling what information an AI agent has available at any given time — optimizing for relevance, token efficiency, and preventing fact drift over long interactions.

## Key Points

### Progressive Disclosure
Agents load information in stages — only name/description at discovery, full instructions at activation, bundled resources at execution. This keeps many skills available with minimal context footprint.

### Divider Pattern
Split CLAUDE.md/GEMINI.md/CODEX.md into multiple files (context, rules, etc.) and reference them in the root file. Agents load target references only when needed. Dramatically reduces token usage.

### Context Compaction
- Avoid long chat sessions — compact and move to a new session
- Put context and memory in persistent files to prevent re-loading
- Use RTK (Rust Token Killer) to reduce token overhead on CLI operations
- Use Caveman to reduce token usage across sessions
- **Prompt compression pipeline**: Extract → Summarize → Optimize → Filter → Output (see [[prompt-compression]]) for upstream compression before context even reaches the LLM

### Memory Strategy
- Memory is transportable and every project must have memory
- Write learned rules to `.claude/rules/` to learn from mistakes
- Write back context given by developer to prevent incomplete context
- Always instruct AI to update memory and rules to prevent fact slippage

### Model Stacking
Don't use expensive models for easy tasks. Match model capability to task complexity. Smaller models serve as the basic evaluation for skills — if a skill works on a small model, it's properly designed.

## Connections

- Related: [[skill-design]] — progressive disclosure is a core skill design pattern
- Related: [[agentic-data-analysis]] — CLAUDE.md as business context for data analysis
- Related: [[prompt-compression]] — upstream input reduction using extractive/summarization/token-optimization pipeline
- Source: [[skills-and-agents-rules]] — operational rules for context management
- Source: [[anatomy-of-the-.claude-folder]] — CLAUDE.md, `.claude/rules/`, and settings as the on-disk context layer
- Source: [[claude-skills-technical-report]] — the three-level skill loading model as a concrete progressive-disclosure implementation

## Notes

Core insight from rules: "Always put instruction to update the memory and context and rule so the AI should update these files and prevent fact slips." Context persistence across sessions is the key mechanism.

Token efficiency and context quality are not opposites — smart context architecture (dividers, progressive disclosure, memory files) improves both simultaneously.

In large codebases, CLAUDE.md files should be "pointers and critical gotchas only" at root level; subdirectory files provide local conventions. The quality of Claude's navigation is bounded by how well the codebase is set up.