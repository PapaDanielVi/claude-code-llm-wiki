---
title: "Prompt Engineering Hacks in 53 Mins (GPT, Claude)"
type: source
created: 2026-05-13
updated: 2026-05-13
tags: ["prompt-engineering", "llm", "ai", "best-practices"]
aliases: ["prompt-engineering-tips", "llm-prompting"]
---

# Prompt Engineering Hacks in 53 Mins (GPT, Claude)

## Summary
Key insights from Nick's video on prompt engineering best practices for getting reliable, high-quality outputs from LLMs like GPT and Claude. Focuses on practical, actionable tips rather than theoretical concepts.

## Key Points
- **Use API playgrounds**: Switch from consumer models (ChatGPT, Claude) to API playground/workbench versions for full control over parameters like temperature, max tokens, stop sequences, and system messages
- **Keep prompts short**: Model performance decreases significantly with prompt length; aim for ~250 tokens for optimal accuracy
- **Understand prompt types**: System (who the AI is), user (what you want it to do), assistant (using previous outputs as examples)
- **Leverage one-shot learning**: Adding just one example to your prompt often provides disproportionate accuracy improvements compared to zero-shot
- **LLMs are conversational engines**: They excel at reasoning and conversation but aren't reliable knowledge engines for factual recall
- **Be unambiguous**: Use specific, precise language to narrow the range of possible outputs (e.g., "list 5 products" vs "produce a report")
- **Adopt Spartan tone**: Use the term "Spartan" in tone of voice guidelines for the right balance of directness and flexibility
- **Iterate with data**: Test prompts multiple times (Monte Carlo approach) to measure consistency rather than relying on single lucky outputs
- **Define output formats explicitly**: Specify exact formats like JSON, CSV, or XML instead of vague requests for "reports" or "sheets"
- **Eliminate conflicting instructions**: Remove contradictory terms like "detailed summary" that cancel each other out and waste tokens
- **Learn data formats**: Understand XML, JSON, and CSV for structured output that integrates with other systems
- **Use key prompt structure**: Context → Instructions → Output Format → Rules → Examples
- **Generate examples with AI**: Use AI to create training examples for few-shot prompting
- **Choose appropriate models**: Don't overspend on expensive models unnecessarily, but don't cripple performance by using overly cheap models for important tasks

## Connections
- Related to: [[prompt-compression]], [[ai-scaffold-hierarchy]]
- Could connect to: [[concepts/automation]], [[concepts/claude-skills]]

## Notes
The speaker emphasizes that many prompt engineering "hacks" are actually just applications of understanding how LLMs work fundamentally. The most effective prompts combine brevity, clarity, structure, and empirical testing rather than relying on complex or verbose instructions.