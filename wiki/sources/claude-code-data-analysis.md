---
title: "Claude Code: Data Analysis Without the Spreadsheet Headaches"
type: source
source-type: video-transcript
raw-path: raw/Claude Code Data Analysis Without the Spreadsheet Headaches.md
created: 2026-05-07
updated: 2026-05-07
tags: [agentic-ai, claude-code, data-analysis, business-intelligence, workflow-design, vscode]
aliases: [data-analysis-without-spreadsheets, base-camp-brew, teachers-tech-data]
---

## Summary

Part 3 of Jamie's (Teachers Tech) Claude Code series. Takes two real-world-style spreadsheets — 12 months of sales data (600+ transactions) and 200 customer records — for a fictional coffee company (Base Camp Brew) and uses Claude Code as an AI agent to produce full business analysis reports. Demonstrates that non-technical business owners can get detailed, data-driven insights (trends, anomalies, specific recommendations) in ~5 minutes per report using only markdown workflows and CLAUDE.md, with zero coding, formulas, or pivot tables.

## Key Points

### The Setup

- Uses Claude Code as a VS Code extension (shows the editor-based workflow)
- Project structure mirrors the agentic workflow pattern from Part 2:
  - `CLAUDE.md` — business context, rules, formatting preferences
  - `resources/` — data files (Excel spreadsheets)
  - `workflows/` — reusable analysis process
  - `output/` — finished reports

### CLAUDE.md Configuration (Data Analysis Context)

The CLAUDE.md file for this project includes:
- **Project context** — what the business is, what data exists
- **Business details** — Base Camp Brew: 3 physical locations + online store, craft coffee company
- **Rules** — ask clarifying questions before analysis, show methodology, use actual numbers not vague statements, format dollar amounts, flag unusual findings, include specific recommendations, save reports to output folder
- **Structure** — resources, workflows, output folders

### The Data Analysis Workflow

Reusable workflow that follows four phases:
1. **Intake and scoping** — confirm which data files, ask about scope and constraints
2. **Data quality assessment** — check for missing values, anomalies, data issues
3. **Deep analysis** — multiple lenses (revenue, profit, channels, trends, anomalies, recommendations)
4. **Report production** — formatted tables, actual numbers, specific recommendations, top 3 actions

The workflow is pointed at a data file via natural language: "analyze resources/sales data using the data analysis workflow"

### Agent Asks Clarifying Questions First

Before analysis, the agent asks structured questions:
- **Metrics priority** — revenue vs profit vs volume weighting
- **Channel focus** — equal vs focused analysis across sales channels
- **Next quarter** — any planned changes that affect recommendations
- **Scope** — which analytical lenses to apply

This prevents wasted analysis on the wrong dimensions.

### Sales Analysis Results (~5 min)

- Bean subscription drives 32% of all profit; volume grew 84%
- Cold brew is massively seasonal (summer peak)
- Mall kiosk "isn't broken, it's just small"
- Two channels drive 78.5% of profit
- November 2025: 58.3% month-over-month profit drop flagged as anomaly
- Top 3 recommendations: double down on bean subscription, build winter product strategy, increase average transaction size at mall kiosk

### Customer Analysis Results (~5 min)

- Classic power law: 28% of customers generate 80% of all spend
- Median customer spends $3,352
- Online is the best acquisition channel (nearly double the repeat rate)
- Downtown shop acquires the most customers but has the lowest repeat rate (dropped 26%)
- 43 single-purchase customers identified as re-engagement target
- Recommendations: re-engagement campaign, investigate downtown retention, double down on online acquisition

### Iteration on Reports

Reports can be refined without starting over:
- "Add a comparison table showing all four channels side by side" → agent scans existing analysis and creates a new table
- Targeted feedback edits the existing report, not a fresh run
- Compounds quality across multiple rounds

### Reusability Argument

The core pitch: everything built is reusable. Next month, drop updated spreadsheets into resources/, run the same workflow. CLAUDE.md remembers business context, workflow file defines the process, agent memory recalls prior findings (e.g., "November had a supply issue"). Each run gets slightly smarter about the specific business.

### Not Just Coffee

The pattern generalizes: swap CLAUDE.md for your business, drop in your spreadsheets. Works for e-commerce sales, client invoices, marketing metrics, survey results.

## Notes

Demonstrates the full end-to-end agentic loop: intake → clarifying questions → analysis → structured report. The real value is reusability — same workflow runs monthly, and each iteration gets smarter due to agent memory and CLAUDE.md context.

## Connections

- Builds on: [[agentic-workflows]] — this is a direct application of the agentic workflow pattern from Part 2
- Related: [[context-management]] — CLAUDE.md as context architecture driving analysis quality
- Related: [[skill-design]] — workflow files as reusable instruction sets
- Source: [[claude-code-agentic-workflows]] — Part 2 of the series that established the foundational pattern
