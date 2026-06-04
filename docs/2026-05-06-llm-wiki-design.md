# LLM Wiki Schema Design

**Purpose:** Personal knowledge base using LLM as wiki maintainer
**Focus:** Self-improvement, health, psychology (holistic)
**Interaction:** Active partner with proactive nudges

## Directory Structure

```
claude-code-llm-wiki/
├── raw/                    # Immutable source documents (read-only by LLM)
│   ├── articles/          # Clipped web articles
│   ├── books/             # Book notes, PDFs
│   ├── journals/          # Journal entries
│   └── app-data/          # Health tracker exports (Whoop, Apple Health, etc.)
├── wiki/                   # LLM-generated content (LLM-owned)
│   ├── entities/          # Person, place, thing, habit, practice pages
│   ├── concepts/          # Topic, theme, model, abstract ideas
│   ├── insights/          # Syntheses, analyses, comparisons
│   │   └── slides/        # Marp presentations
│   ├── sources/           # Source summaries (linked to raw/)
│   │   └── app-data/     # App data summaries
│   └── assets/
│       └── charts/        # Generated visualizations
├── meta/                   # LLM internal tracking
│   ├── health-check.md    # Proactive health nudges
│   └── patterns.md        # Pattern detection tracking
├── log.md                  # Chronological activity log
├── CLAUDE.md               # This schema (also serves as LLM instructions)
└── README.md               # Quick start guide
```

**Key conventions:**
- `raw/` is immutable — LLM reads but never modifies
- `wiki/` is LLM-owned — all content creation goes here
- `log.md` is append-only — records all operations chronologically
- `index.md` tracks every page with one-liner summary

## Page Types

| Type        | Purpose                                              | Example                                                       |
| ----------- | ---------------------------------------------------- | ------------------------------------------------------------- |
| **Entity**  | Discrete item: person, place, thing, habit, practice | `entities/standing-desk.md`, `entities/john-smith.md`         |
| **Concept** | Abstract topic, theme, framework                     | `concepts/habit-loop.md`, `concepts/cognitive-distortions.md` |
| **Insight** | Synthesis, analysis, comparison, generated content   | `insights/q2-health-review.md`, `insights/habit-vs-goal.md`   |
| **Source**  | Summary of raw document                              | `sources/article-morning-routine.md`                          |

**Naming conventions:**
- Filenames: lowercase-with-hyphens.md
- Entity names: full name or descriptor (e.g., `standing-desk` not `standing_desk`)
- Timestamps in frontmatter, not filenames
- No spaces in filenames

**Standard page structure:**
```markdown
---
title: "Page Title"
type: entity|concept|insight|source
created: 2026-05-06
updated: 2026-05-06
tags: [domain, specificity]
sources: [linked sources if applicable]
aliases: [alternative names]
---

## Summary
One-paragraph overview.

## Key Points
- Bulleted takeaways

## Connections
- Related links to other wiki pages

## Notes
- Personal observations, questions, contradictions
```

## Frontmatter Schema

**Universal fields (all pages):**
```yaml
---
title: "Page Title"
type: entity|concept|insight|source
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [tag1, tag2]
aliases: [alt-name-1, alt-name-2]
---
```

**Domain tags:**
- `#self` — self-improvement, habits, goals, productivity
- `#health` — physical health, fitness, nutrition, sleep
- `#psych` — psychology, emotions, relationships, therapy

**Type-specific fields:**

*Entity:*
```yaml
entity-type: person|place|thing|habit|practice
```

*Source:*
```yaml
source-type: article|book|podcast|journal|app-data
raw-path: raw/articles/example.md
```

*Insight:*
```yaml
related-sources: [source-1, source-2]
confidence: high|medium|low
```

## Ingest Workflow

**Trigger:** New source in `raw/` OR scheduled check-in

**Steps:**
1. LLM reads source from `raw/`
2. For app data: parse structured export (JSON, CSV)
3. Write summary to appropriate `wiki/sources/` subdirectory
4. Update related `wiki/entities/` and `wiki/concepts/` pages
5. Create cross-references (bidirectional links)
6. Append entry to `log.md`
7. Update `wiki/index.md`

**Log entry format:**
```markdown
## [YYYY-MM-DD] ingest | Source Title
- Source: sources/example.md
- Entities updated: entity-1, entity-2
- Concepts updated: concept-1
- Tags: #domain
```

**App data specifics:**
- Export to `raw/app-data/[source]/[date].json`
- Ingest creates structured summary with key metrics
- Updates trend entries in relevant entity pages
- Flags anomalies in `meta/patterns.md` for proactive nudges

## Proactive Nudge System

**Scheduled check-ins:**
- **Weekly:** "Any new journal entries or health data to process?"
- **Monthly:** Health metric review, wiki lint pass
- **Quarterly:** Synthesis of period's themes, slide deck generation

**Pattern detection:**
- **Contradictions:** New source contradicts existing claim → flag it
- **Trending:** Same topic mentioned 3+ times → suggest synthesis
- **Gaps:** Important concept mentioned but no page → create it
- **Neglect:** Page not updated in 30 days → prompt refresh
- **Anomaly:** Health metric spike/drop → surface for reflection

**Implementation:**
- LLM maintains `meta/health-check.md` and `meta/patterns.md`
- Reviewed before each new session
- Nudges raised at session start or during natural conversation flow

## Query Workflow

**When you ask a question:**
1. LLM reads `wiki/index.md` to find relevant pages
2. Drills into relevant pages (reads frontmatter + summary sections)
3. Synthesizes answer from wiki content
4. Cites sources (links to wiki pages)
5. Offers to file answer as new `wiki/insights/` page

**Output formats** (specify in query or use default):
- **Markdown** — structured text (default)
- **Table** — comparisons, pros/cons, rankings
- **Chart** — matplotlib/observable for metrics/trends
- **Marp slides** — presentations
- **Canvas** — visual diagrams for concept mapping

**Compounding principle:** Good answers get filed back to wiki. Exploration results are preserved, not lost to chat history.

## Index and Log Format

### `wiki/index.md` — Content Catalog

Updated on every ingest. Structure:

```markdown
# Index

## Entities
- [habit-loop](entities/habit-loop.md) — trigger-routine-reward model (BJ Fogg)
- [standing-desk](entities/standing-desk.md) — current desk setup since 2024

## Concepts
- [habit-loop](concepts/habit-loop.md) — BJ Fogg behavior model
- [cognitive-distortions](concepts/cognitive-distortions.md) — CBT thought errors

## Insights
- [q2-health-review](insights/q2-health-review.md) — health metrics Q2 2026
- [habit-vs-goal](insights/habit-vs-goal.md) — systems vs targets

## Sources
- [whoop-export-week-23](sources/whoop-export-week-23.md) — HRV, RHR, recovery
- [article-morning-routine](sources/article-morning-routine.md) — cold + sunlight

## Assets
- [charts/](wiki/assets/charts/) — health trend visualizations
- [slides/](wiki/insights/slides/) — Marp presentations
```

### `log.md` — Activity Log

Append-only chronological record. Format:

```markdown
# Log

## [2026-05-06] ingest | Article: "The Science of Habit Formation"
- Source: sources/article-habit-science.md
- Updated: habit-loop, behavior-change
- Tags: #self, #psych

## [2026-05-05] query | "What's my current exercise pattern?"
- Answered from: habit-loop, health-metrics
- Filed as: insights/exercise-pattern-q2.md

## [2026-05-01] lint | Weekly health check
- Flags: 3 mentions of "stress" without coping strategy entry
- Action: Nudged user to log stress management activity
```

**Parsing tip:** Entries start with `## [YYYY-MM-DD]` — grep for recent entries:
```bash
grep "^## \[" log.md | tail -5
```

## Visualization Stack

| Format            | Tool                                     | Use Case                                           |
| ----------------- | ---------------------------------------- | -------------------------------------------------- |
| **Charts**        | matplotlib (Python) or Observable/Kotlin | Health trends, habit streaks, comparisons          |
| **Tables**        | Markdown                                 | Comparisons, rankings, pros/cons                   |
| **Slides**        | Marp                                     | Quarterly reviews, health summaries, presentations |
| **Dynamic views** | Dataview (Obsidian plugin)               | Frontmatter queries, filtered lists                |
| **Concept maps**  | Canvas                                   | Complex relationships, visual brainstorming        |

**Chart workflow:**
1. LLM generates chart code (Python/matplotlib or JS/Observable)
2. Saves to `wiki/assets/charts/[name].png`
3. Links from relevant pages: `![[charts/name.png]]`

**Marp workflow:**
1. LLM generates Marp markdown
2. Saves to `wiki/insights/slides/[name].md`
3. Obsidian Marp plugin renders in preview mode

## Conventions Summary

1. **Files:** lowercase-with-hyphens.md
2. **Frontmatter:** title, type, created, updated, tags, aliases
3. **Page sections:** Summary, Key Points, Connections, Notes
4. **Log format:** `## [YYYY-MM-DD] operation | Title`
5. **Index:** updated on every ingest, one-liner per page
6. **Links:** bidirectional wiki links between related pages
7. **Assets:** charts in `wiki/assets/charts/`, slides in `wiki/insights/slides/`
8. **Meta tracking:** `meta/health-check.md`, `meta/patterns.md` for proactive nudges

## Wiki Health (Lint Checklist)

Periodically run these checks:
- [ ] Contradictions between pages
- [ ] Stale claims superseded by newer sources
- [ ] Orphan pages (no inbound links)
- [ ] Concepts mentioned but lacking dedicated page
- [ ] Missing cross-references
- [ ] Health metric anomalies to surface
- [ ] Neglected pages (>30 days since update)
