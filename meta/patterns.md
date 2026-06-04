# Patterns

Tracked patterns and anomalies across the wiki.

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
