# Skill: Swarm Consensus

## Description
Mechanisms for agents to agree on decisions, architectural choices, or conflict resolution.

## Triggers
*   Keywords: "consensus", "agreement", "vote", "decision record", "adr", "quorum", "conflict", "disagree"
*   Context: When agents have conflicting outputs or need to ratify a major decision.

## Protocols

### 1. Conflict Resolution Matrix
| Priority | Domain | Owner Agent |
| :--- | :--- | :--- |
| 1 (Highest) | Security & Compliance | `security-auditor` |
| 2 | System Stability | `site-reliability-engineer` |
| 3 | Architecture & Scalability | `system-architect` |
| 4 | Feature Implementation | `builder` |

*   **Rule**: If `security-auditor` flags a risk, it blocks all lower-priority decisions until resolved.

### 2. Decision Records (ADR)
When a consensus is reached, generate a lightweight ADR:
- **Title**: [Short Description]
- **Status**: Proposed / Accepted / Rejected
- **Context**: The issue being discussed.
- **Decision**: The agreed path forward.
- **Consequences**: Pros/Cons.

### 3. Disagree and Commit
If consensus cannot be reached after 3 rounds of exchange:
1. The agent with the highest priority domain authority makes the final call.
2. Dissenting agents must record their objection in the "Consequences" section of the ADR but proceed with the decision.
