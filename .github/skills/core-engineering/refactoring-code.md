---
name: refactoring-code
description: Applies holistic Clean Code refactoring and architectural optimization to any codebase.
---

# Refactoring Code (Polyglot)

## Workflows

- [ ] **Phase 1: Environmental Hardening**
    - [ ] Enable strictest compiler/linter settings for the language (e.g., `strict` TS, `strict` MyPy).
    - [ ] Run analysis tools and identify baseline errors.
    - [ ] Resolution: Add types, fix nullability issues, remove unused code.

- [ ] **Phase 2: Complexity Reduction**
    - [ ] Identify high Cyclomatic Complexity functions.
    - [ ] Apply "Extract Method" to isolate logic chunks.
    - [ ] Apply "Replace Nested Conditional with Guard Clauses".
    - [ ] Simplify boolean logic.

- [ ] **Phase 3: Domain Alignment**
    - [ ] Identify "Primitive Obsession" (e.g., using strings for IDs).
    - [ ] Create/Extract Value Objects or dedicated Types.
    - [ ] Rename variables/functions to match Domain Language (Ubiquitous Language).

- [ ] **Phase 4: Architectural Alignment**
    - [ ] Identify "God Classes" / "God Modules".
    - [ ] Separate Pure Logic (Core) from I/O (Shell).
    - [ ] Define explicit Interfaces/Traits for dependencies.

## Feedback Loops
1.  **Analyze**: Run linter/compiler.
2.  **Test**: Run existing tests (must pass).
3.  **Review**: Check if code reads like a sentence.

## Reference Implementation (General Pattern)

```typescript
// BEFORE: Guard clauses missing, primitive obsession, mixed levels of abstraction
function process(data: any) {
  if (data != null) {
      if (data.isValid) {
         // ... strict logic mixed with DB calls ...
      }
  }
}

// AFTER: Guard clauses, typed input, separation of concerns
function process(data: ValidatedInput): Result<Success, Error> {
  if (!data) return Result.fail("Missing data");
  
  const coreResult = coreLogic(data); // Pure
  return dbAdapter.save(coreResult); // Impure
}
```

## Resources
- [Refactoring and Clean Code](../../instructions/core-engineering/refactoring-clean-code.md)
- [Python Development](../../languages/writing-python.md)
- [TypeScript Development](../../languages/writing-typescript.md)
- [Go Development](../../languages/writing-go.md)
- [Rust Development](../../languages/writing-rust.md)
