---
title: "Claude Skills: Build Your First AI Assistant"
type: source
created: 2026-05-07
updated: 2026-05-07
tags:
  - skill-design
  - agentic-ai
  - claude-desktop
  - co-work
aliases:
  - "claude-skills-beginner-guide"
  - "teachers-tech-claude-skills"
source_url: "https://www.youtube.com/watch?v=... (Teachers Tech)"
---

## Summary

Beginner-oriented video walkthrough of Claude Skills on claude.ai and Co-work (desktop app). Covers skill anatomy, the built-in Skill Creator tool, and practical examples from zero to working skills. The most original contribution is the capability vs workflow skill taxonomy and the Co-work integration patterns for file-based skills.

## Key Points

### Skill Anatomy
- A skill is a folder containing `skill.md` with two parts: **summary** (name + one-line description) and **body** (step-by-step instructions)
- The summary is the "label on the outside of the folder" — Claude reads it first to decide whether to load the full skill
- Skills are just text files — edit and rerun, don't rebuild from scratch

### Progressive Disclosure (practical framing)
- Claude reads only the summary for each available skill, then loads full instructions only when the task matches
- With 10 skills, Claude isn't reading all 10 in full — only the relevant ones
- Keeps things fast and token-efficient

### Skill Creator (web + Co-work)
- Built-in skill that builds other skills through conversation
- User describes what they need → Claude asks clarifying questions → generates the full skill.md
- Works on claude.ai (web) and in Co-work (desktop)
- Skills created on the web carry over to Co-work and vice versa

### Capability vs Workflow Skills

The most actionable framework in the source:

| | Capability Skills | Workflow Skills |
|---|---|---|
| **Purpose** | Teach Claude HOW to do something it can't do well | Capture YOUR specific process and standards |
| **Obsolescence** | Become unnecessary as models improve | Never become obsolete — they're about your standards, not Claude's ability |
| **Examples** | Create Word docs, fill PDF forms, format spreadsheets | YouTube description format, content repurposing pipeline, pricing reply process |
| **Priority** | Build second | Build first — lasting value |

**Rule of thumb**: As Claude gets smarter, capability skills retire. Workflow skills compound.

### Co-work Integration Patterns

Co-work (desktop app tab) gives skills access to local files and folders:

**Folder-watching workflow**:
1. Create a folder (e.g., `content-repurposer/`)
2. Drop input files (e.g., `.sbv` subtitle files) into the folder
3. Skill processes every matching file, creates dated subfolder with outputs
4. Can be triggered via scheduled tasks

**Reference-file workflow**:
1. Skill references a local file (e.g., `pricing-tiers.pdf`)
2. On trigger, Claude reads the file, matches input to reference data, drafts output
3. Example: paste client email → Claude reads pricing PDF → drafts professional reply

**Gmail connector** (Co-work):
- Claude can search/read emails and create drafts (cannot send)
- Granular permissions: allow, ask, or block per action
- Combined with skills: "handle this pricing inquiry" → reads email → reads PDF → drafts reply

### Practical Skill Examples from Video

1. **YouTube Description Skill** (workflow) — hook, summary, timestamps, social links, CTA. Output as text file with line breaks preserved.
2. **Content Repurposer** (Co-work + workflow) — takes `.sbv` subtitle files, produces blog post + Twitter thread + email newsletter as Word docs. Folder-watching with scheduled triggers.
3. **Pricing Responder** (Co-work + workflow) — reads client inquiry, matches to pricing PDF tier, drafts professional reply. Flags services not in PDF for manual handling.

## Connections

- **Concept**: [[skill-design]] — capability vs workflow taxonomy adds to existing rigid vs flexible framework
- **Concept**: [[context-management]] — progressive disclosure practical framing
- **Concept**: [[skill-evaluation]] — Skill Creator runs test cases during creation
- **Source**: [[skills-and-agents-rules]] — skill.md format and structure
- **Source**: [[claude-code-skill-patterns]] — skill triggering and authoring workflow
- **Source**: [[complete-guide-building-skills]] — comprehensive skill creation guide

## Notes

The capability vs workflow distinction is orthogonal to the rigid vs flexible distinction in [[skill-design]]. A workflow skill can be rigid (exact YouTube description format) or flexible (content repurposing with adaptable tone). A capability skill can also be either. The capability/workflow axis answers "WHAT should I build?" while rigid/flexible answers "HOW should I write it?"

The Skill Creator's conversational approach is notable because it asks clarifying questions rather than guessing — same principle as the "Ask Test" in [[skill-evaluation]]. Good skill creators (human or AI) ask before building.

Co-work skills that reference local files blur the line between skills and agents — they gain tool access (file I/O, Gmail) that pure web skills don't have. This maps to the agent + skill pattern in [[agents-vs-skills]]: the skill provides the SOP, Co-work provides the tool access.
