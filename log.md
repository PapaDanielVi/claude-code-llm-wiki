# Log

## [2026-06-12] ingest | Top 5 Open-Source Agentic AI Frameworks in 2026

### Source
- Created: `wiki/sources/top-5-agentic-frameworks-2026.md` — AIMultiple benchmark of LangChain, LangGraph, AutoGen, CrewAI (2,000 runs across 5 tasks)
- Raw file had been sitting in `raw/` since 2026-05-15 with no ingest (caught by lint)

### Key insights
- With the same LLM, framework loop architecture dominates agent behavior (pivot capacity, cost, failure modes)
- Goal-centric (LangGraph/AutoGen, ~90% pivot on tool failure) vs plan-centric (CrewAI, 0% pivot) is the key behavioral split
- CrewAI's retry/verification machinery can corrupt parameters the LLM originally got right
- LangChain treats tool exceptions as fatal by default — resilience requires explicit configuration

### Pages created/updated
- Created: [[agentic-frameworks]] (concept) — first non-Claude-Code agentic content in the wiki
- Updated: [[agentic-workflows]], [[automation]], [[self-annealing]], [[model-context-protocol]] — backlinks and framework context

### Tags
- #agentic-ai, #technology, #frameworks

## [2026-06-12] lint | Wiki health check (2026-06-12)

### Fixed
- 3 true orphans: backlinks added for `anatomy-of-the-.claude-folder` (4 concepts), `prompting`, `prompt-engineering-hacks`
- Phantom link `[[Nivetha Suruliraj]]` in `prompt-compression.md` frontmatter → plain text
- Path-prefixed links in `prompt-engineering-hacks.md` → bare format
- Placeholder Connections prose in `google-ai-prompt-engineering-course.md` → real wiki links
- Index drift: added `best-practices-for-skill-creators` and `optimizing-skill-descriptions`; added Entities/Insights sections; re-filed `ai-2027-project`

### Status
- No contradictions, no duplicates, no stale content
- Near-orphan leaf nodes accepted intentionally (documented in patterns.md)
- Gap caught: un-ingested raw file → ingested same session (see entry above)

## [2026-06-05] lint | Wiki health check (2026-06-05)

### Fixed
- Path-prefixed wiki links in `concepts/prompting.md` → standardized to bare `[[page-name]]` format
- Added missing `## Notes` section to `sources/how-claude-code-works-large-codebases.md`

### Status
- **Orphans**: 7 pages with ≤1 inbound link (documented in patterns.md)
- **Structural issues**: Resolved (path prefixes, missing Notes)
- **All wiki links resolve**: No gaps detected
- **All pages updated**: Within last 30 days

## [2026-05-15] lint | Wiki health check

### Fixed
- Orphan concept page added to index: `concepts/agentic-data-analysis.md`
- 2 source pages missing `## Summary` → added: `agentic-workflows-business-transcription.md`, `anatomy-of-the-.claude-folder.md`
- 6 concept/source pages missing `## Key Points` → added: `agents-vs-skills`, `prompting`, `skill-design`, `skill-evaluation`, `soft-skills`, `anatomy-of-the-.claude-folder`
- 5 concept/source pages missing `## Notes` → added: `agentic-data-analysis`, `claude-agents-vs-skills`, `claude-code-agentic-workflows`, `claude-code-data-analysis`, `karpati-claude-best-practices`
- 1 source page missing `## Connections` → added: `anatomy-of-the-.claude-folder.md`
- Normalized `#tag` → `tag` format in tags arrays across 5 concept pages: `claude-skills`, `self-annealing`, `model-context-protocol`, `automation`, `agentic-workflows`
- Fixed `source_type` → `source-type` in `ai-scaffold-hierarchy.md`
- Removed redundant frontmatter `summary:` from 4 concept pages: `claude-skills`, `self-annealing`, `model-context-protocol`, `automation`
- Fixed non-standard wiki link syntax `[text](page)` → `[[page]]` in `ai-scaffold-hierarchy.md`
- Added `## Notes` to `agentic-data-analysis.md`
- Added `## Key Points` to `agentic-workflows.md` concept (extracted from content)

## [2026-05-10] lint | Wiki health check

### Fixed
- 2 orphan pages linked into graph:
  - `mechanistic-interpretability.md` — linked from `anthropic-interpretability.md`
  - `karpati-claude-best-practices.md` — linked from `claude-code-agentic-workflows.md`
- 3 source files missing `type:` and `updated:` fields → added:
  - `sources/prompt-compression.md`
  - `sources/self-annealing-ai-agents-explained.md`
  - `sources/llm-dcp.md`

## [2026-05-10] ingest | You're Wasting 40% Of Your AI Time On Something Fixable
- Source: sources/ai-scaffold-hierarchy.md
- Simon Willison video on agentic scaffold framework
- Core concepts: prompts vs skills vs plugins vs MCPs hierarchy, hooks and scripts for deterministic checks
- Concepts updated: agentic-workflows (added scaffold hierarchy connection)
- Tags: #ai-futures, #technology, #agentic-workflows, #scaffolding

## [2026-05-07] ingest | Claude.md Best Practices transcript
- Source: sources/karpati-claude-best-practices.md
- Concepts updated: agentic-workflows (added Karpati principles section)
- Tags: #claude-code, #agent-best-practices, #prompting, #karpati-skills
- Key insight: "The difference between working and broken: asking questions before building vs assuming intent"
- Links to: [[agentic-workflows]], [[skill-design]], [[context-management]]

## [2026-05-07] lint | Wiki health check

### Fixed
- 6 files with path-prefixed wiki links → stripped `concepts/`, `entities/`, `sources/` prefixes:
  - `concepts/ida.md`, `concepts/ai-alignment.md`, `concepts/agi-timeline.md`, `concepts/neuralese.md`
  - `entities/ai-2027-project.md`
  - `sources/ai-2027.md`
- 2 sources with mismatched frontmatter format → standardized to YAML array for both tags and aliases:
  - `sources/optimizing-skill-descriptions.md`
  - `sources/best-practices-for-skill-creators.md`

### Status
All lint checks clean: no broken links, no style mismatches, no orphans, no gaps.
- Source: sources/claude-skills-build-first-assistant.md
- Concept updated: skill-design (added capability vs workflow skills taxonomy)
- Tags: #skill-design, #agentic-ai, #claude-desktop, #co-work
- Key insight: "As Claude gets smarter, capability skills retire. Workflow skills compound."
- Links to: [[skill-design]], [[context-management]], [[skill-evaluation]]

## [2026-05-07] ingest | Claude Code: Data Analysis Without the Spreadsheet Headaches
- Source: sources/claude-code-data-analysis.md
- Concept created: agentic-data-analysis
- Concept updated: agentic-workflows (added data analysis application section)
- Tags: #agentic-ai, #claude-code, #data-analysis, #business-intelligence
- Key insight: "Everything built is reusable. Next month, drop updated spreadsheets into resources/, run the same workflow."
- Links to: [[agentic-data-analysis]], [[agentic-workflows]], [[context-management]], [[skill-design]]

## [2026-05-07] ingest | Claude Code: Build Your First AI Agent
- Source: sources/claude-code-agentic-workflows.md
- Concept created: agentic-workflows
- Tags: #agentic-ai, #claude-code, #workflow-design, #prompt-engineering
- Key insight: "A well-written workflow with basic tools outperforms a sloppy prompt with every plugin."
- Links to: [[agentic-workflows]], [[context-management]], [[skill-design]], [[agents-vs-skills]]

## [2026-05-07] ingest | The Complete Guide to Building Skills for Claude
- Source: sources/complete-guide-building-skills.md
- Concept created: skill-evaluation
- Concept updated: skill-design (rigid/flexible framework, skill types, routing, archetypes, session lifecycle, error posture)
- Tags: #skill-design, #agentic-ai, #prompting
- Key insight: "Default to rigid. Start with strict rules and loosen only when needed."
- Links to: [[skill-design]], [[skill-evaluation]], [[context-management]], [[agents-vs-skills]]

## [2026-05-06] ingest | Claude Agents vs Skills
- Source: sources/claude-agents-vs-skills.md
- Concepts created: agents-vs-skills, soft-skills
- Tags: #skill-design, #agentic-ai, #soft-skills, #career-growth
- Key insight: "3 good agents + 10 disciplined skills" beats most enterprise setups
- Links to: [[skill-design]], [[skills-and-agents-rules]]

## [2026-05-06] lint | Wiki health check (2nd pass)

### Fixed
- 2 orphan pages linked: `ai-2027-project` from `ai-2027.md`, `claude-code-skill-patterns` from `skill-design.md`
- Duplicate `[[skill-design]]` link removed from `context-management.md`
- Created missing meta files: `meta/health-check.md`, `meta/patterns.md`

### Status
All lint checks clean: no contradictions, no stale claims, no orphans, no gaps, no neglected pages.

## [2026-05-06] lint | Wiki health check

### Fixed
- All 17 broken wiki links resolved — replaced non-existent targets with existing pages
- Thinned `mechanistic-interpretability.md` concept to 5 lines + "See also" reference (was 80% duplicate of `anthropic-interpretability.md`)
- Standardized 3 files to YAML array tag format: `skills-and-agents-rules`, `skill-authoring-best-practices`, `claude-code-skill-patterns`
- Fixed duplicate `ai-futures` tag in `mechanistic-interpretability.md`
- Added missing tags to `skill-authoring-best-practices`, `optimizing-skill-descriptions`, `best-practices-for-skill-creators`
- Renamed raw files: "Best practices for skill creators.md" → `best-practices-for-skill-creators.md`, "Optimizing skill descriptions.md" → `optimizing-skill-descriptions.md`

### Remaining growth areas
- Concepts still heavily summarize their sources — add original LLM synthesis over time
- `[[pair-programming]]` in Notes section converted to plain text — consider creating a concept

## [2026-05-06] ingest | Optimizing skill descriptions
- Source: sources/optimizing-skill-descriptions.md
- Links to: [[best-practices-for-skill-creators]], [[skill-design]]
- Tags: #skill-design, #agentic-ai

## [2026-05-06] ingest | Best practices for skill creators
- Source: sources/best-practices-for-skill-creators.md
- Concept: concepts/skill-design.md
- Tags: #skill-design, #agentic-ai

## [2026-05-06] ingest | AI 2027
- Source: sources/ai-2027.md
- Entities created: ai-2027-project
- Concepts created: agi-timeline, ai-alignment, neuralese, ida
- Tags: #research, #ai-futures, #existential-risk

## [2026-05-06] lint | Wiki health check
- Fixed: 4 missing bidirectional links (agi-timeline ↔ neuralese, ai-alignment ↔ ida/neuralese)
- Fixed: trimmed entity to avoid duplicating source content
- Fixed: renamed raw/AI 2027.md → raw/ai-2027.md (removed space)

## [2026-05-06] ingest | Anthropic AI Interpretability Research
- Source: sources/anthropic-interpretability.md
- Concept created: mechanistic-interpretability
- Links to: [[ai-alignment]], [[neuralese]], [[anthropic-interpretability]]
- Tags: #ai-futures, #existential-risk, #research
- Key finding: "golden ticket" hypothesis — sparse, interpretable features exist in neural networks

## [2026-05-06] ingest | Claude Code Skill Patterns (Screenshot)
- Source: sources/claude-code-skill-patterns.md (from screenshot)
- Topics: skill triggering, three-stage workflow (init/author/test), CLAUDE.md role
- Links to: [[skill-design]], [[skill-authoring-best-practices]], [[skills-and-agents-rules]]
- Tags: #skill-design, #ai-futures

## [2026-05-06] ingest | Skill Authoring Best Practices
- Source: sources/skill-authoring-best-practices.md
- Concepts created: (none)
- Tags: #ai

## [2026-05-06] ingest | Skills and Agents Rules
- Source: sources/skills-and-agents-rules.md
- Concept created: context-management
- Links to: [[skill-design]]
- Tags: #skill-design, #agentic-ai, #agentic-workflows, #context-management
- Notes: 19 operational rules, progressive disclosure architecture, SKILL.md format, folder structure, open source skill repos
## [2026-05-07] ingest | Agentic Workflows Video Course Transcription
- Read raw/Agentic-Workflows-Transcription.md (large file, parsed via CLI)
- Created wiki/sources/agentic-workflows-business-transcription.md — source summary
- Created wiki/concepts/agentic-workflows.md — core concept (loops, tools, state, self-correction)
- Created wiki/concepts/model-context-protocol.md — MCP protocol concept
- Created wiki/concepts/claude-skills.md — skills concept
- Created wiki/concepts/automation.md — automation concept
- Created wiki/concepts/self-annealing.md — self-healing pattern
- Linked all concept pages to source and to each other

## [2026-05-08] ingest | Prompt Compression
- Source: sources/prompt-compression.md
- Concept updated: context-management (cross-referenced compression techniques)
- Tags: #ai-futures, #context-management, #llm-optimization
- Key insight: "5-step pipeline: Extract → Summarize → Optimize → Filter → Output enables 60-90% token reduction"
- Links to: [[context-management]], [[agentic-workflows]], [[model-context-protocol]]

## [2026-05-08] ingest | LLM-DCP Paper
- Source: sources/llm-dcp.md
- Concept: prompt-compression (added research-grade MDP formulation)
- Tags: #ai-futures, #research, #reinforcement-learning, #prompt-compression
- Key insight: "MDP-based compression outperforms entropy methods by modeling sequential token dependency"
- Links to: [[prompt-compression]], [[context-management]], [[agentic-workflows]]

## [2026-05-09] ingest | Self-Annealing AI Agents Explained
- Source: sources/self-annealing-ai-agents-explained.md
- Concept updated: self-annealing (added 3-step loop, protocol prompt, implementation approaches)
- Tags: #agentic-ai, #self-improvement, #prompt-engineering
- Key insight: "Every failure should make the agent stronger. Treat errors as inputs for self-improvement, not endpoints."
- Links to: [[self-annealing]], [[agentic-workflows]], [[automation]]
## [2026-05-13] ingest | Prompt Engineering Hacks in 53 Mins (GPT, Claude)
- Source: sources/prompt-engineering-hacks.md
- Key insights from Nick's video on prompt engineering best practices for getting reliable, high-quality outputs from LLMs like GPT and Claude
- Concepts updated: prompting (added key prompt structure, one-shot learning, unambiguous language)
- Tags: #prompt-engineering, #llm-optimization, #ai-best-practices

## [2026-05-13] ingest | Google AI Prompt Engineering Course
- Source: sources/google-ai-prompt-engineering-course.md
- Summarized Google's AI Prompt Engineering Course covering fundamental to advanced prompting techniques
- Key insights: Five-step framework (Task, Context, References, Evaluate, Iterate), persona/format enhancement, iteration methods (RAHEN saves tragic idiots), multimodal prompting, advanced techniques (prompt chaining, Chain of Thought, Tree of Thought), and AI agent framework
- Concepts updated: prompting (added core framework, iteration methods, advanced techniques)
- Tags: #ai-futures, #technology

## [2026-06-04] ingest | How Claude Code works in large codebases

### Source
- Created: `wiki/sources/how-claude-code-works-large-codebases.md` — Agentic search vs RAG, five extension points, large codebase patterns

### Key insights
- Agentic search (live file traversal) vs RAG (embedded indexes) — no embedding pipeline lag for active codebases
- Five extension points in order: CLAUDE.md → hooks → skills → plugins → MCP servers
- Large codebase patterns: lean layered CLAUDE.md, subdirectory scoping, LSP for symbol navigation

### Concepts updated
- [[agentic-workflows]] — added large codebase patterns, subdirectory scoping notes
- [[context-management]] — added large codebase strategies section (subdirectory scoping, CLAUDE.md layering, LSP filtering)
- [[skill-design]] — added plugin distribution pattern, linked to large codebases source
- [[claude-skills]] — added large codebases source link, progressive disclosure on-demand loading

### Tags
- #claude-code, #scale, #agentic-workflows, #context-management

## [2026-06-04] ingest | Introducing Dynamic Workflows

### Source
- Created: `wiki/sources/introducing-dynamic-workflows.md` — Dynamic workflows: parallel subagents, verification loops, convergence patterns

### Key insights
- Parallel execution across 10s to 100s of subagents with verification before output
- Convergence loop: agents work from independent angles, adversarial agents refute findings
- Case study: Bun ported from Zig to Rust (~750k lines, 99.8% test passing) in 11 days
- Progress persistence enables interruption recovery

### Concepts updated
- [[agentic-workflows]] — added dynamic workflows subsection on parallel execution, convergence loops, usecases
- [[claude-skills]] — added dynamic workflows source link

### Tags
- #claude-code, #agentic-workflows, #dynamic-workflows, #scale

## [2026-06-04] ingest | Every Claude Code Dynamic Workflow (6 Core Patterns)

### Source
- Created: `wiki/sources/claude-code-dynamic-workflow-patterns.md` — Six design patterns for dynamic workflows

### Key insights
- **Core problems solved**: agent laziness, self-preference bias, goal drift in long sessions
- Six patterns: classify-and-act, fan-out-and-synthesize, adversarial verification, generate-and-filter, tournament (pairwise), loop-until-done
- Patterns can be stacked for complex workflows (e.g., fan out → adversarial verify → loop until clean)
- When to NOT use: basic UI changes don't need agent swarms; workflows consume substantial tokens

### Concepts updated
- [[agentic-workflows]] — added dynamic workflow patterns subsection with all six patterns and stacking strategies

### Tags
- #claude-code, #agentic-workflows, #dynamic-workflows, #patterns
