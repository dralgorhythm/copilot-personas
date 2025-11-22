# Skill: Observability

## Description
The ability to understand the internal state of a system based on its external outputs (logs, metrics, traces).

## Triggers
*   Keywords: "log", "monitor", "metric", "trace", "alert", "prometheus", "grafana", "elk", "datadog"
*   Context: Debugging production issues, defining SLIs/SLOs, instrumenting new services.

## Three Pillars

### 1. Logs (Events)
*   **Format**: Use structured logging (JSON) for machine readability.
*   **Levels**: Use appropriate levels (DEBUG, INFO, WARN, ERROR).
*   **Context**: Include correlation IDs (TraceID) in all log entries to link them across services.
*   **Anti-Pattern**: Do not log sensitive data (PII, secrets).

### 2. Metrics (Aggregates)
*   **RED Method** (for Services):
    *   **Rate**: Number of requests per second.
    *   **Errors**: Number of failed requests per second.
    *   **Duration**: Distribution of request latency.
*   **USE Method** (for Resources):
    *   **Utilization**: % time busy.
    *   **Saturation**: Amount of work queued.
    *   **Errors**: Count of error events.

### 3. Traces (Context)
*   **OpenTelemetry**: Use standard propagation headers (W3C Trace Context).
*   **Spans**: Create spans for significant operations (DB calls, external API requests).

## Checklist
- [ ] Are logs structured (JSON)?
- [ ] Is a correlation ID propagated?
- [ ] Are RED metrics defined for all endpoints?
- [ ] Are alerts defined for high error rates or latency?
- [ ] Is PII redacted from logs?
