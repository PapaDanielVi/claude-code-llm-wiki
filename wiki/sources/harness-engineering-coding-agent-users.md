---
title: "Harness Engineering for Coding Agent Users"
type: source
created: 2026-06-17
updated: 2026-06-17
tags: [harness-engineering, agentic-ai, technology, ai-futures]
source-type: article
author: Birgitta Böckeler
aliases: ["harness engineering for coding agent users", "guides and sensors"]
---

# Harness Engineering for Coding Agent Users

## Summary

Birgitta Böckeler lays out a mental model for the *outer harness* a developer builds around a coding agent: not the model and not the agent's built-in scaffolding, but the user-controllable layer of guides and sensors that a team adds for its own system. The originating framing the [[agent-harness-engineering]] (Addy Osmani) source later builds on. The article reframes harness components along two axes (feedforward guides vs feedback sensors, and computational vs inferential execution), frames the whole thing as a [cybernetic governor](https://en.wikipedia.org/wiki/Cybernetics) regulating the codebase toward a desired state, and argues the human's real job is to *steer* by iterating on that system over time.

A well-built outer harness has two goals: raise the probability the agent gets it right the first time, and provide a self-correcting feedback loop that catches issues before a human sees them. The payoff is less review toil, higher system quality, and fewer wasted tokens. Source: martinfowler.com, published 2026-04-02 (supersedes a February 2026 memo).

## Key Points

### Harness as a bounded context
- "Harness" has come to mean everything in an agent except the model itself (`agent = model + harness`), but that is too wide. Böckeler narrows it to coding agents and splits it into three concentric layers: the **model** at the core, the **builder harness** the coding-agent vendor ships (system prompt, retrieval, orchestration), and the **user harness** the developer builds for their own use case and system. The article is about that outermost ring.

### Guides (feedforward) and sensors (feedback)
- **Guides feed forward** into the agent's generation: AGENTS.md, skills, rules, reference docs, how-tos, language servers (LSP), CLIs, scripts, codemods.
- **Sensors feed back**, pointing at the agent and into its self-correcting loop: review agents, static analysis, logs, the browser.
- A human sits to the left of both, steering the guides and the sensors.

### Computational vs inferential
- **Computational** — deterministic and fast, run by the CPU: tests, linters, type checkers, structural analysis. Milliseconds to seconds, reliable. Cheap enough to run on every change.
- **Inferential** — semantic analysis, AI code review, "LLM as judge", run by a GPU/NPU. Slower, more expensive, non-deterministic, but allow rich guidance and semantic judgment. With a strong, task-suitable model, inferential sensors can still increase trust despite the non-determinism.
- The two axes are orthogonal. Examples: coding conventions = feedforward + inferential (AGENTS.md, skills); codemods = feedforward + computational (OpenRewrite recipes); structural tests = feedback + computational (an ArchUnit pre-commit/agent hook checking module boundaries); review instructions = feedback + inferential (skills); project bootstrap instructions = feedforward + both (a skill plus a bootstrap script).

### The steering loop
- The human's job is to **steer** the agent by iterating on the harness. When an issue recurs, improve the feedforward and feedback controls so it becomes less probable or is prevented outright.
- AI itself makes the harness cheaper to build: agents can write structural tests, draft rules from observed patterns, scaffold custom linters, or generate how-tos from codebase archaeology.

### Timing: keep quality left
- Borrowed from [continuous integration / continuous delivery](https://martinfowler.com/articles/continuousIntegration.html): distribute checks across the lifecycle by cost, speed, and criticality, and push them as far left as possible because earlier issues are cheaper to fix.
- Fast and cheap, run pre-commit / pre-integration: linters, fast test suites, a basic review agent.
- Expensive, run post-integration in the pipeline (plus a repeat of the fast checks): mutation testing, a broader review that considers the bigger picture.
- **Continuous drift / health sensors** run *outside* the change lifecycle, against the whole codebase: dead-code detection, test-coverage quality analysis, dependency scanners. Runtime monitoring is a frontier: agents watching degrading SLOs and suggesting fixes, or AI judges sampling response quality and flagging log anomalies.

### Regulation categories
The harness is a cybernetic governor; it helps to qualify *what* it regulates, because harnessability and complexity vary by category.
- **Maintainability harness** — internal code quality. The easiest type today because so much existing tooling applies. Computational sensors reliably catch structural problems (duplicate code, cyclomatic complexity, missing coverage, architectural drift, style). LLMs can *partially* catch semantic problems (semantically duplicate code, redundant tests, brute-force fixes, over-engineering), but expensively and probabilistically, not every commit. Neither reliably catches the highest-impact failures: misdiagnosis, unnecessary features, misunderstood instructions. Correctness is outside any sensor's remit if the human never specified what they wanted.
- **Architecture fitness harness** — defines and checks architecture characteristics, i.e. [fitness functions](https://www.thoughtworks.com/en-de/radar/techniques/architectural-fitness-function). E.g. skills that feed forward performance requirements paired with performance tests that feed back regressions; logging-standard skills paired with debugging instructions that make the agent reflect on log quality.
- **Behaviour harness** — "the elephant in the room": does the app functionally do what's needed? High-autonomy users today feed forward a functional spec (a short prompt to multi-file descriptions) and feed back a green AI-generated test suite plus coverage, sometimes mutation testing, plus manual testing. This puts too much faith in AI-generated tests. The [approved fixtures](https://lexler.github.io/augmented-coding-patterns/patterns/approved-fixtures/) pattern helps in some areas but isn't a wholesale answer. Good behaviour harnesses that reduce supervision are still an open problem.

### Harnessability
- Codebases differ in how amenable they are to harnessing. A strongly typed language gives type-checking as a free sensor; clear module boundaries afford architectural rules; frameworks like Spring abstract away details so the agent can't get them wrong. Without those properties, the corresponding controls can't be built.
- Greenfield teams can bake harnessability in from day one. Legacy teams with accrued technical debt face the harder problem: the harness is most needed exactly where it's hardest to build.

### Harness templates
- Most enterprises have a few service topologies covering ~80% of needs (API-backed business services, event processors, data dashboards), often already codified as service templates. These may evolve into **harness templates**: a bundle of guides and sensors that leashes an agent to a topology's structure, conventions, and tech stack. Teams might start picking stacks partly by which harnesses already exist.
- Same problems as service templates, maybe worse: instantiated templates drift from upstream improvements, and non-deterministic guides/sensors are harder to version and test.

### Open questions
- How to keep a harness coherent as it grows, with guides and sensors in sync and not contradicting each other.
- How far agents can be trusted to make sensible trade-offs when instructions and feedback signals point in different directions.
- If sensors never fire, is that high quality or inadequate detection? We need a "coverage" measure for harnesses, analogous to code coverage and mutation testing for tests.
- Tooling to configure, sync, and reason about feedforward/feedback controls as one system, rather than scattered across delivery steps.
- Building the outer harness is an ongoing engineering practice, not a one-time configuration.

## Connections

- [[harness-engineering]] — the concept page; this source supplies its guides/sensors and computational/inferential vocabulary and the regulation categories
- [[agent-harness-engineering]] — Addy Osmani's later synthesis, which cites Böckeler; same `agent = model + harness` core, told through the ratchet, hooks, and HaaS rather than guides/sensors
- [[birgitta-bockeler]] — author
- [[claude-skills]] — skills are the primary inferential feedforward guide (and inferential feedback, for review skills)
- [[model-context-protocol]] — an MCP server that reaches a team's knowledge tool is a feedforward guide in the change lifecycle
- [[context-management]] — keeping checks "left" and progressive disclosure both manage what reaches the agent and when
- [[self-annealing]] — the OpenAI "garbage collection" / Thoughtworks "janitor army" drift scans where agents suggest fixes are the self-healing end of continuous sensors
- [[agentic-workflows]] — distributing feedforward and feedback across a change's lifecycle is workflow design

## Notes

- Real-world harness examples the article cites: an [OpenAI team](https://openai.com/index/harness-engineering/) using custom linters, structural tests, and recurring "garbage collection" drift scans (their hardest problems are now "designing environments, feedback loops, and control systems"); [Stripe's minions](https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents) with heuristic pre-push hooks and "blueprints" that bake sensors into the workflow ("shift feedback left"); and Thoughtworks teams tackling architecture drift with mixes of agents and custom linters ("janitor army").
- Mutation testing and structural testing are framed as underused computational feedback sensors now having a resurgence; LSP integration is the example of an emerging computational feedforward guide.
- GenAI (Claude and Claude Code) was used for research and language polishing, per the author's disclosure.
- This article supersedes Böckeler's February 2026 memo on harness engineering (the memo URL now redirects here).

## Source

Raw article: `raw/Harness engineering for coding agent users.md`. By Birgitta Böckeler, martinfowler.com/articles/harness-engineering.html, published 2026-04-02.
