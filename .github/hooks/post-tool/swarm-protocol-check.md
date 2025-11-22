# Hook: Swarm Protocol Check

## Trigger
Runs after an agent generates a final response or artifact.

## Action
1.  **Validation**:
    - Did the agent acknowledge any active blockers from `swarm-state.json`?
    - If a decision was made, was an ADR or consensus record created?
    - If handing off, is the summary clear?

2.  **Correction**:
    - If the output violates a protocol (e.g., ignoring a security blocker), reject the output and prompt the agent to revise.
