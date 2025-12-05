# Refactoring and Clean Code (Polyglot)
> **Apply To**: `*`

These guidelines govern how agents and developers should refactor code to be robust, maintainable, and "agent-friendly" (high cognitive resonance), regardless of the implementation language.

## <coding_standards>
1.  **Safety First**: You **MUST** utilize the strictest available static analysis tools for the language (e.g., `strict` in TS, `mypy --strict` in Python, clippy in Rust).
2.  **Explicit Contracts**: You **MUST** define explicit return types and argument types at module boundaries. Avoid implicit `any` or `dynamic` typing.
3.  **Immutability by Default**: You **MUST** prefer immutable data structures to prevent side-effect bugs, unless performance critical paths require mutation.
4.  **Single Responsibility**: You **MUST** keep files and functions focused on a single responsibility.
</coding_standards>

## <best_practices>
*   **Domain Modeling**: Use semantic types (Value Objects) instead of primitives (e.g., `UserId` type vs `string`) to enforce correctness.
*   **Guard Clauses**: Use "Early Return" pattern to handle edge cases and remove indentation depth ("Happy Path" stays on the left).
*   **Result Pattern**: Where the language supports it (Rust, Go, TS with libraries), prefer returning error values over throwing unchecked exceptions.
*   **Functional Core**: Push side effects (I/O, DB calls) to the edges of the system ("Imperative Shell") and keep business logic pure.
</best_practices>

## <refactoring_protocols>
*   **Hardening**: The first step of refactoring legacy code is enabling strict linting/compiler flags and fixing the resulting errors.
*   **Extraction**: Break "God Functions" into smaller, named functions that do one thing well.
*   **Dependency Inversion**: Extract interfaces/traits for external dependencies to allow for easy mocking and testing.
</refactoring_protocols>

## <tooling>
*   **Linters**: ESLint (TS/JS), Ruff/Pylint (Python), Clippy (Rust), GolangCI-Lint (Go).
*   **Formatters**: Prettier (TS/JS), Black (Python), Rustfmt (Rust), Gofmt (Go).
</tooling>

## <concepts>
*   **Cognitive Resonance**: The quality of code being easy for both humans and AI agents to "understand". Explicit intent increases resonance.
*   **Cyclomatic Complexity**: A metric of branching logic. Keep it low by extracting conditional logic.
</concepts>
