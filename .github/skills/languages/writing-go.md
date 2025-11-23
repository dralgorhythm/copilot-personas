---
name: Writing Go
description: Writing efficient, idiomatic Go code with proper concurrency patterns and error handling.
---

# Writing Go

## Workflows

### 1. Scaffold Go Module

Creates a standard Go module with common structure.

```bash
#!/bin/bash
# create-go-module.sh
# Usage: ./create-go-module.sh <module-name>

MODULE_NAME=$1

if [ -z "$MODULE_NAME" ]; then
  echo "Usage: $0 <module-name>"
  exit 1
fi

mkdir -p "$MODULE_NAME"
cd "$MODULE_NAME"

# Initialize module
go mod init "$MODULE_NAME"

# Create directory structure
mkdir -p cmd/server
mkdir -p internal/handlers
mkdir -p pkg
mkdir -p test

# Create main.go
cat <<EOF > cmd/server/main.go
package main

import (
    "fmt"
    "log"
)

func main() {
    fmt.Println("Starting $MODULE_NAME")
    if err := run(); err != nil {
        log.Fatal(err)
    }
}

func run() error {
    // Application logic here
    return nil
}
EOF

# Create Makefile
cat <<EOF > Makefile
.PHONY: build test lint run

build:
	go build -o bin/server ./cmd/server

test:
	go test -v -race -cover ./...

lint:
	golangci-lint run

run:
	go run ./cmd/server
EOF

echo "Go module structure created: $MODULE_NAME"
```

### 2. Go Code Review

Review Go code for idiomatic usage and correctness.

1. **Error Check**: Are all errors checked and handled?
2. **Context Check**: Is `context.Context` propagated correctly?
3. **Concurrency Check**: Are goroutines managed to prevent leaks?
4. **Resource Check**: Are resources (files, connections) closed using `defer`?
5. **Lint Check**: Does the code pass `golangci-lint`?

## Feedback Loops

### 1. Automated Linting

* **Trigger**: Pre-commit or CI.
* **Action**: Run `golangci-lint` to catch style and correctness issues.
* **Outcome**: Consistent code style and fewer bugs.

### 2. Race Detection

* **Trigger**: CI Test Suite.
* **Action**: Run tests with the race detector enabled (`go test -race`).
* **Outcome**: Identification of data races in concurrent code.
