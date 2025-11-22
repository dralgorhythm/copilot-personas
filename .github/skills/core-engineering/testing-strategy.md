# Skill: Testing Strategy

## Description

The ability to define and execute a comprehensive testing plan that ensures software quality, reliability, and maintainability.

## Triggers

* **Keywords**: "test", "spec", "e2e", "unit", "integration", "mock", "stub", "jest", "junit", "pytest", "tdd", "bdd"
* **Context**: Writing new features, refactoring code, fixing bugs, setting up CI/CD.

## Core Knowledge

### Concepts

* **Test Pyramid**: A strategy prioritizing many fast unit tests, fewer integration tests, and very few slow E2E tests.
* **Mock vs Stub**: A Stub provides canned answers to calls; a Mock allows verifying that specific calls were made.
* **TDD (Test Driven Development)**: Writing the test *before* the code (Red -> Green -> Refactor).
* **BDD (Behavior Driven Development)**: Defining tests in natural language (Given/When/Then) to align with business requirements.
* **Code Coverage**: The percentage of code lines/branches executed by the test suite.

### Principles

* **Isolation**: Tests should not depend on each other or shared mutable state (e.g., database records).
* **Determinism**: Tests must produce the same result every time. Flaky tests are worse than no tests.
* **Fast Feedback**: Developers should be able to run relevant tests in seconds, not minutes.
* **Test Behavior, Not Implementation**: Tests should verify *what* the code does, not *how* it does it (avoids brittle tests).

## Actionable Affordances

### Tool Affordances

#### Scaffold Test File

Creates a standard test file structure based on the source file name.

```bash
#!/bin/bash
# scaffold-test.sh
# Usage: ./scaffold-test.sh <SourceFile>
# Example: ./scaffold-test.sh src/utils/math.ts

SRC_FILE=$1

if [ -z "$SRC_FILE" ]; then
  echo "Usage: $0 <SourceFile>"
  exit 1
fi

# Simple heuristic for test file location (colocation or __tests__)
TEST_FILE="${SRC_FILE%.*}.test.ts"

if [ -f "$TEST_FILE" ]; then
  echo "Test file already exists: $TEST_FILE"
  exit 1
fi

cat <<EOF > "$TEST_FILE"
import { describe, it, expect } from 'vitest';
// import { subject } from './$(basename "${SRC_FILE%.*}")';

describe('$(basename "${SRC_FILE%.*}")', () => {
  it('should behave as expected', () => {
    // Arrange
    const input = 1;

    // Act
    // const result = subject(input);

    // Assert
    expect(true).toBe(true);
  });
});
EOF

echo "Created test file: $TEST_FILE"
```

### Reference Implementation

#### AAA Pattern (Arrange, Act, Assert)

Standard pattern for organizing unit tests.

```typescript
import { UserService } from './user.service';
import { UserRepository } from './user.repository';

describe('UserService', () => {
  it('should create a new user when valid data is provided', async () => {
    // 1. ARRANGE: Prepare the environment and dependencies
    const mockRepo = { save: jest.fn() } as unknown as UserRepository;
    const service = new UserService(mockRepo);
    const userData = { email: 'test@example.com' };

    // 2. ACT: Execute the code under test
    const result = await service.createUser(userData);

    // 3. ASSERT: Verify the outcome
    expect(result.email).toBe(userData.email);
    expect(mockRepo.save).toHaveBeenCalledWith(expect.objectContaining(userData));
  });
});
```

### Libraries & Tools

* **Unit/Integration**: Jest, Vitest (JS/TS); Pytest (Python); JUnit 5 (Java); XUnit (.NET).
* **E2E**: Playwright, Cypress, Selenium.
* **Mocks**: Mockito (Java), unittest.mock (Python).
* **Containers**: Testcontainers (Java/Go/Node) for real integration dependencies.

## Checklist

* [ ] **Pyramid**: Are we writing mostly unit tests?
* [ ] **Edge Cases**: Do tests cover nulls, empty strings, and boundaries?
* [ ] **Independence**: Can tests run in parallel?
* [ ] **Cleanup**: Do integration tests clean up the DB after running?
* [ ] **CI**: Are tests running automatically on every PR?
