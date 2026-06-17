---
title: "Agent Harness Engineering"
type: source
created: 2026-06-17
updated: 2026-06-17
tags: [harness-engineering, agentic-ai, technology, ai-futures]
source-type: article
author: Addy Osmani
aliases: ["harness engineering"]
---

# Agent Harness Engineering

## Summary

Addy Osmani pulls together the emerging discipline of *harness engineering*: treating everything around the model (prompts, tools, context policies, hooks, sandboxes, subagents, feedback loops, recovery paths) as a real engineering artifact that tightens every time the agent slips. The framing equation, coined by Viv Trivedy, is `agent = model + harness` — "if you're not the model, you're the harness." The central claim: a decent model with a great harness beats a great model with a bad harness, and most of the leverage people attribute to model choice actually lives in the harness.

The post synthesizes work from Viv Trivedy ("Anatomy of an Agent Harness", and the HaaS framing), Dex Horthy, HumanLayer ("skill issue" reframe), Anthropic's engineering team (long-running harness design), and Birgitta Böckeler. Source: addyosmani.com, published 2026-04-19.

## Key Points

### Agent = Model + Harness
- A raw model is not an agent. It becomes one once a harness gives it state, tool execution, feedback loops, and enforceable constraints.
- A harness includes: system prompts / `CLAUDE.md` / `AGENTS.md` / skill files / subagent prompts; tools, skills, MCP servers and their descriptions; bundled infrastructure (filesystem, sandbox, browser); orchestration logic (subagent spawning, handoffs, model routing); hooks and middleware (compaction, continuation, lint); observability (logs, traces, cost/latency metering).
- Claude Code, Cursor, Codex, Aider, Cline are all harnesses. The model underneath is sometimes the same; the behavior you experience is dominated by what the harness does.
- Simon Willison's reduction: an agent "runs tools in a loop to achieve a goal." The skill is in designing both the tools and the loop.

### The "skill issue" reframe
- HumanLayer frames most agent failures as configuration problems, not model problems. The failure is usually legible: the agent didn't know a convention → add it to `AGENTS.md`; ran a destructive command → add a blocking hook; got lost in a 40-step task → split into planner + executor.
- Data point: on Terminal Bench 2.0, Claude Opus 4.6 inside Claude Code scores far lower than the same model in a custom harness. Viv's team moved an agent from Top 30 to Top 5 by changing only the harness.
- Models get post-training coupled to the harness they were trained against; moving them into a better-fitted harness can unlock capability the original was leaving on the floor. "The gap between what today's models can do and what you see them doing is largely a harness gap."

### The ratchet: every mistake becomes a rule
- Treat agent mistakes as permanent signals, not one-off stories or bad runs to retry.
- You only add constraints when you've seen a real failure; you only remove them when a capable model has made them redundant. Every line in a good `AGENTS.md` should trace back to a specific thing that went wrong.
- This is why harness engineering is a discipline, not a framework. The right harness is shaped by your failure history. You can't download it.

### Working backwards from behavior
- Viv's design pattern: *behavior we want (or want to fix) → harness design to deliver it.* If you can't name the behavior a component exists to deliver, it probably shouldn't be there.
- **Filesystem + Git (durable state)** — the most foundational primitive. Gives a workspace, an offload surface for intermediate work, and a coordination surface; Git adds versioning, rollback, and branching for free. Most other primitives end up pointing at the filesystem.
- **Bash + code execution (general-purpose tool)** — the main loop is a ReAct loop (reason → act → observe → repeat). Rather than pre-building a tool for every action, give the agent bash and let it build tools on the fly. "The difference between teaching someone to use a single kitchen gadget and handing them a kitchen."
- **Sandboxes + default tooling** — bash needs a safe place to run. Sandboxes give isolation, allow-listing, network isolation, on-demand spin-up/teardown. Good defaults ship runtimes, Git/test CLIs, and a headless browser so the agent can observe its own work and close the self-verification loop.
- **Memory + search (continual learning)** — models have no knowledge beyond weights + context. Memory file standards like `AGENTS.md` get injected every start; as the agent edits the file and the harness reloads it, knowledge carries across sessions. Web search and MCP tools (e.g., Context7) bridge the training cutoff.

### Battling context rot
- Context rot: models get worse at reasoning and task completion as the window fills. Three recurring techniques:
  - **Compaction** — summarize and offload older context when the window nears full (letting the API error is not an option for production).
  - **Tool-call offloading** — keep head/tail tokens of large outputs (e.g., a 2,000-line log) and offload the full text to the filesystem for read-on-demand.
  - **Skills with progressive disclosure** — reveal instructions and tools only when the task calls for them; loading everything at startup degrades performance before the first action.
- Anthropic adds **full context resets** for very long jobs: tear the session down and rebuild from a compact hand-off file. They are explicit that compaction alone was not sufficient. Closer to onboarding a new engineer than to "memory."

### Long-horizon execution: Ralph Loops, planning, verification
- Models suffer from early stopping, poor decomposition, and incoherence across multiple context windows. The harness designs around this.
- **Ralph Loop** — a hook intercepts the model's attempt to exit and re-injects the original prompt into a fresh context window, forcing continuation against a completion goal. Each iteration starts clean but reads prior state from the filesystem. Turns a single-session agent into a multi-session one.
- **Planning** — the model decomposes a goal into steps in a plan file on disk; the harness prompts/reminds it to use the file and runs self-verification (hooks run a test suite and loop failures back as error text).
- **Planner / generator / evaluator splits** — Anthropic finds separating generation from evaluation into distinct agents outperforms self-evaluation, because agents skew positive grading their own work ("GANs for prose"). Related: the **sprint contract**, where generator and evaluator negotiate what "done" means before code is written. Writing down the done-condition first catches scope drift.

### Hooks: the enforcement layer
- A hook runs at a lifecycle point (before tool call, after file edit, before commit, on session start). The difference between "I told the agent to do X" and "the system enforces X."
- Uses: run typecheck/lint/tests after each edit; block destructive bash (`rm -rf`, `git push --force`, `DROP TABLE`); require approval before PR/push to `main`; auto-format on write.
- Principle: **success is silent, failures are verbose.** If typecheck passes, the agent hears nothing; if it fails, the error text is injected and the agent self-corrects. Feedback is nearly free in the common case and directly actionable when it isn't.

### AGENTS.md and tool choice
- The flat markdown rulebook at repo root is the highest-leverage config point because it lands in the system prompt every turn.
- **Keep it short** (HumanLayer keeps theirs under 60 lines) — every line competes for attention; more rules make each rule matter less. "Pilot's checklist, not style guide."
- **Earn each line** — rules trace to a specific past failure or hard external constraint. "Ratchet; don't brainstorm."
- Same discipline for tools: ten focused tools beat fifty overlapping ones because the model can hold the menu in its head. Security note: tool descriptions are trusted text injected into the prompt, so a sloppy or malicious MCP can prompt-inject your agent before you type anything.

### Harnesses don't shrink, they move
- As models improve, the space of interesting harness combinations moves rather than shrinks. Opus 4.6 largely killed the context-anxiety failure mode (Sonnet 4.5 used to wrap up work prematurely near its perceived limit), making a class of anxiety-mitigation scaffolding dead code.
- But the ceiling moved with the model: newly reachable tasks bring new failure modes needing multi-day memory policy, multi-agent coordination, or design-quality evaluators. Anthropic: "every component in a harness encodes an assumption about what the model can't do on its own." When the model improves at that thing, the component should come out; when it unlocks something new, new scaffolding is needed.

### The model-harness training loop
- A feedback loop: a useful primitive is discovered in the harness → standardized into the product → used when training the next model → the next model gets better at that primitive → repeat.
- Today's agent products are post-trained with harnesses in the loop, so the model gets specifically better at filesystem ops, bash, planning, subagent dispatch. This co-training causes overfitting (a general model wouldn't care whether you used `apply_patch` or `str_replace`), and explains strange regressions when you change a tool's logic.
- Practical implication: a harness is a living system, not a one-time config; and the best harness isn't necessarily the one the model trained inside, it's the one designed for your task.

### Harness-as-a-Service (HaaS)
- Viv's framing: we're moving from building on LLM APIs (which return a completion) to harness APIs (which return a runtime). The Claude Agent SDK, Codex SDK, and OpenAI Agents SDK all point the same way: you get the loop, tools, context management, hooks, and sandbox primitives out of the box and customize them.
- The default path shifted from "build your own loop, tool-calling, state, approval flow" to "pick a harness framework, configure it along four pillars (system prompt, tools, context, subagents), and spend your effort on domain-specific prompt and tool design." That's what makes "skill issue" tractable.
- "Good agent building is an exercise in iteration. You can't do iterations if you don't have a v0.1." Start messy.

### Where this is going
- Top coding agents (Claude Code, Cursor, Codex, Aider, Cline) look more like each other than their underlying models do — harness patterns are converging on the load-bearing scaffolding.
- Open problems Viv highlights: orchestrating many agents in parallel on a shared codebase; agents that analyze their own traces to find and fix harness-level failures; harnesses that assemble the right tools and context just-in-time instead of being pre-configured at startup. That last one is "where harnesses stop being static config and start becoming something closer to a compiler."

## Connections

- [[harness-engineering]] — the concept page distilled from this source
- [[harness-engineering-coding-agent-users]] — Birgitta Böckeler's originating article that this post cites; the guides/sensors framing behind this synthesis
- [[birgitta-bockeler]] — one of the figures this source builds on, now with an entity page
- [[ai-scaffold-hierarchy]] — the "scaffold" / "agentic suit" framing is the same idea told through prompts → skills → plugins → MCPs; this source supplies the engineering discipline around it
- [[context-management]] — context rot, compaction, tool-call offloading, progressive disclosure, and full context resets all originate here
- [[agentic-workflows]] — planning, self-verification, planner/evaluator splits, and the Ralph Loop are the long-horizon execution patterns
- [[agentic-frameworks]] — HaaS and the SDKs (Claude Agent SDK, Codex SDK, OpenAI Agents SDK) are the framework layer this names
- [[model-context-protocol]] — MCP tool descriptions as trusted prompt text and the prompt-injection risk
- [[self-annealing]] — agents analyzing their own traces to fix harness-level failures is a harness-level self-healing frontier

## Notes

- People worth a future entity page (gap): **Viv Trivedy** (coined "harness engineering" and "Harness-as-a-Service"), **Addy Osmani** (author), **Dex Horthy** / **HumanLayer** (the "skill issue" reframe), **Fareed Khan** (estimated Claude Code architecture breakdown). **Birgitta Böckeler** now has an entity page ([[birgitta-bockeler]]) following the ingest of her own article.
- Fareed Khan's annotated Claude Code architecture maps nearly every concept above to a named component: knowledge layer (context injection), memory store + worktree isolator (loop state), permission gate (destructive-action hooks), multi-agent layer (subagent context firewalls), tool dispatch (where MCP and bash plug in).
- Nuance vs [[agentic-frameworks]]: that page notes CrewAI's retry loop *corrupting* parameters ("more self-review is not automatically safer"). This source argues separating generation from evaluation into distinct agents *does* help. Not a contradiction: the harm is from a self-review retry mutating good output; the benefit is from an independent evaluator. Both point to the same lesson — who verifies, and how, matters more than how much.

## Source

Raw article: `raw/Agent Harness Engineering.md`. By Addy Osmani, addyosmani.com/blog/agent-harness-engineering/, published 2026-04-19.
</content>
</invoke>
