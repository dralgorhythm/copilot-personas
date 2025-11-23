# Refactoring Instructions
> **Apply To**: `**/*`

Guidelines for restructuring existing code without changing its external behavior to improve readability, maintainability, and performance.

## <best_practices>
*   **Boy Scout Rule**: Always leave the code better than you found it.
*   **Red-Green-Refactor**: The TDD cycle where refactoring happens after the test passes.
*   **Extract Method**: The most common refactoring. Moving a code block into its own method with a descriptive name.
</best_practices>

## <concepts>
*   **Code Smell**: A surface indication that usually corresponds to a deeper problem in the system (e.g., Long Method, God Class).
*   **Technical Debt**: The implied cost of additional rework caused by choosing an easy (limited) solution now instead of using a better approach that would take longer.
*   **Cyclomatic Complexity**: A metric indicating the number of independent paths through the code. Lower is better.
*   **Big O Notation**: Describing the limiting behavior of a function when the argument tends towards a particular value or infinity (Time/Space complexity).
*   **Strangler Fig Pattern**: Gradually replacing specific functionality of a legacy system with new implementations.
</concepts>

## <tooling>
*   **Static Analysis**: SonarQube, CodeClimate.
*   **Linters**: ESLint (Complexity rules), Pylint.
*   **Profiling**: Chrome DevTools, PySpy, Java Flight Recorder.
</tooling>
