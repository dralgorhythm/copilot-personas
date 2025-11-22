# Prompt Engineering & Agent Management Ecosystem

> **Mission**: To provide a unified, research-backed, and architecturally sound environment for creating, managing, and optimizing AI agents.

## 1. The Core Agent

*   [Principal Architect](../.github/agents/architect.agent.md): The central orchestrator for all prompt engineering tasks. Located in `.github/agents/`.

## 2. Standards & Frameworks

*   [Unified Prompt Engineering Standard (UPEMS)](standards/UnifiedPromptEngineeringStandard.md): The governing document for all agent architecture.
*   [Global Constitution](../.github/copilot-instructions.md): The repo-wide rules applied to all agents.

## 3. Guides

*   [Persona Creation Process](guides/creation-process.md): Step-by-step guide to building a new agent.
*   [Optimization Guide](guides/optimization-guide.md): Techniques for refining and tuning agents.
*   [Agentic Mechanisms](guides/agentic-mechanisms.md): Guide to using Skills and Hooks.

## 4. Templates

*   [Agent Definition](templates/agent-definition.yaml): The standard YAML/XML structure for `.agent.md` files.
*   [Artifact Plan](templates/artifact-plan.md): The blueprint format for "Architect" agents.

## 5. Context Architecture (The "Brain")

We use a hybrid of **Shared Context** and **Context Injection**.

*   **Context Injection** (`.github/instructions/`): Rules applied automatically based on file type.
    *   `prompt-engineering.instructions.md`: Rules for editing prompts.
    *   `typescript.instructions.md`: Rules for coding.
*   **Shared Context** (`shared-context/`): Reusable modules linked manually.
    *   [Core Values](shared-context/core-values.md)
    *   [Output Standards](shared-context/output-standards.md)

## 6. Agentic Mechanisms

We use advanced mechanisms to augment agent capabilities:

*   **Skills** (`.github/skills/`): Modular capabilities loaded on demand.
*   **Hooks** (`.github/hooks/`): Lifecycle event instructions (e.g., Pre-Prompt).

