# Debugging Instructions
> **Apply To**: `**/*`

Guidelines for identifying, isolating, and resolving defects or unexpected behavior in software systems.

## <best_practices>
*   **Reproducibility**: A bug that cannot be reproduced cannot be confidently fixed. Create a minimal reproduction case.
*   **Fix the Cause, Not the Symptom**: Don't just patch the error (e.g., adding a null check) without understanding why the state was invalid.
*   **One Change at a Time**: Change only one variable per test iteration to isolate effects.
*   **Scientific Method**: Observe -> Hypothesize -> Predict -> Test -> Analyze.
*   **Rubber Ducking**: Explaining code, line-by-line, to an inanimate object (or colleague) to force detailed analysis.
</best_practices>

## <concepts>
*   **Heisenbug**: A software bug that seems to disappear or alter its behavior when one attempts to study it (e.g., by adding logging).
*   **Root Cause Analysis (RCA)**: The process of discovering the root causes of problems in order to identify appropriate solutions.
*   **Binary Search**: A strategy to isolate the source of a bug by repeatedly dividing the search space (e.g., git bisect, commenting out half the code).
</concepts>

## <tooling>
*   **Debuggers**: `pdb` (Python), `dlv` (Go), `gdb` (C/C++), VS Code Debugger.
*   **Tracing**: OpenTelemetry, Jaeger, Honeycomb.
*   **Logging**: Log4j (Java), Winston (Node), Structlog (Python).
</tooling>
