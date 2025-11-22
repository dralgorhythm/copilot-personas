# Skill Definition Standard

## Overview
This standard defines the structure and required components for "Rich Skills" in the Copilot Personas repository. All new skills must adhere to this schema to ensure consistency and provide actionable affordances (tools, code) to the agent.

## Schema

### 1. Metadata
*   **Description**: A concise summary of the skill.
*   **Triggers**: Keywords and context that activate the skill.

### 2. Core Knowledge
*   **Concepts**: Key terms and definitions (Ubiquitous Language).
*   **Principles**: Guiding rules or heuristics.

### 3. Actionable Affordances
*   **Tool Affordances (Bash)**: Embedded bash scripts that the agent can suggest or execute to perform tasks related to the skill (e.g., scaffolding, analysis).
    *   *Constraint*: Scripts must be idempotent and safe to run.
    *   *Format*: Markdown code blocks with `bash` language identifier.
*   **Reference Implementations**: Pseudo-code or polyglot examples demonstrating the skill's patterns.
*   **Libraries**: A list of recommended libraries or frameworks for major languages (e.g., Java, Python, TypeScript, .NET).

### 4. Resources
*   Links to detailed markdown files in a `resources/` subdirectory for complex topics.

## Formatting Rules
*   Use Markdown headers for sections.
*   Code blocks must specify the language.
*   Bash scripts should include comments explaining their purpose.
