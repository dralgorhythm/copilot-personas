# Implementing Code Instructions
> **Apply To**: `**/*.{ts,js,py,java,go,rs}`, `src/**/*`

Guidelines for writing clean, efficient, maintainable, and secure code across various programming languages.

## <coding_standards>
1.  **SOLID**: The five design principles for object-oriented programming (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).
2.  **DRY**: (Don't Repeat Yourself) Reducing repetition of software patterns.
3.  **KISS**: (Keep It Simple, Stupid) Striving for simplicity in design and implementation.
4.  **YAGNI**: (You Aren't Gonna Need It) Implementing things when you actually need them, never when you foresee that you need them.
5.  **Composition over Inheritance**: Prefer composing objects with behavior over inheriting from base classes to reduce coupling.
</coding_standards>

## <best_practices>
*   **Readability First**: Code is read much more often than it is written. Optimize for the human reader.
*   **Fail Fast**: Report errors as soon as they occur, rather than attempting to continue with invalid state.
*   **Immutability**: Prefer immutable data structures to prevent side effects and thread-safety issues.
*   **Cyclomatic Complexity**: Keep cyclomatic complexity low to ensure code is testable and understandable.
</best_practices>

## <testing_protocols>
*   **Unit Testing**: Test individual components in isolation.
*   **Edge Cases**: Explicitly test boundary conditions and invalid inputs.
*   **Happy Paths**: Verify the standard expected behavior.
*   **Error Paths**: Verify that exceptions and errors are handled correctly.
</testing_protocols>
