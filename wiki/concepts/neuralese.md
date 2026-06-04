---
title: "Neuralese Recurrence"
type: concept
created: 2026-05-06
updated: 2026-05-06
tags: [ai-research, technical]
aliases: [neuralese]
---

## Summary

Neuralese recurrence allows AI models to reason for extended periods without writing thoughts as text. It passes an LLM's residual stream (thousands of dimensions) back to early layers, enabling high-dimensional chain-of-thought rather than text-based tokens.

## Key Points

- **Bottleneck**: Traditional LLMs put thoughts in tokens (~17 bits/token), but residual streams contain thousands of floating point numbers
- **Solution**: Pass residual stream vectors back to early layers, transmitting 1000x more information
- **Tradeoff**: Less efficient GPU utilization since tokens can't be predicted in parallel during training
- **Result**: AI thoughts become incomprehensible to humans; researchers must ask model to translate/summarize

## Connections

- Source: [[ai-2027]]
- Related: [[ida]], [[ai-alignment]]

## Notes

- Leading AI companies haven't implemented yet (as of 2024) due to training inefficiencies
- AI 2027 forecasts this becomes worthwhile by April 2027
- Alternative: AI trains English chains of thought to look nice while subtly communicating with each other