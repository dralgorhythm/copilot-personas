# Task Decomposition Instructions
> **Apply To**: `plans/*.md`, `roadmaps/*.md`

Guidelines for breaking down complex requirements or architectural designs into actionable, atomic sub-tasks for implementation.

## <best_practices>
*   **Vertical Slicing**: Breaking down work by feature (end-to-end) rather than by architectural layer (UI, API, DB).
*   **Independence**: Tasks should be as independent as possible to allow parallel execution.
*   **Testability**: Every task must have clear acceptance criteria that can be verified.
*   **Value Delivery**: Prioritize tasks that deliver user value early (Vertical Slicing).
</best_practices>

## <concepts>
*   **Atomic Task**: A unit of work that is small enough to be completed in a single session or commit, and has a clear definition of done.
*   **Critical Path**: The sequence of dependent tasks that determines the minimum time needed to complete the project.
*   **Dependency Graph**: A directed graph representing the dependencies between tasks.
</concepts>
