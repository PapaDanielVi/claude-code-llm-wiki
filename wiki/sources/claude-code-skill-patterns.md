---
title: "Claude Code Skill Authorship Patterns"
type: source
created: 2026-05-06
updated: 2026-05-06
tags: [skill-design, ai-futures, research]
aliases: [claude-code-skills, skill-creation-workflow]
---

# Claude Code Skill Authorship Patterns

## Source
- **Type**: Screenshot / UI artifact
- **Path**: raw/attachments/1778013065635-Screenshot_2026-05-06_at_12.01.02_am.png
- **Context**: Claude Code CLI conversation about skill creation

## Summary

Screenshot of Claude Code conversation discussing skill authorship patterns, invocation triggers, and best practices. Covers:

1. **Skill Descriptions**: Should be concise (~200 characters or less preferred)
2. **Clear Scope**: Define success criteria explicitly
3. **Named Examples**: Use specific named examples instead of generic placeholders
4. **Trigger Context**: Skills should match their invocation context precisely

## Key Points

### What Triggers Skills

The conversation addresses what causes `/skill-create` to be invoked:
- The `/` prefix creates a shortcut to the skill's name
- Skills are typically invoked when their description matches the user's intent
- Named patterns work better than generic descriptions
- Clear scope definition helps with accurate triggering

### Three-Stage Workflow

Mentioned workflow for skill creation:
1. **Initialization** - Setting up the skill structure
2. **Authoring** - Writing the skill content
3. **Testing/Evaluation** - Validating the skill works correctly

### CLAUDE.md Role

The conversation references CLAUDE.md as the "root workspace config file" that can define workspace-specific skills and behaviors.

### Skill Invocation Patterns

- Skills respond to specific patterns in user requests
- The name itself (after `/`) is a trigger mechanism
- Better matching occurs when skill names are descriptive and unique
- Context matching helps route to appropriate skills

## Connections

- Related to [[skill-design]] concept
- Related to [[skills-and-agents-rules]] for operational guidelines

## Notes

This screenshot represents an interactive conversation where questions were asked about skill triggering. The responses provide practical guidance for skill authorship, emphasizing concise descriptions, clear scope definitions, and context-aware invocation patterns.

The conversation suggests that well-designed skills have:
- Short, descriptive names
- Explicit success criteria
- Named examples over placeholders
- Context-appropriate triggers

This aligns with the broader skill design principles documented in [[skill-authoring-best-practices]] and [[skills-and-agents-rules]].