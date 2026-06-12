# claude-code-llm-wiki: Agentic Workflows & Claude Skills Knowledge Base

A living knowledge base for **Claude Code skills**, **context engineering**, **prompting**, and **agentic workflows**. Built for developers who want to understand and build effective AI systems.

## What This Is

This repository contains distilled knowledge about building agentic AI systems with Claude Code. It's organized as a personal wiki following the **LLM-Wiki pattern** — a structured approach to compounding knowledge through iterative ingestion, querying, and linting.

**Current state** (2026-06-12): 45 wiki pages distilled from 23 raw source documents — 18 concepts, 26 source summaries, 1 entity.

The knowledge is organized into:

- **Concepts** — Core ideas: agentic workflows, skill design, prompting, MCP, self-annealing systems, agentic frameworks
- **Entities** — Named things: projects, researchers, frameworks
- **Sources** — Summaries of original materials: articles, videos, course notes, research papers
- **Insights** — Synthesis across multiple sources (added as patterns emerge)

## Quick Start: Querying This Knowledge

To query the knowledge in this wiki, you can:

### 1. Browse the Index

Start with [`wiki/index.md`](wiki/index.md) — it contains one-line summaries of every page, grouped by type.

```bash
curl -s https://raw.githubusercontent.com/PapaDanielVi/claude-code-llm-wiki/refs/heads/master/wiki/index.md | head -50
```

### 2. Read Relevant Pages

Use the Obsidian-style [[wiki links]] to navigate. For example:

```bash
# Read the agentic workflows concept
curl -s https://raw.githubusercontent.com/PapaDanielVi/claude-code-llm-wiki/refs/heads/master/wiki/concepts/agentic-workflows.md

# Read the skill design guide
curl -s https://raw.githubusercontent.com/PapaDanielVi/claude-code-llm-wiki/refs/heads/master/wiki/concepts/skill-design.md
```

### 3. Search for Topics

```bash
# Find all pages mentioning "MCP"
grep -r "MCP\|model-context-protocol" wiki/ --include="*.md"

# Find all workflow patterns
grep -r "pattern\|Pattern" wiki/ --include="*.md"
```

### 4. Use with Claude Code

If you have Claude Code installed, you can use this as context:

```bash
# Clone and use as context
git clone https://github.com/PapaDanielVi/claude-code-llm-wiki.git
cd claude-code-llm-wiki
claude --add-dir=.
```

Then reference pages in your prompts:
- *"Using the patterns in [[agentic-workflows]], design a workflow for code review"*
- *"Apply the rigid/flexible principles from [[skill-design]] to this task"*

## Knowledge Structure

```
claude-code-llm-wiki/
├── wiki/
│   ├── concepts/     # Core concepts: workflows, skills, prompting, MCP
│   ├── entities/     # People, projects, frameworks
│   ├── insights/     # Synthesis across sources
│   ├── sources/      # Summaries of original materials
│   └── index.md      # Master catalog of all pages
├── raw/              # Source materials (articles, notes, exports) — immutable
├── meta/             # Patterns detected, open questions, health checks
├── docs/             # Design rationale for the wiki itself
├── log.md            # Append-only activity log of all operations
└── CLAUDE.md         # Operating manual: schema + behavioral contract for the LLM
```

## Key Topics

### Agentic Workflows
- **Loop-based operation**: Plan → Act → Evaluate → Adapt
- **Six core patterns**: classify-and-act, fan-out-and-synthesize, adversarial verification, generate-and-filter, tournament, loop-until-done
- **Dynamic workflows**: Parallel subagents, convergence loops, large-scale migrations
- See: [agentic-workflows.md](wiki/concepts/agentic-workflows.md)

### Skill Design
- **Rigid vs. Flexible**: Default to rigid (strict rules); loosen only when needed
- **Capability vs. Workflow Skills**: Capability = teach Claude how; Workflow = capture YOUR process
- **Progressive disclosure**: Core instructions under 500 lines, details loaded on demand
- **Description optimization**: Imperative phrasing, user-intent focus, tested with eval queries
- See: [skill-design.md](wiki/concepts/skill-design.md)

### Context Engineering
- **Token-efficient architecture**: Progressive disclosure, session lifecycle management
- **Large codebase patterns**: Subdirectory scoping, CLAUDE.md layering
- **Compression techniques**: Extract → Summarize → Optimize → Filter → Output
- See: [context-management.md](wiki/concepts/context-management.md)

### Claude Skills
- **Native vs. Superpowers**: Built-in capabilities vs. community extensions
- **Skill archetypes**: Dialectic, Maximalist, Triggerless
- **Error posture**: Fail-fast, graceful degradation, retry, human escalation
- **Runtime internals**: Three-level progressive disclosure (~100 tokens/skill metadata), sandboxing, trigger reliability
- See: [claude-skills.md](wiki/concepts/claude-skills.md)

### Agentic Frameworks
- **Architecture determines behavior**: With the same LLM, the framework's loop mechanism (state machine, conversation loop, managerial process, sequential executor) dominates pivot capacity, cost, and failure modes
- **Goal-centric vs. plan-centric**: The key split in how agents recover from tool failures
- **LangChain · LangGraph · AutoGen · CrewAI · OpenAI Swarm** compared via a 2,000-run benchmark
- See: [agentic-frameworks.md](wiki/concepts/agentic-frameworks.md)

### Prompting & Compression
- **Effective prompting framework**: Brevity, clarity, structure, empirical testing (Task → Context → References → Evaluate → Iterate)
- **Prompt compression**: Extract → Summarize → Optimize → Filter pipelines; LLM-DCP achieves up to 12.9x compression
- See: [prompting.md](wiki/concepts/prompting.md)

## Quality Control

The compounding nature of this wiki is also its main risk: a subtle error baked in during ingest reinforces itself across every later update. Defenses in place:

- **Cite, don't assert** — every non-trivial claim traces to a source page or inline `[[source-slug]]` link
- **Flag, don't overwrite** — contradictions get a `## Conflicts` section, never a silent edit
- **Provenance audits** — periodic raw-vs-wiki comparison of every source page against its original document (latest: 2026-06-12, findings in [`meta/patterns.md`](meta/patterns.md))
- **Git diffs as the safety net** — small, frequent commits keep human review tractable

Pages with unresolved provenance issues are marked ⚠️ in the index until resolved.

## How to Contribute

This wiki grows through three operations:

1. **Ingest** — Add new knowledge sources to `raw/`, summarize in `wiki/sources/`
2. **Query** — Ask questions about existing knowledge, file syntheses as insights
3. **Lint** — Check for contradictions, orphans, gaps; fix issues

The full schema and behavioral contract live in [`CLAUDE.md`](CLAUDE.md) — read it before making changes. The human owns `raw/` and the questions; the LLM owns `wiki/` and the maintenance.

## License

MIT License — See [LICENSE](LICENSE)

## Attribution

Built with the LLM-Wiki pattern from [@karpathy's llm-wiki.md](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).

---

*This is a living knowledge base. Knowledge compounds through use.*
