# Skill: Debugging & Troubleshooting

## Description

The systematic process of identifying, isolating, and resolving defects or unexpected behavior in software systems.

## Triggers

* **Keywords**: "debug", "fix bug", "troubleshoot", "error", "exception", "stack trace", "fail", "crash", "hang"
* **Context**: When a build fails, a test fails, a runtime error is reported, or the system behaves unexpectedly.

## Core Knowledge

### Concepts

* **Heisenbug**: A software bug that seems to disappear or alter its behavior when one attempts to study it (e.g., by adding logging).
* **Root Cause Analysis (RCA)**: The process of discovering the root causes of problems in order to identify appropriate solutions.
* **Rubber Ducking**: Explaining code, line-by-line, to an inanimate object (or colleague) to force detailed analysis.
* **Binary Search**: A strategy to isolate the source of a bug by repeatedly dividing the search space (e.g., git bisect, commenting out half the code).

### Principles

* **Scientific Method**: Observe -> Hypothesize -> Predict -> Test -> Analyze.
* **Reproducibility**: A bug that cannot be reproduced cannot be confidently fixed.
* **Fix the Cause, Not the Symptom**: Don't just patch the error (e.g., adding a null check) without understanding why the state was invalid.
* **One Change at a Time**: Change only one variable per test iteration to isolate effects.

## Actionable Affordances

### Tool Affordances

#### Debug Context Gatherer

Collects environment variables and recent logs to aid debugging.

```bash
#!/bin/bash
# debug-context.sh
# Usage: ./debug-context.sh <LogFile>

LOG_FILE=$1

echo "--- System Info ---"
uname -a
date

echo "--- Node/Runtime Versions ---"
node -v || echo "Node not found"
python3 --version || echo "Python not found"
java -version 2>&1 || echo "Java not found"

echo "--- Environment Variables (Safe) ---"
env | grep -v -E "KEY|SECRET|TOKEN|PASSWORD" | sort

if [ -n "$LOG_FILE" ] && [ -f "$LOG_FILE" ]; then
  echo "--- Recent Logs (Last 50 lines) ---"
  tail -n 50 "$LOG_FILE"
else
  echo "--- No Log File Provided or Found ---"
fi
```

### Reference Implementation

#### Structured Logging (Python)

Using structured logs (JSON) makes debugging easier in aggregation tools.

```python
import logging
import json
import sys

class JsonFormatter(logging.Formatter):
    def format(self, record):
        log_record = {
            "timestamp": self.formatTime(record),
            "level": record.levelname,
            "message": record.getMessage(),
            "module": record.module,
            "line": record.lineno
        }
        # Add extra context if available
        if hasattr(record, "user_id"):
            log_record["user_id"] = record.user_id
            
        return json.dumps(log_record)

logger = logging.getLogger("app")
handler = logging.StreamHandler(sys.stdout)
handler.setFormatter(JsonFormatter())
logger.addHandler(handler)
logger.setLevel(logging.INFO)

# Usage
def process_request(user_id):
    logger.info("Processing request", extra={"user_id": user_id})
    try:
        # ... logic ...
        raise ValueError("Invalid input")
    except Exception as e:
        logger.error(f"Failed to process: {str(e)}", extra={"user_id": user_id})

process_request("user_123")
```

### Libraries & Tools

* **Debuggers**: `pdb` (Python), `dlv` (Go), `gdb` (C/C++), VS Code Debugger.
* **Tracing**: OpenTelemetry, Jaeger, Honeycomb.
* **Logging**: Log4j (Java), Winston (Node), Structlog (Python).

## Checklist

* [ ] **Reproduction**: Do we have a minimal reproduction case?
* [ ] **Logs**: Have we checked the logs for stack traces or error codes?
* [ ] **Recent Changes**: What changed recently? (Check `git log` or `git bisect`).
* [ ] **Environment**: Is this happening in all environments (Dev, Prod) or just one?
* [ ] **Assumptions**: Are we assuming something (e.g., "Database is up") that we haven't verified?
