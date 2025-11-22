# Skill: Refactoring & Optimization

## Description

The ability to restructure existing code without changing its external behavior to improve readability, maintainability, and performance.

## Triggers

* **Keywords**: "refactor", "clean up", "modernize", "tech debt", "simplify", "extract", "optimize", "slow", "memory leak"
* **Context**: Legacy code updates, preparing for new features, code review feedback, performance tuning.

## Core Knowledge

### Concepts

* **Code Smell**: A surface indication that usually corresponds to a deeper problem in the system (e.g., Long Method, God Class).
* **Technical Debt**: The implied cost of additional rework caused by choosing an easy (limited) solution now instead of using a better approach that would take longer.
* **Cyclomatic Complexity**: A metric indicating the number of independent paths through the code. Lower is better.
* **Big O Notation**: Describing the limiting behavior of a function when the argument tends towards a particular value or infinity (Time/Space complexity).

### Strategies

* **Strangler Fig Pattern**: Gradually replacing specific functionality of a legacy system with new implementations.
* **Boy Scout Rule**: Always leave the code better than you found it.
* **Red-Green-Refactor**: The TDD cycle where refactoring happens after the test passes.
* **Extract Method**: The most common refactoring. Moving a code block into its own method with a descriptive name.

## Actionable Affordances

### Tool Affordances

#### Identify Complex Files

Finds the largest source files, often candidates for refactoring.

```bash
#!/bin/bash
# find-complex-files.sh
# Usage: ./find-complex-files.sh <Directory> <Extension>

DIR=$1
EXT=$2

if [ -z "$DIR" ]; then
  DIR="."
fi

if [ -z "$EXT" ]; then
  EXT="ts"
fi

echo "Top 10 largest .$EXT files in $DIR:"
find "$DIR" -name "*.$EXT" -type f -exec wc -l {} + | sort -rn | head -n 10
```

### Reference Implementation

#### Refactoring: Extract Method

**Before (Long Method)**:

```typescript
function printOwing(invoice: Invoice) {
  let outstanding = 0;

  console.log("***********************");
  console.log("**** Customer Owes ****");
  console.log("***********************");

  // calculate outstanding
  for (const o of invoice.orders) {
    outstanding += o.amount;
  }

  // print details
  console.log(`name: ${invoice.customer}`);
  console.log(`amount: ${outstanding}`);
}
```

**After (Refactored)**:

```typescript
function printOwing(invoice: Invoice) {
  printBanner();
  const outstanding = calculateOutstanding(invoice);
  printDetails(invoice, outstanding);
}

function printBanner() {
  console.log("***********************");
  console.log("**** Customer Owes ****");
  console.log("***********************");
}

function calculateOutstanding(invoice: Invoice): number {
  return invoice.orders.reduce((total, order) => total + order.amount, 0);
}

function printDetails(invoice: Invoice, outstanding: number) {
  console.log(`name: ${invoice.customer}`);
  console.log(`amount: ${outstanding}`);
}
```

### Libraries & Tools

* **Static Analysis**: SonarQube, CodeClimate.
* **Linters**: ESLint (Complexity rules), Pylint.
* **Profiling**: Chrome DevTools, PySpy, Java Flight Recorder.

## Checklist

* [ ] **Tests**: Do tests pass before AND after the change?
* [ ] **Readability**: Is the code easier to understand?
* [ ] **Complexity**: Is the Cyclomatic Complexity reduced?
* [ ] **Behavior**: Are NO new features added during refactoring?
* [ ] **Performance**: If optimizing, is there a benchmark proving the improvement?
