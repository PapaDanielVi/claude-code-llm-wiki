# Patterns

Tracked patterns and anomalies across the wiki.

## Lint Check — 2026-06-12

### ✅ Contradictions
- None detected.

### ✅ Stale Content
- No superseded claims identified.

### ⚠️ Orphans (0 inbound links) — fixed this pass
- `anatomy-of-the-.claude-folder` — linked OUT to 4 concepts but none linked back (broken bidirectionality). Fixed: backlinks added to `claude-skills`, `context-management`, `skill-design`, `model-context-protocol`.
- `prompting` (concept) — never linked from its own source pages. Fixed: links added from `prompt-engineering-hacks` and `google-ai-prompt-engineering-course`.
- `prompt-engineering-hacks` (source) — no inbound links. Fixed: linked from `prompting` concept and `google-ai-prompt-engineering-course`.

### ⚠️ Gaps — fixed this pass
- `wiki/sources/prompt-compression.md` frontmatter contained a phantom link `[[Nivetha Suruliraj]]` (author, no page intended). Converted to plain text.
- `raw/Top 5 Open-Source Agentic AI Frameworks in 2026.md` was present in `raw/` since 2026-05-15 but never ingested (no log entry, no source page). Ingested this pass → `sources/top-5-agentic-frameworks-2026` + new concept `agentic-frameworks`.

### ⚠️ Index Drift — fixed this pass
- `best-practices-for-skill-creators` and `optimizing-skill-descriptions` source pages were missing from `wiki/index.md`.
- `ai-2027-project` (entity) was filed under Concepts; index had no Entities/Insights sections. Restructured.

### ⚠️ Structural Issues — fixed this pass
- `prompt-engineering-hacks.md` had path-prefixed links (`[[concepts/automation]]`, `[[concepts/claude-skills]]`) — same defect class previously fixed in `prompting.md` on 2026-06-05. Normalized.
- `google-ai-prompt-engineering-course.md` Connections section contained placeholder prose ("Links to prompting concepts in wiki/concepts/") instead of actual wiki links. Replaced with real links.

### ✅ Neglected Pages
- None — all pages updated within the last 30 days or untouched with no related new sources.

### ✅ Duplicates
- None. `skill-authoring-best-practices` and `best-practices-for-skill-creators` cover adjacent ground but trace to distinct raw documents; kept separate.

### ✅ Unsourced Claims
- Concept pages trace to source pages. New `agentic-frameworks` page labels its one extrapolation explicitly as inference.

### Near-orphans (1 inbound link) — accepted as leaf nodes
- `ai-2027-project`, `llm-dcp`, `karpati-claude-best-practices`, `claude-skills-build-first-assistant`, `self-annealing-ai-agents-explained`, `mechanistic-interpretability`/`anthropic-interpretability` pair. These are intentionally narrow; no forced connections added (hallucination guard).

## Lint Check — 2026-06-05

### ✅ Contradictions
- None detected. Claims across pages are consistent.

### ✅ Stale Content
- All pages updated within last 30 days. No superseded claims identified.

### ⚠️ Orphans (Pages with ≤1 Inbound Link)
These pages have minimal connections to the wiki graph:
- `^ai-2027-project` (entity) — linked only from `ai-2027.md` source
- `^claude-skills-build-first-assistant` — linked only from `skill-design.md`
- `^google-ai-prompt-engineering-course` — linked only from `prompting.md`
- `^karpati-claude-best-practices` — linked only from `skill-design.md`
- `^llm-dcp` — linked only from `prompt-compression.md`
- `^mechanistic-interpretability` — linked only from `anthropic-interpretability.md`
- `^self-annealing-ai-agents-explained` — linked only from `self-annealing.md`

**Recommendation**: Review for organic connections to add, or accept as leaf nodes if intentionally isolated.

### ⚠️ Missing Page Sections
- `wiki/sources/how-claude-code-works-large-codebases.md` — missing `## Notes` section (all other sources have one)
- `wiki/concepts/prompting.md` — has path-prefixed links in line 85: `[[concepts/automation]]`, `[[concepts/claude-skills]]`, `[[concepts/agentic-workflows]]`, `[[concepts/agents-vs-skills]]`

### ✅ Gaps (Missing Pages)
- All wiki links resolve to existing pages. No gaps detected.

### ✅ Neglected Pages
- No pages untouched >30 days while related sources have arrived.

### ✅ Duplicates
- No duplicate coverage identified.

### ✅ Unsourced Claims
- All concept pages include `## Source` or `Source:` sections linking to source pages.

## Content Patterns

### Observation
All current content clusters around two domains: AI futures (AI 2027 scenario) and agentic AI/skill design. No diversification into other domain tags yet.

### Tag Distribution
- `ai-futures`: 4 pages
- `skill-design`: 4 pages
- `existential-risk`: 3 pages
- `agentic-ai`: 4 pages
- `research`: 3 pages
- `technical`: 3 pages
- `prompting`: 2 pages
- `context-management`: 2 pages

### Ingest Cadence
Single bulk ingest on 2026-05-06. No incremental ingests yet.

## Anomalies
- None detected yet.
