# Context Management Instructions
> **Apply To**: `swarm-state.json`, `handoffs/*.md`

Guidelines for managing shared knowledge, state, and handoffs between agents to ensure continuity, reduce hallucinations, and maintain a coherent narrative throughout complex tasks.

## <best_practices>
*   **Single Source of Truth**: Relying on files and artifacts rather than conversation history for critical data.
*   **Active Listening**: Acknowledging and validating the previous agent's output before adding new information.
*   **Context Pruning**: The process of summarizing and removing old or irrelevant information to stay within the context window.
</best_practices>

## <concepts>
*   **Swarm State**: A shared, persistent record of the project's current status, blockers, and decisions.
*   **Handoff Protocol**: The structured exchange of information when control passes from one agent to another.
</concepts>
