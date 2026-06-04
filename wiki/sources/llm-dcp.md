---
title: "Dynamic Compressing Prompts for Efficient Inference of Large Language Models"
type: source
source: "https://arxiv.org/html/2504.11004v1"
author:
  - "Jinwu Hu"
  - "Wei Zhang"
  - "Yufeng Wang"
  - "Yu Hu"
  - "Bin Xiao"
  - "Mingkui Tan"
  - "Qing Du"
published: 2025-04-08
created: 2026-05-08
updated: 2026-05-08
description: "LLM-DCP: task-agnostic prompt compression via Markov Decision Process, RL-trained DCP-Agent with hierarchical curriculum training, achieving 12.9x compression without output degradation"
tags:
  - "source"
  - "ai-futures"
  - "research"
  - "prompt-compression"
---

# Dynamic Compressing Prompts for Efficient Inference of Large Language Models

## Summary

LLM-DCP models prompt compression as a Markov Decision Process (MDP), training a DCP-Agent via reinforcement learning (PPO) to iteratively remove redundant tokens. The reward function balances compression rate, LLM output distribution, and key information retention. A Hierarchical Prompt Compression (HPC) curriculum strategy progressively increases compression difficulty. Achieves 12.9x compression on Arxiv-March23 with 3.04% Rouge-2 improvement over SOTA.

## Key Points

### Core Innovation: MDP-based Compression
- **Prompt compression as sequential decision-making**: Each token removal decision depends on evolving context (not independent/entropy-based)
- **DCP-Agent**: Learns to iteratively compress by building on previous compression decisions
- **States**: compressed prompt at each timestep; **Actions**: retain/discard each token (binary 0/1); **Rewards**: compression rate + KL divergence of outputs + key info retention (BERTScore)

### Reward Function Design
```
R = α(1/ρ) + β·D(s₀,sₜ) - γ·KL(P(sₜ_G|sₜ), P(s₀_G|s₀)) - penalties
```
- α component: compression ratio reward
- β component: key information retention (BERTScore between original/compressed)
- γ component: LLM output distribution alignment (via smaller aligned model, not black-box)
- Penalties: over/under-compression bounds

### HPC Training Strategy (Curriculum Learning)
- 3 stages with progressive difficulty
- Stage 1: high compression ratio bounds → Stage 3: tighter bounds
- ψ=0.10 controls difficulty ramp
- Relative improvement: 25.5% compression ratio, 0.5 EM metric

### Distribution Alignment
- Uses Llama3-8B fine-tuned on alpaca-gpt4-data instead of black-box GPT-4o-mini for reward signals
- Significantly reduces training cost

### Results
| Dataset | Method | Compression | Rouge-2 |
|--------|--------|-------------|---------|
| Arxiv-March23 | LLMLingua-2 | 12.0x | 14.62 |
| Arxiv-March23 | LLM-DCP | **12.9x** | **15.94** (+9.03%) |
| GSM8K (1-shot) | LLMLingua-2 | 5.7x | 76.87 EM |
| GSM8K (1-shot) | LLM-DCP | **6.9x** | **77.03 EM** (+21.1% ratio) |

## Connections

- Extends [[prompt-compression]] — research-grade MDP formulation vs. IBM tutorial's rule-based pipeline
- Related to [[context-management]] — upstream token reduction before LLM input
- RL-based approach relates to [[agentic-workflows]] — sequential decision-making agent architecture
- Complements [[model-context-protocol]] — different angle on maximizing context window efficiency

## Notes

**Why MDP over entropy-based methods**: Prior methods (Selective-Context, LLMLingua) estimate token importance independently using self-information. LLM-DCP recognizes each token's significance depends on context decisions already made — sequential dependency.

**No black-box LLM for training**: Unlike TAIL-RL or other RL methods, LLM-DCP trains reward function using distribution-aligned small model, making it practical.

**Code**: https://github.com/Fhujinwu/DCP
