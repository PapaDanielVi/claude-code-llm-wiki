---
title: "How Claude Code works in large codebases: Best practices and where to start"
type: source
created: 2026-06-04
updated: 2026-06-04
tags:
  - clippings
  - claude-code
  - scale
aliases:
---

# How Claude Code works in large codebases

Source: https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start

## Summary

Claude Code navigates large codebases (monorepos, legacy systems, distributed architectures) through agentic search—traversing the file system, reading files, and grep-ing for specifics—rather than RAG-based embedding systems. This approach works from the live codebase without requiring index maintenance, but requires proper setup with CLAUDE.md files, hooks, skills, plugins, and MCP servers for optimal performance.

## Key Points

### Navigation Approach
- Agentic search vs RAG: traverses file system live, no embedding pipeline lag
- Works on multi-million-line codebases in C, C++, C#, Java, PHP (beyond typical AI coding targets)
- Quality depends on starting context—CLAUDE.md layering is critical

### Five Extension Points (in order)
1. **CLAUDE.md files** — Context loaded every session; root for big picture, subdirectory for local conventions
2. **Hooks** — Scripts for continuous improvement and deterministic checks; not just restrictions
3. **Skills** — On-demand packaged expertise; progressive disclosure pattern
4. **Plugins** — Bundled skills/hooks/MCP configs for org-wide distribution
5. **MCP servers** — Connections to internal tools, data sources, APIs

### Additional Capabilities
- LSP integrations for symbol-level navigation (crucial for large multi-language codebases)
- Subagents for splitting exploration from editing with isolated context windows

### Large Codebase Patterns
- Keep CLAUDE.md files lean and layered (root = pointers, subdirectories = local conventions)
- Initialize in subdirectories, not repo root (Claude walks up tree automatically)
- Scope test/lint commands per subdirectory to avoid timeouts
- Use `.ignore` files to exclude generated files, build artifacts, third-party code
- Build codebase maps when directory structure is unconventional
- Run LSP servers for symbol-based search over string-based grep

### Organizational Layer
- Need dedicated infrastructure investment before broad access
- Minimum viable: DRI (Directly Responsible Individual) for configuration, permissions, plugins
- Cross-functional working groups (engineering, security, governance) work best

## Connections

- [[agentic-workflows]] — progressive disclosure, workflow design
- [[context-management]] — token efficiency, CLAUDE.md hierarchy
- [[skill-design]] — skills vs agents, plugin distribution
- [[claude-skills]] — on-demand expertise, progressive disclosure
- [[model-context-protocol]] — MCP servers for internal tools
## Notes

This source emphasizes that agentic search (live file traversal) works best when the codebase is properly scaffolded with lean, layered CLAUDE.md files. The five extension points (CLAUDE.md → hooks → skills → plugins → MCP servers) form a hierarchy where each layer builds on the previous one. For large codebases, subdirectory scoping is critical — initializing in subdirectories prevents overwhelming context with root-level files.
