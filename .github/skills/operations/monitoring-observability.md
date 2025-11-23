---
name: monitoring-observability
description: The ability to understand the internal state of a system based on its external outputs (logs, metrics, traces) to ensure reliability and performance.
---

# Monitoring Observability

## Workflows
<!-- Checklist for complex tasks -->
- [ ] **Logs**: Are logs structured (JSON)?
- [ ] **Correlation**: Is a correlation ID propagated across service boundaries?
- [ ] **Metrics**: Are RED metrics defined for all HTTP endpoints?
- [ ] **Alerts**: Are alerts defined for high error rates or latency (SLO breaches)?
- [ ] **Privacy**: Is PII redacted from logs and traces?

## Feedback Loops
<!-- Validation steps -->
1. Instrument code (OpenTelemetry).
2. Deploy to staging.
3. Generate traffic.
4. Verify logs in aggregator (Loki/ELK).
5. Verify metrics in dashboard (Grafana).
6. Verify traces (Jaeger/Tempo).

## Utility Scripts
<!-- Reference executable scripts -->
- `prometheus.yml`: Creates a basic Prometheus scrape config.

```yaml
# prometheus.yml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']

  - job_name: 'app_service'
    metrics_path: '/metrics'
    static_configs:
      - targets: ['app:8080']
```

## Reference Implementation
<!-- Code patterns -->

### OpenTelemetry Instrumention (Node.js)

Demonstrates setting up tracing and metrics.

```javascript
// instrumentation.js
const { NodeSDK } = require('@opentelemetry/sdk-node');
const { getNodeAutoInstrumentations } = require('@opentelemetry/auto-instrumentations-node');
const { PrometheusExporter } = require('@opentelemetry/exporter-prometheus');

const sdk = new NodeSDK({
  traceExporter: new ConsoleSpanExporter(),
  metricReader: new PrometheusExporter({
    port: 9464,
  }),
  instrumentations: [getNodeAutoInstrumentations()],
});

sdk.start();
```

## Resources
<!-- Links to external docs or local reference files -->
- [Observability Instructions](../../instructions/observability.instructions.md)
