# Skill: Chaos Engineering

## Description
Proactively testing system resilience by injecting faults.

## Triggers
*   Keywords: "chaos", "fault injection", "resilience testing", "gremlin", "chaos monkey", "latency injection"
*   Context: Verifying that the system can withstand failures.

## Principles
*   **Hypothesis**: Define steady state (e.g., "System returns 200 OK").
*   **Variable**: Introduce a real-world event (e.g., "DB latency increases by 500ms").
*   **Experiment**: Run the test in a controlled environment (Staging first).
*   **Verify**: Check if steady state is maintained.
*   **Blast Radius**: Minimize the impact of the experiment.
