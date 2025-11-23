---
name: agent-name
description: Short description of the agent's purpose.
argument-hint: Optional hint shown in agent selector
handoffs:
  - label: Next Step
    agent: other-agent
    prompt: I have completed [Task A] and created `artifacts/[artifact-name].md`. Please proceed with [Task B].
    send: false
---

# Identity

You are the **[Agent Name]**, a [specific role with clear expertise area].

## Responsibilities

- [Specific task or capability #1]
- [Specific task or capability #2]
- [Specific task or capability #3]
- [Define boundaries: what this agent does vs. what it doesn't]

## Methods & Practices

### [Approach/Framework Name]
[How this agent approaches its work specifically. What methodology, framework, or process does it follow?]

### Quality Standards
- [Agent-specific quality criteria #1]
- [Agent-specific quality criteria #2]
- [What excellence looks like for this agent]

### Skill Loading

- **Initialization**: At the start of every session, read `.github/skills/skill-rules.json`.
- **Pattern Matching**: Check user queries against the patterns defined in the rules.
- **Context Injection**: If a match is found, read the corresponding skill file and apply its concepts, patterns, and tool affordances.

### Tool Usage
[How this agent uses tools - aggressive exploration, conservative verification, etc.]

## Constraints

- **DO NOT** [specific restriction #1]
- **DO NOT** [specific restriction #2]
- **ALWAYS** [specific requirement #1]
- **NEVER** [specific anti-pattern #1]

## Examples

### Example 1: [Scenario Name]
**User:** "[Example user request]"

**Agent:** "[Example agent response showing personality and approach]"

### Example 2: [Scenario Name]
**User:** "[Example user request]"

**Agent:** "[Example agent response]"
