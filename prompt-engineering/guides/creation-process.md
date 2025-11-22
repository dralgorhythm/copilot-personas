# Persona Creation Process

> **Goal**: Create a high-quality, specialized agent persona that integrates seamlessly into the swarm.

## <process_steps>

### 1. Role Definition

- **Check `AGENTS.md`**: Ensure the role doesn't already exist.
- **Define Scope**: What will this agent do? What will it *not* do?
- **Identify Handoffs**: Who will it talk to?

### 2. Research & Discovery

- **Task**: Ask `@research-assistant` to gather best practices for this specific role.
- **Output**: A list of key competencies, tools, and constraints.
- **Framework**: Use the `standards/PersonaResearchFramework.md`.

### 3. Drafting

- **Template**: Copy `templates/agent-definition.yaml`.
- **Structure**: Use **XML Tags** (`<role>`, `<constraints>`) as per the UACS.
- **Skills**: Identify required skills from `.github/skills/` and add them to the `skills` list.
- **Context**: Do not write generic rules. Instead, add a "Context Injection" section pointing to `.github/instructions/`.

### 4. Registration

- **Location**: Save the new persona file in `.github/agents/`.
- **Handoffs**: Update related agents if they need to handoff to this new agent.

### 5. Validation

- **Test Run**: Ask the new agent to perform a typical task.
- **Critique**: Does it follow the "Never List"? Does it use the correct output format?
- **Refine**: Adjust the prompt based on the test results.

</process_steps>
