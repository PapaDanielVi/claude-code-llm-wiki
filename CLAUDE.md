---
title: "LLM Wiki — Schema & Operating Manual"
type: schema
created: 2026-05-06
updated: 2026-06-04
---

# claude-code-llm-wiki Operating Manual

This file is the schema **and** the behavioral contract. Read it before doing anything else in this repo.

**The pattern:** You own `raw/` and the questions. The LLM owns `wiki/` and the maintenance. Every ingest, every query, every lint pass compounds the knowledge base. The wiki is the build artifact — treat it like code.

**The model:** Obsidian on one side, Claude on the other. The LLM edits; you browse in real time — graph view, backlinks, live page updates. The LLM is the programmer; the wiki is the codebase; you are the architect.

---

## Directory Structure

```
claude-code-llm-wiki/
├── raw/                    # Your inputs — immutable, LLM reads only
│   ├── articles/           # Clipped web articles
│   ├── books/              # Book notes, PDFs
│   ├── journals/           # Journal entries
│   └── app-data/           # Health exports, CSVs
│
├── wiki/                   # LLM-owned knowledge (you read, LLM writes)
│   ├── entities/           # People, places, projects, habits, practices
│   ├── concepts/           # Topics, themes, frameworks, models
│   ├── insights/           # Syntheses, analyses, comparisons
│   ├── sources/            # One summary per raw document
│   └── index.md            # Master catalog — updated on every operation
│
├── meta/                   # LLM self-tracking
│   ├── health-check.md     # Proactive nudges (scheduled + pattern-based)
│   └── patterns.md         # Detected patterns, anomalies, open questions
│
├── log.md                  # Append-only activity log
└── CLAUDE.md               # This file — schema + behavioral contract
```

> **Flat is better than deep.** Don't create subdirectories inside `wiki/` categories. Deep hierarchies slow the agent and fragment the graph. When in doubt, add a tag instead of a folder.

---

## File Conventions

| Convention         | Rule                                                                                      |
| ------------------ | ----------------------------------------------------------------------------------------- |
| Filenames          | `lowercase-with-hyphens.md`                                                               |
| Frontmatter fields | `title`, `type`, `created`, `updated`, `tags`, `aliases`                                  |
| Page sections      | Summary · Key Points · Connections · Notes                                                |
| Log entries        | `## [YYYY-MM-DD] operation \| Title`                                                      |
| Links              | `[[wiki-links]]` — always bidirectional                                                   |
| Source attribution | Every claim on a wiki page must trace to a source page or a `[[source-slug]]` inline link |

**Frontmatter template:**
```yaml
---
title: "Page Title"
type: concept          # entity | concept | insight | source
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [#self, #health]
aliases: [alternate name]
sources: [source-slug-1, source-slug-2]
---
```

---

## Page Types

| Type      | Purpose                      | Examples                                          |
| --------- | ---------------------------- | ------------------------------------------------- |
| `entity`  | Named things in your world   | person, place, project, habit, practice           |
| `concept` | Ideas and frameworks         | topic, theme, mental model                        |
| `insight` | LLM syntheses across sources | analysis, comparison, conclusion, emerging thesis |
| `source`  | One-per-raw-document summary | book chapter digest, article summary              |

**Source pages are the foundation.** Every claim in an entity or concept page should be traceable back to a source page. When in doubt, make a source page first, then propagate upward.

---

## Domain Tags

| Tag                 | Scope                                      |
| ------------------- | ------------------------------------------ |
| `#self`             | Self-improvement, habits, goals            |
| `#health`           | Physical health, fitness, sleep, nutrition |
| `#psych`            | Psychology, emotions, relationships        |
| `#research`         | Research projects and papers               |
| `#technology`       | Tech topics, tools                         |
| `#ai-futures`       | AI forecasting, alignment                  |
| `#existential-risk` | X-risk research                            |

Add new tags freely — document them here when you do. Tags are vocabulary; keep them consistent across pages.

---

## Operations

There are three operations. Everything is one of these three.

### 1. Ingest

*Trigger: new file in `raw/`*

A single source typically touches 10–15 wiki pages. Do not rush.

```
1. Read source fully before writing anything
2. Discuss key takeaways if helpful — ingest one source at a time
3. Write summary → wiki/sources/<slug>.md
4. For each entity or concept touched: update existing page OR create new one
5. Add bidirectional links between all affected pages
6. Check for contradictions with existing pages (see Conflicts below)
7. Append to log.md
8. Update wiki/index.md
```

**On contradictions:** If new source conflicts with an existing wiki page, do not silently overwrite. Add a `## Conflicts` section to both the source page and the affected wiki page. Note the conflicting claim, which source supports each side, and the date. Flag in `meta/patterns.md`. Resolve only when instructed.

**Ingest one source at a time.** Bulk ingest flattens nuance and produces generic pages. Resist it.

### 2. Query

*Trigger: you ask a question*

```
1. Read wiki/index.md to identify relevant pages
2. Read those pages in full
3. Synthesize answer — ground every claim in a source page
4. Offer to file synthesis as wiki/insights/<slug>.md
```

Good answers get filed. Exploration compounds. If an answer reveals a gap (concept mentioned but no page), note it in `meta/patterns.md` as a gap to fill on next ingest.

**Hallucination guard:** Do not invent connections not present in the wiki. If a synthesis requires reasoning beyond what the sources support, label it explicitly as inference: *"This is an extrapolation not yet confirmed by sources."*

### 3. Lint

*Trigger: periodic or when requested*

Check for and report (do not auto-fix contradictions):

- [ ] **Contradictions** — claims that conflict across pages
- [ ] **Stale content** — claims likely superseded by newer sources
- [ ] **Orphans** — pages with no inbound links
- [ ] **Gaps** — concepts referenced but no page exists
- [ ] **Neglect** — pages untouched >30 days while related sources have arrived
- [ ] **Duplicates** — two pages covering substantially the same ground
- [ ] **Unsourced claims** — assertions with no traceable source link

Report findings in `meta/patterns.md` as a dated entry. Propose merges, deletions, and new pages — implement only what's approved.

---

## Hallucination & Quality Control

The compounding nature of this wiki is also its main risk: a subtle error baked in during ingest reinforces itself across every subsequent update that touches the affected page. Prevention is better than correction.

**Rules:**

1. **Cite, don't assert.** Every non-trivial claim on an entity or concept page links to a source page or carries an inline `[[source-slug]]` reference.
2. **Flag, don't overwrite.** Contradictions get a `## Conflicts` section, not a silent edit.
3. **Label inferences.** Synthesis in `wiki/insights/` may go beyond sources — always label where reasoning exceeds evidence.
4. **Git diffs are the safety net.** Human review of `git diff` after each ingest session catches errors that lint misses. Commit frequently so diffs stay small.
5. **Distinguish absence from negation.** "Source does not mention X" ≠ "X is false." Never infer falsity from silence.

---

## LLM Boundaries

|                | LLM does                   | LLM does not                   |
| -------------- | -------------------------- | ------------------------------ |
| `raw/`         | Reads                      | Writes, edits, or deletes      |
| `wiki/`        | Full ownership             | —                              |
| `meta/`        | Full ownership             | —                              |
| `log.md`       | Appends only               | Edits past entries             |
| Contradictions | Flags, proposes resolution | Auto-resolves without approval |
| Inferences     | Writes, clearly labeled    | Presents as established fact   |

---

## Meta Files

**`log.md`** — Append-only record of every operation (ingest, query, lint).
```bash
grep "^## \[" log.md | tail -10   # recent activity
```

**`wiki/index.md`** — One-line summary per wiki page, grouped by type. The LLM's entry point on every query. Updated after every ingest and every new insight.

**`meta/health-check.md`** — Proactive observations from `raw/app-data/`. Updated when patterns emerge, not on a fixed schedule. Nudges only — not diagnoses.

**`meta/patterns.md`** — Running log of detected patterns, anomalies, open contradictions, and gaps. Dated entries. This is where lint findings live.

---

## Git

After each ingest session (not after every single file), ask the developer to commit:

```bash
git add .
git commit -m "ingest: <brief description of source(s)>"
git push
```

Small, frequent commits keep `git diff` readable — that's your human review layer. Use descriptive messages. The log tracks granular ops; git tracks checkpoints.

---

*Full design rationale: `docs/2026-05-06-llm-wiki-design.md`*
*Pattern origin: [Karpathy llm-wiki.md](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)*
