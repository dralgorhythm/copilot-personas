# Skill: Requirements Analysis

## Description

The process of eliciting, analyzing, documenting, and validating the requirements for a software product to ensure it meets stakeholder needs.

## Triggers

* **Keywords**: "requirement", "spec", "specification", "acceptance criteria", "user need", "use case", "user story", "prd"
* **Context**: Understanding what to build before designing or coding, clarifying vague requests, defining scope.

## Core Knowledge

### Concepts

* **Functional Requirements**: What the system should do (e.g., "User can log in").
* **Non-Functional Requirements (NFRs)**: How the system should perform (e.g., "Login takes < 1s"). Also known as Quality Attributes.
* **User Story**: A short, simple description of a feature from the perspective of the person who desires the new capability.
* **Acceptance Criteria**: Conditions that a software product must satisfy to be accepted by a user, customer, or other consuming system.
* **INVEST**: Acronym for good user stories: Independent, Negotiable, Valuable, Estimable, Small, Testable.

### Principles

* **Ambiguity Reduction**: Vague terms like "fast", "secure", or "scalable" must be quantified.
* **Problem over Solution**: Focus on the user's problem before jumping to technical solutions.
* **Traceability**: Every requirement should be traceable to a business goal and a test case.
* **Feasibility**: Requirements must be technically and economically feasible within constraints.

## Actionable Affordances

### Tool Affordances

#### Scaffold PRD (Product Requirement Document)

Creates a standard PRD template.

```bash
#!/bin/bash
# scaffold-prd.sh
# Usage: ./scaffold-prd.sh <FeatureName>

FEATURE_NAME=$1

if [ -z "$FEATURE_NAME" ]; then
  echo "Usage: $0 <FeatureName>"
  exit 1
fi

FILENAME="PRD-$FEATURE_NAME.md"

cat <<EOF > "$FILENAME"
# PRD: $FEATURE_NAME

## 1. Problem Statement
*   **What**: [Describe the problem]
*   **Who**: [Target User]
*   **Why**: [Business Value]

## 2. User Stories
| ID | As a... | I want to... | So that... |
| :--- | :--- | :--- | :--- |
| US-1 | [Role] | [Action] | [Benefit] |

## 3. Functional Requirements
1.  [Requirement 1]
2.  [Requirement 2]

## 4. Non-Functional Requirements
*   **Performance**: [Metric]
*   **Security**: [Constraint]
*   **Reliability**: [SLA]

## 5. Acceptance Criteria (Gherkin)
\`\`\`gherkin
Scenario: [Name]
  Given [Context]
  When [Event]
  Then [Outcome]
\`\`\`

## 6. Out of Scope
*   [Item 1]
EOF

echo "Created PRD template: $FILENAME"
```

### Reference Implementation

#### Standard User Story with Gherkin

```markdown
### User Story: Password Reset

**As a** registered user,
**I want to** reset my password via email,
**So that** I can regain access to my account if I forget my credentials.

### Acceptance Criteria

```gherkin
Scenario: Successful Password Reset Request
  Given the user is on the "Forgot Password" page
  And the user enters a valid email address "user@example.com"
  When they click the "Send Reset Link" button
  Then a confirmation message "Check your email" is displayed
  And a password reset email is sent to "user@example.com"
  And the email contains a unique, time-limited token link
```

### Tools

* **Documentation**: Confluence, Notion, Google Docs.
* **Tracking**: Jira, Linear, Azure DevOps, GitHub Issues.
* **Modeling**: Miro, Lucidchart (for User Flows).

## Checklist

* [ ] **Quantified**: Are NFRs measurable (e.g., "200ms" not "fast")?
* [ ] **Atomic**: Are user stories small enough to be completed in one sprint/session?
* [ ] **Testable**: Can a QA engineer write a test case based solely on the criteria?
* [ ] **Prioritized**: Is the priority (MoSCoW) clear?
* [ ] **Constraints**: Are technical and business constraints identified?
