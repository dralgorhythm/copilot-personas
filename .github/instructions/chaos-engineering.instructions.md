# Chaos Engineering Instructions
> **Apply To**: `chaos-mesh.yaml`, `gremlin.json`, `litmus/*.yaml`

Guidelines for proactively testing system resilience by injecting faults to identify weaknesses before they cause outages.

## <best_practices>
*   **Blast Radius**: Minimize the impact of the experiment. Start small (one instance) and expand.
*   **Rollback**: Ensure you can stop the experiment immediately if things go wrong.
*   **Observability**: You must have logs/metrics to see the effect of the experiment.
*   **Environment**: Run experiments in a safe environment (Staging) before attempting in Production.
</best_practices>

## <concepts>
*   **Hypothesis**: Define steady state (e.g., "System returns 200 OK").
*   **Variable**: Introduce a real-world event (e.g., "DB latency increases by 500ms").
*   **Experiment**: Run the test in a controlled environment.
*   **Verify**: Check if steady state is maintained.
</concepts>
