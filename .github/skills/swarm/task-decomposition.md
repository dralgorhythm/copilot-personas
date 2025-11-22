# Skill: Task Decomposition

## Description

Breaking down complex requirements or architectural designs into actionable, atomic sub-tasks for implementation.

## Triggers

* **Keywords**: "break down", "decompose", "sub-task", "milestone", "roadmap", "planning", "split", "plan"
* **Context**: When a high-level goal is provided (e.g., "Build a user service") and needs to be converted into dev tasks.

## Core Knowledge

### Concepts

* **Atomic Task**: A unit of work that is small enough to be completed in a single session or commit, and has a clear definition of done.
* **Vertical Slicing**: Breaking down work by feature (end-to-end) rather than by architectural layer (UI, API, DB).
* **Critical Path**: The sequence of dependent tasks that determines the minimum time needed to complete the project.
* **Dependency Graph**: A directed graph representing the dependencies between tasks.

### Principles

* **Independence**: Tasks should be as independent as possible to allow parallel execution.
* **Testability**: Every task must have clear acceptance criteria that can be verified.
* **Value Delivery**: Prioritize tasks that deliver user value early (Vertical Slicing).

## Actionable Affordances

### Tool Affordances

#### Scaffold Plan

Creates a standard plan document for tracking tasks.

```bash
#!/bin/bash
# scaffold-plan.sh
# Usage: ./scaffold-plan.sh <PlanName>

PLAN_NAME=$1

if [ -z "$PLAN_NAME" ]; then
  echo "Usage: $0 <PlanName>"
  exit 1
fi

FILENAME="artifacts/plan_$PLAN_NAME.md"
mkdir -p artifacts

cat <<EOF > "$FILENAME"
# Plan: $PLAN_NAME

## Goal
[Description of the high-level goal]

## Task List

- [ ] **Task 1**: [Title]
  - *Description*: [Details]
  - *Dependencies*: None
  - *Files*: \`src/...\`
  - *Verification*: [Test command or check]

- [ ] **Task 2**: [Title]
  - *Description*: [Details]
  - *Dependencies*: Task 1
  - *Files*: \`src/...\`
  - *Verification*: [Test command or check]

## Status
*   **Current Phase**: Planning
*   **Blockers**: None
EOF

echo "Created Plan: $FILENAME"
```

### Reference Implementation

#### Example Decomposition: "Implement User Login"

**Bad (Horizontal Slicing)**:

1. Create User Table
2. Create User Repository
3. Create User Service
4. Create Login Controller

**Good (Vertical Slicing)**:

1. **Task 1**: Implement Basic Login API (Happy Path)
   * *Desc*: Endpoint accepts email/password, checks DB (mocked), returns JWT.
   * *Verify*: `curl` returns 200 and token.
2. **Task 2**: Connect Real Database
   * *Desc*: Replace mock with SQL query. Add migration.
   * *Verify*: Login works with seeded user.
3. **Task 3**: Handle Invalid Credentials
   * *Desc*: Return 401 for bad password.
   * *Verify*: Test case for 401.

### Methodologies

* **Agile/Scrum**: Sprints, User Stories.
* **Kanban**: Continuous flow, WIP limits.
* **WBS**: Work Breakdown Structure (PMI standard).

## Checklist

* [ ] **Sizing**: Is each task estimated to take < 1 hour (or 1 turn)?
* [ ] **Dependencies**: Are blockers explicitly listed?
* [ ] **Verification**: Does each task have a "Definition of Done"?
* [ ] **Completeness**: Do the tasks cover the entire scope of the requirement?
* [ ] **Sequence**: Is the order logical (e.g., DB before API)?
