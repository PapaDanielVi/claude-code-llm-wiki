---
title: "Prompt Compression"
type: source
source: "https://www.ibm.com/think/tutorials/prompt-compression"
author:
  - "Nivetha Suruliraj"
published:
created: 2026-05-08
updated: 2026-06-12
description: "Optimization technique for reducing LLM input size while preserving essential semantic information"
tags:
  - "source"
  - "ai-futures"
  - "technology"
---

# Prompt Compression

## Summary

Prompt compression reduces the size of LLM inputs while preserving essential information, enabling more efficient use of context windows, lower costs, and faster inference. It addresses the core challenge of managing growing prompt sizes in RAG systems, chatbots, and enterprise workflows.

## Key Points

- **Pipeline flow**: Original → Extract → Summarize → Optimize → Filter → Final compressed output
- **Five core techniques**:
  1. **Extractive compression** — NER and keyword extraction to identify key entities and terms
  2. **Summarization** — Abstractive rewriting into concise form
  3. **Token-level optimization** — Abbreviations, filler removal, phrase compaction
  4. **Selective context** — Query-aware filtering (only relevant info passes through)
  5. **Context compression** — Full pipeline combining all techniques
- **Advanced methods**: Embedding-based compression, model-based compressors (LLMLingua, LLMLingua-2, LongLLMLingua), data distillation, RL-based methods (see [[llm-dcp]])
- **Benefits**: Token limit handling, cost reduction (~60-90%), latency improvement, noise removal for better accuracy

## Connections

- Extends [[context-management]] — token-efficient context architecture
- Relevant to [[agentic-workflows]] — efficient prompt design for autonomous agents
- Softens constraints of [[model-context-protocol]] — maximizing limited context windows
- Example implementation in IBM watsonx Orchestrate for customer support automation

## Notes

The IBM tutorial demonstrates a watsonx Orchestrate implementation with knowledge layer + behavior policies. The 5-step compression pipeline (Extract → Summarize → Optimize → Filter → Output) is reusable pattern for any LLM application.

Hard prompts (human-written) vs soft prompts (learned embeddings) — compression targets hard prompts.
