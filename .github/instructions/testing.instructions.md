# Testing Instructions
> **Apply To**: `**/*.test.*`, `**/*.spec.*`, `tests/**/*`

Guidelines for defining and executing a comprehensive testing plan that ensures software quality, reliability, and maintainability.

## <best_practices>
*   **Test Behavior, Not Implementation**: Tests should verify *what* the code does, not *how* it does it (avoids brittle tests).
*   **Fast Feedback**: Developers should be able to run relevant tests in seconds, not minutes.
*   **Determinism**: Tests must produce the same result every time. Flaky tests are worse than no tests.
*   **Isolation**: Tests should not depend on each other or shared mutable state (e.g., database records).
</best_practices>

## <concepts>
*   **Test Pyramid**: A strategy prioritizing many fast unit tests, fewer integration tests, and very few slow E2E tests.
*   **Mock vs Stub**: A Stub provides canned answers to calls; a Mock allows verifying that specific calls were made.
*   **TDD (Test Driven Development)**: Writing the test *before* the code (Red -> Green -> Refactor).
*   **BDD (Behavior Driven Development)**: Defining tests in natural language (Given/When/Then) to align with business requirements.
*   **Code Coverage**: The percentage of code lines/branches executed by the test suite.
</concepts>

## <tooling>
*   **Unit/Integration**: Jest, Vitest (JS/TS); Pytest (Python); JUnit 5 (Java); XUnit (.NET).
*   **E2E**: Playwright, Cypress, Selenium.
*   **Mocks**: Mockito (Java), unittest.mock (Python).
*   **Containers**: Testcontainers (Java/Go/Node) for real integration dependencies.
</tooling>
