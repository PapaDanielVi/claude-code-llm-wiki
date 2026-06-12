---
title: "Agentic Frameworks"
type: concept
created: 2026-06-12
updated: 2026-06-12
tags:
  - agentic-ai
  - technology
  - frameworks
aliases:
  - agent frameworks
  - multi-agent frameworks
sources: [top-5-agentic-frameworks-2026]
---

# Agentic Frameworks

## Summary

Agentic frameworks are the orchestration libraries (LangChain, LangGraph, AutoGen, CrewAI, OpenAI Swarm) that wrap an LLM in an execution loop — managing state, tool calls, retries, and multi-agent coordination. The core insight from benchmarking: with the same underlying model, the framework's inner loop architecture dominates agent behavior — how it recovers from errors, whether it can parallelize tool calls, and how much token/latency overhead it adds. [[top-5-agentic-frameworks-2026]]

## Key Points

- **Architecture determines behavior, not the LLM**: identical models produce different pivot rates, costs, and failure modes depending on the framework's loop mechanism [[top-5-agentic-frameworks-2026]]
- **Four loop archetypes**:
  - *State machine* (LangGraph) — never forgets, but accumulated state can re-trigger completed steps
  - *Conversation loop* (AutoGen) — resilient feedback nudging, native parallel tool calls
  - *Managerial process* (CrewAI) — role/goal/backstory discipline, but verbose monologue and self-correction loops; plan-centric (0% pivot under tool failure)
  - *Sequential executor* (LangChain) — cheapest for linear flows; tool exceptions fatal by default until wrapped
- **Verification machinery can hurt**: CrewAI's retry loop corrupted parameters the LLM had originally gotten right — more self-review is not automatically safer [[top-5-agentic-frameworks-2026]]
- **Goal-centric vs plan-centric** is the key behavioral split: goal-centric agents (LangGraph, AutoGen) construct alternative execution paths when tools fail; plan-centric agents (CrewAI) wait for or retry the assigned tool
- **Framework selection heuristic** (per the benchmark): LangChain for cheap linear pipelines/RAG, LangGraph for stateful enterprise logic, AutoGen for resilience and parallel tool use, CrewAI for role-structured transparent workflows, Swarm for quick prototypes

## Connections

- [[agentic-workflows]] — frameworks are the infrastructure layer these workflows run on; Claude Code's dynamic workflows solve the same orchestration problem with a different design
- [[model-context-protocol]] — MCP standardizes tool integration across systems, whereas each framework defines tools its own way
- [[automation]] — error-recovery and pivot capacity determine how unattended a system can safely run
- [[self-annealing]] — feedback-loop architectures (state machine, conversation loop) natively support detect-diagnose-recover patterns; plan-centric ones resist them

## Source

- [[top-5-agentic-frameworks-2026]] — AIMultiple benchmark: 2,000 runs across 5 tasks, plus qualitative comparison tables

## Notes

- The wiki's existing agentic content is Claude Code-centric; this page is the first coverage of the broader open-source framework ecosystem.
- *Inference (not yet confirmed by sources)*: the benchmark's "goal-centric vs plan-centric" split maps onto Claude Code's dynamic workflow patterns — loop-until-done and adversarial verification assume goal-centric agents. A future source comparing Claude Code's orchestration with these frameworks would confirm or refute this.
