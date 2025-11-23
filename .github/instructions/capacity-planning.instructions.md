# Capacity Planning Instructions
> **Apply To**: `k6.js`, `jmeter.jmx`, `hpa.yaml`, `scaling-policy.json`

Guidelines for estimating resource needs, planning for scale, and ensuring system stability under varying load conditions.

## <best_practices>
*   **Horizontal over Vertical**: Prefer adding more nodes (scaling out) over adding more power to a single node (scaling up) for resilience and cost-efficiency.
*   **No Single Point of Failure (SPOF)**: Ensure redundancy for every component in the critical path.
*   **Graceful Degradation**: The system should maintain partial functionality when some components fail or are overloaded.
*   **Measure, Don't Guess**: Base capacity decisions on load testing data and production metrics, not intuition.
</best_practices>

## <concepts>
*   **Little's Law**: The long-term average number of customers in a stable system $L$ is equal to the long-term average effective arrival rate $\lambda$ multiplied by the average time a customer spends in the system $W$ ($L = \lambda W$).
*   **Headroom**: The difference between the maximum capacity of the system and the current load.
*   **Backpressure**: A mechanism for a system to signal to upstream producers that it is overwhelmed and cannot accept more work.
*   **Throttling/Rate Limiting**: Controlling the rate of traffic sent or received by a network interface or controller.
</concepts>
