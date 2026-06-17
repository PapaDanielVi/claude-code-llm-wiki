---
title: "Harness Engineering"
type: concept
created: 2026-06-17
updated: 2026-06-17
tags: [harness-engineering, agentic-ai, technology, ai-futures]
aliases: ["agent harness", "harness design", "agent = model + harness", "guides and sensors"]
sources: [agent-harness-engineering, harness-engineering-coding-agent-users]
---

## Summary

Harness engineering is the discipline of designing everything around a model so it can finish real work: prompts, tools, context policies, hooks, sandboxes, subagents, feedback loops, and recovery paths. The defining equation, coined by Viv Trivedy, is `agent = model + harness` — "if you're not the model, you're the harness." A raw model is not an agent; it becomes one once a harness gives it state, tool execution, feedback loops, and enforceable constraints. [[agent-harness-engineering]]

The load-bearing claim: a decent model with a great harness beats a great model with a bad harness. Most of the leverage people attribute to model choice actually lives in the harness, which is your surface area, not the provider's. [[agent-harness-engineering]]

Birgitta Böckeler's originating framing scopes this to the *user harness* a developer builds for their own system, distinct from the model and from the *builder harness* the coding-agent vendor ships. Its job is twofold: raise the probability the agent gets it right the first time, and self-correct issues before a human reviews them. [[harness-engineering-coding-agent-users]]

## Key Points

### Guides and sensors, computational and inferential
Böckeler's framing organizes the user harness along two orthogonal axes. **Guides feed forward** into generation (AGENTS.md, skills, rules, reference docs, how-tos, LSPs, CLIs, codemods); **sensors feed back**, pointing at the agent and into its self-correcting loop (review agents, static analysis, logs, the browser). Crossing that with execution type: **computational** controls are deterministic, fast, CPU-run, and reliable (tests, linters, type checkers, structural analysis), cheap enough for every change; **inferential** controls are semantic, GPU/NPU-run, slower, costlier, and non-deterministic (AI review, LLM-as-judge) but allow rich guidance and judgment. Coding conventions are feedforward + inferential; codemods are feedforward + computational; an ArchUnit module-boundary check is feedback + computational; review instructions are feedback + inferential. [[harness-engineering-coding-agent-users]]

### The steering loop and keeping quality left
The human's real job is to **steer** by iterating on the harness: when an issue recurs, tighten the guides and sensors so it becomes less probable or impossible. (This is the same idea as the ratchet below, framed as a control loop.) Borrowing from CI/CD, sensors are distributed across the change lifecycle by cost and speed and pushed as far **left** as possible: fast cheap checks (linters, quick tests, a basic review agent) run pre-commit; expensive ones (mutation testing, broad architectural review) run post-integration. Separately, **continuous drift/health sensors** run outside the change lifecycle against the whole codebase: dead-code detection, coverage-quality analysis, dependency scanners, and runtime monitors watching SLOs or sampling response quality. [[harness-engineering-coding-agent-users]]

### Regulation categories
The harness is a cybernetic governor; it helps to qualify what it regulates, because harnessability varies by category. **Maintainability** (internal code quality) is the easiest today: computational sensors reliably catch structural problems, LLMs partially catch semantic ones (semantic duplication, over-engineering) but expensively, and neither reliably catches misdiagnosis, unnecessary features, or misunderstood instructions. **Architecture fitness** defines and checks architecture characteristics via fitness functions (performance skills paired with perf tests, logging standards paired with log-quality reflection). **Behaviour** (does the app do what's needed?) is the open problem: today people feed forward a spec and feed back a green AI-generated test suite plus manual testing, which over-trusts AI-written tests. The [approved fixtures](https://lexler.github.io/augmented-coding-patterns/patterns/approved-fixtures/) pattern helps selectively but isn't a wholesale answer. [[harness-engineering-coding-agent-users]]

### Harnessability and harness templates
Not every codebase is equally amenable to harnessing. Strong typing gives type-checking for free; clear module boundaries afford architectural rules; frameworks like Spring abstract away whole classes of mistakes. Greenfield teams can bake harnessability in from day one; legacy teams face the harder problem that the harness is most needed where it is hardest to build. Böckeler predicts **harness templates**: per-topology bundles of guides and sensors (a Node dashboard, a JVM CRUD service, a Go event processor), an evolution of service templates, with the same drift and versioning problems, possibly worse given non-deterministic controls. [[harness-engineering-coding-agent-users]]

### The "skill issue" reframe
Most agent failures are configuration problems, not model problems (HumanLayer). The failure is usually legible and fixable in the harness: an unknown convention goes into `AGENTS.md`, a destructive command gets a blocking hook, a 40-step task gets split into planner + executor. Proof point: on Terminal Bench 2.0, the same model scores far lower inside one harness than another; Viv's team moved an agent Top 30 → Top 5 by changing only the harness. "The gap between what today's models can do and what you see them doing is largely a harness gap." [[agent-harness-engineering]]

### The ratchet
Treat every agent mistake as a permanent signal, not a one-off. Add constraints only when you've seen a real failure; remove them only when a capable model has made them redundant. Every line in a good `AGENTS.md` should trace to a specific thing that went wrong. This is why harness engineering is a discipline, not a framework — the right harness is shaped by your failure history, so you can't download it. [[agent-harness-engineering]]

### Working backwards from behavior
Design pattern: *behavior you want (or want to fix) → the harness piece that delivers it.* If you can't name the behavior a component exists to deliver, it shouldn't be there. The standard primitives, each mapped to a behavior the model can't deliver alone:
- **Filesystem + Git** → durable state: workspace, offload surface, coordination surface, plus versioning/rollback/branching. The foundational primitive most others point back to.
- **Bash + code execution** → a general-purpose tool: hand the agent a kitchen, don't pre-build every gadget.
- **Sandboxes + default tooling** → safe execution and self-verification: isolation, allow-listing, network isolation, plus runtimes, test CLIs, and a headless browser to observe its own work.
- **Memory files + web search + MCP** → continual learning across the training cutoff and across sessions.

### Battling context rot
Models degrade as the context window fills. Three recurring techniques (see [[context-management]]): **compaction** (summarize/offload old context), **tool-call offloading** (keep head/tail of large outputs, store the rest on disk), and **skills with progressive disclosure** (reveal tools only when needed). For very long jobs, Anthropic adds **full context resets** — rebuild the session from a compact hand-off file, because compaction alone was not sufficient.

### Long-horizon execution
Models suffer early stopping, poor decomposition, and incoherence across windows. The harness compensates with the **Ralph Loop** (a hook intercepts the exit attempt and re-injects the original prompt into a fresh window, reading prior state from disk), **planning** (decompose into a plan file plus self-verification hooks), and **planner/generator/evaluator splits** (separate generation from evaluation, since agents skew positive grading their own work). The **sprint contract** writes the done-condition before code, catching scope drift. See [[agentic-workflows]].

### Hooks: the enforcement layer
A hook runs at a lifecycle point and turns "I told the agent to do X" into "the system enforces X": run typecheck/lint/tests after each edit, block destructive bash, gate PRs and pushes, auto-format on write. Guiding principle: **success is silent, failures are verbose** — a passing check says nothing, a failing one injects its error text into the loop for self-correction.

### AGENTS.md and tool choice
The flat repo-root rulebook is the highest-leverage config because it lands in the system prompt every turn. Keep it short (under ~60 lines) and earn each line — "pilot's checklist, not style guide; ratchet, don't brainstorm." Same discipline for tools: ten focused tools beat fifty overlapping ones. Security note: tool descriptions are trusted prompt text, so a sloppy or malicious MCP can prompt-inject the agent before you type anything (see [[model-context-protocol]]).

### Harnesses don't shrink, they move
"Every component in a harness encodes an assumption about what the model can't do on its own" (Anthropic). When the model gets better at that thing, the component becomes dead code and should come out; when it unlocks something new, new scaffolding is needed to reach the new ceiling. Opus 4.6 killing the context-anxiety failure mode retired a whole class of scaffolding while opening tasks that need multi-day memory and multi-agent coordination instead.

### The model-harness training loop
Useful primitive discovered in the harness → standardized into the product → used to train the next model → next model improves at that primitive → repeat. Co-training means models overfit to their harness (a general model wouldn't care whether you used `apply_patch` or `str_replace`), which is why the same model feels different across harnesses and why changing a tool's logic can cause regressions.

### Harness-as-a-Service (HaaS)
The shift from LLM APIs (return a completion) to harness APIs (return a runtime): the Claude Agent SDK, Codex SDK, and OpenAI Agents SDK ship the loop, tools, context management, hooks, and sandbox primitives. The default path is now "pick a framework, configure four pillars (system prompt, tools, context, subagents), invest in domain-specific prompt/tool design." "You can't do iterations if you don't have a v0.1." See [[agentic-frameworks]].

## Connections

- [[harness-engineering-coding-agent-users]] — Böckeler's originating article; supplies the guides/sensors, computational/inferential, regulation-category, and harness-template framing
- [[agent-harness-engineering]] — Addy Osmani's synthesis; supplies the ratchet, hooks, HaaS, and the `agent = model + harness` equation
- [[birgitta-bockeler]] — author of the originating framing
- [[ai-scaffold-hierarchy]] — the same "scaffolding around the model" idea from the user's side (prompts → skills → plugins → MCPs); harness engineering is the engineering discipline that hardens it via the ratchet and hooks
- [[context-management]] — context rot, compaction, tool-call offloading, progressive disclosure, and context resets are the harness's context-engineering toolkit
- [[agentic-workflows]] — planning, self-verification, planner/evaluator splits, and the Ralph Loop are the long-horizon execution layer
- [[agentic-frameworks]] — the HaaS framework layer (LangChain, LangGraph, AutoGen, CrewAI, and the vendor Agent SDKs) that implements the loop, tools, and hooks
- [[model-context-protocol]] — MCP servers as harness tools, and their descriptions as a prompt-injection surface
- [[self-annealing]] — agents analyzing their own traces to fix harness-level failure modes is the self-healing frontier of harness design
- [[claude-skills]] — skills are the progressive-disclosure mechanism the harness uses to keep context lean

## Notes

The boundary with [[ai-scaffold-hierarchy]] is deliberate. That source treats the scaffold as a layered toolkit a user assembles (prompt vs skill vs plugin vs MCP). This concept is about the engineering practice: deriving each component from a named behavior, ratcheting constraints from observed failures, and enforcing them deterministically with hooks. Same object, two lenses.

*Inference (not yet confirmed by sources):* the ratchet ("every mistake becomes a rule") is the manual, human-driven version of [[self-annealing]]'s automated detect-diagnose-recover loop. A harness that "analyzes its own traces to fix harness-level failure modes" (Viv's open problem) would close that gap and make the ratchet autonomous.
</content>
