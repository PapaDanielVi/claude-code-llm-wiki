---
title: "Agentic Data Analysis"
type: concept
created: 2026-05-07
updated: 2026-05-07
tags: [agentic-ai, claude-code, data-analysis, business-intelligence, no-code]
aliases: [data-analysis-without-code, ai-data-analysis, spreadsheet-analysis, agentic-analytics]
---

## Summary

Using AI agents (specifically Claude Code) to analyze business data — spreadsheets, CSVs, exports — without writing code, formulas, or pivot tables. The user points the agent at a data file, the agent asks clarifying questions about scope and priorities, runs the analysis through a reusable workflow, and produces structured reports with actual numbers, trend identification, anomaly flagging, and specific recommendations. The entire process takes ~5 minutes per report.

## Key Points

### How It Works

1. **CLAUDE.md** defines the business context (what the company does, what data exists, formatting rules)
2. **Workflow file** defines the analysis process step-by-step in plain English
3. **Agent** reads the data, asks clarifying questions, analyzes, and writes the report
4. **Output** goes to a designated folder as formatted markdown

### What Makes It Different From Excel

- No formulas to write or debug
- No pivot table configuration
- No manual scanning for patterns
- Agent finds trends you didn't know were there
- Agent flags anomalies with specific numbers
- Agent produces recommendations, not just charts
- Clarifying questions prevent analysis of the wrong things

### The Clarifying Questions Phase

The agent asks before analyzing to avoid wasted effort:
- Which metrics matter most? (revenue, profit, volume)
- Any channels or segments to focus on?
- Any known constraints or upcoming changes?
- How broad or narrow should the analysis be?

### Reusability

The pattern compounds over time:
- Same workflow runs on new data each month
- CLAUDE.md remembers business context across sessions
- Agent memory recalls prior findings (seasonal patterns, past anomalies)
- Each run gets slightly more domain-aware

### Generalization

The pattern works for any business with tabular data:
- E-commerce sales data
- Client invoices
- Marketing campaign metrics
- Survey results
- Inventory reports
- Health tracker exports

Just swap the CLAUDE.md for your context and drop in your data files.

### Limitations

- Depends on data quality (agent flags issues but can't fix messy data)
- Spreadsheets must be reasonably structured (headers, consistent format)
- Cross-referencing separate files requires joinable keys
- Agent findings need human judgment to validate (correlation vs causation)

## Connections

- Application of: [[agentic-workflows]] — data analysis is a specific use case for goal-driven AI processes
- Requires: [[context-management]] — CLAUDE.md as context architecture is what makes the analysis business-aware
- Related: [[skill-design]] — reusable workflow files are instruction sets
- Source: [[claude-code-data-analysis]]
- Source: [[claude-code-agentic-workflows]] — the foundational pattern this extends

## Notes

- Ideal for businesses that export data from CRMs, ERPs, or spreadsheets but lack in-house BI tooling
- The clarifying-questions phase is key — skipping it leads to analysis of the wrong dimensions
- Pair with [[agentic-workflows]] for the full pattern: data analysis is one application of the broader agentic workflow architecture
