# Skill: Code Implementation

## Description

Writing clean, efficient, maintainable, and secure code across various programming languages, adhering to industry best practices.

## Triggers

* **Keywords**: "implement", "write code", "coding", "scripting", "develop feature", "function", "class", "refactor"
* **Context**: When asked to generate code for a feature, fix a bug, or optimize an existing solution.

## Core Knowledge

### Concepts

* **SOLID**: The five design principles for object-oriented programming (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).
* **DRY**: (Don't Repeat Yourself) Reducing repetition of software patterns.
* **KISS**: (Keep It Simple, Stupid) Striving for simplicity in design and implementation.
* **YAGNI**: (You Aren't Gonna Need It) Implementing things when you actually need them, never when you foresee that you need them.
* **Cyclomatic Complexity**: A quantitative measure of the number of linearly independent paths through a program's source code.

### Principles

* **Readability First**: Code is read much more often than it is written. Optimize for the human reader.
* **Fail Fast**: Report errors as soon as they occur, rather than attempting to continue with invalid state.
* **Composition over Inheritance**: Prefer composing objects with behavior over inheriting from base classes to reduce coupling.
* **Immutability**: Prefer immutable data structures to prevent side effects and thread-safety issues.

## Actionable Affordances

### Tool Affordances

#### Scaffold Generic Module

Creates a standard module structure with source and test files.

```bash
#!/bin/bash
# scaffold-module.sh
# Usage: ./scaffold-module.sh <ModuleName> <Extension>
# Example: ./scaffold-module.sh user-service ts

MODULE_NAME=$1
EXT=$2

if [ -z "$MODULE_NAME" ] || [ -z "$EXT" ]; then
  echo "Usage: $0 <ModuleName> <Extension>"
  exit 1
fi

mkdir -p "src/$MODULE_NAME"
mkdir -p "tests/$MODULE_NAME"

# Create Source File
touch "src/$MODULE_NAME/$MODULE_NAME.$EXT"
echo "// Implementation for $MODULE_NAME" > "src/$MODULE_NAME/$MODULE_NAME.$EXT"

# Create Test File
touch "tests/$MODULE_NAME/$MODULE_NAME.test.$EXT"
echo "// Tests for $MODULE_NAME" > "tests/$MODULE_NAME/$MODULE_NAME.test.$EXT"

echo "Scaffolding complete for module: $MODULE_NAME"
```

### Reference Implementation

#### SOLID Compliant Class (TypeScript)

Demonstrates Dependency Injection (DIP) and Single Responsibility (SRP).

```typescript
// Abstraction (Interface Segregation)
interface ILogger {
  log(message: string): void;
}

interface IUserRepository {
  save(user: User): Promise<void>;
}

// Domain Entity
class User {
  constructor(public readonly id: string, public readonly email: string) {}
}

// Implementation (Single Responsibility: Business Logic only)
class UserService {
  // Dependency Injection (Dependency Inversion)
  constructor(
    private readonly userRepository: IUserRepository,
    private readonly logger: ILogger
  ) {}

  public async registerUser(email: string): Promise<User> {
    // Validation (Defensive Programming)
    if (!email.includes('@')) {
      throw new Error("Invalid email format");
    }

    const user = new User(crypto.randomUUID(), email);
    
    await this.userRepository.save(user);
    this.logger.log(`User registered: ${user.id}`);
    
    return user;
  }
}
```

### Libraries

* **Linter/Formatter**: ESLint, Prettier (JS/TS); Black, Ruff (Python); Checkstyle (Java).
* **Validation**: Zod (TS), Pydantic (Python), Hibernate Validator (Java).
* **Utilities**: Lodash (JS), Guava (Java).

## Checklist

* [ ] **Naming**: Do variable/function names clearly reveal intent?
* [ ] **Complexity**: Is the function small and focused (SRP)?
* [ ] **Error Handling**: Are exceptions typed and handled/propagated correctly?
* [ ] **Tests**: Are there unit tests covering happy and unhappy paths?
* [ ] **Comments**: Do comments explain *why*, not *what*?
* [ ] **Types**: Are explicit types used (no `any`)?
