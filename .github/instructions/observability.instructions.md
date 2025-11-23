# Observability Instructions
> **Apply To**: `prometheus.yml`, `grafana/*.json`, `otel-collector.yaml`, `fluentd.conf`

Guidelines for understanding the internal state of a system based on its external outputs (logs, metrics, traces) to ensure reliability and performance.

## <best_practices>
*   **Structured Logging**: Use structured logging (JSON) for machine readability.
*   **Correlation**: Include correlation IDs (TraceID) in all log entries to link them across services.
*   **RED Method**: Monitor Rate, Errors, and Duration for services.
*   **USE Method**: Monitor Utilization, Saturation, and Errors for resources.
*   **Privacy**: Redact PII from logs and traces.
</best_practices>

## <concepts>
*   **Logs (Events)**: Immutable records of discrete events.
*   **Metrics (Aggregates)**: Numerical data measured over time.
*   **Traces (Context)**: The path of a request through a distributed system.
*   **Cardinality**: The number of unique values in a metric dimension. High cardinality can crash monitoring systems.
</concepts>
