---
title: "Iterated Distillation and Amplification"
type: concept
created: 2026-05-06
updated: 2026-05-06
tags: [ai-research, technical, self-improvement]
aliases: [ida, iterated-distillation]
---

## Summary

Iterated Distillation and Amplification (IDA) is a self-improvement framework where AI models improve through cycles of amplification (more compute, longer thinking) and distillation (training smaller model to replicate results). Similar to AlphaGo's training via Monte-Carlo Tree Search + RL.

## Key Points

1. **Amplification**: Given model M0, improve by allowing longer thinking, running copies in parallel, consulting other AIs
2. **Distillation**: Train new model M1 to imitate Amp(M0) results faster/cheaper
3. **Repeat**: Each cycle produces smarter model

- **Historical precedent**: AlphaGo used MCTS (amplification) + RL (distillation)
- **Challenge**: Requires ground truth signal for quality evaluation
- **2027 breakthrough**: Models become good enough at evaluating subjective quality to apply IDA broadly

## Connections

- Source: [[ai-2027]]
- Related: [[neuralese]], [[ai-alignment]]

## Notes

- Early versions worked on math/coding (verifiable tasks) before expanding
- In AI 2027, IDA enables Agent-3 to become superhuman coder (Mar 2027)
- By Sep 2027, Agent-4 using IDA achieves superhuman AI researcher status