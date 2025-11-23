---
name: Writing Python
description: Writing clean, maintainable, and performant Python code following modern best practices and type safety.
---

# Writing Python

## Workflows

### 1. Scaffold Python Project

Creates a standard Python project with src layout and testing.

```bash
#!/bin/bash
# create-python-project.sh
# Usage: ./create-python-project.sh <ProjectName>

PROJECT_NAME=$1

if [ -z "$PROJECT_NAME" ]; then
  echo "Usage: $0 <ProjectName>"
  exit 1
fi

mkdir -p "$PROJECT_NAME/src/$PROJECT_NAME"
mkdir -p "$PROJECT_NAME/tests"

# Create pyproject.toml
cat <<EOF > "$PROJECT_NAME/pyproject.toml"
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"

[project]
name = "$PROJECT_NAME"
version = "0.1.0"
requires-python = ">=3.11"
dependencies = []

[tool.pytest.ini_options]
testpaths = ["tests"]
pythonpath = ["src"]

[tool.black]
line-length = 100

[tool.ruff]
line-length = 100
EOF

# Create initial files
touch "$PROJECT_NAME/src/$PROJECT_NAME/__init__.py"
touch "$PROJECT_NAME/tests/__init__.py"
echo "# $PROJECT_NAME" > "$PROJECT_NAME/README.md"

echo "Project structure created for: $PROJECT_NAME"
```

### 2. Python Code Review

Review Python code for Pythonic idioms and type safety.

1. **Type Check**: Are type hints used consistently?
2. **Style Check**: Does the code follow PEP 8 (via Black/Ruff)?
3. **Complexity Check**: Are list comprehensions used appropriately (not too complex)?
4. **Resource Check**: Are context managers (`with`) used for resources?
5. **Test Check**: Are tests written using `pytest` fixtures?

## Feedback Loops

### 1. Type Checking

* **Trigger**: Pre-commit or CI.
* **Action**: Run `mypy` to enforce type safety.
* **Outcome**: Catch type-related bugs early.

### 2. Linting & Formatting

* **Trigger**: On save or Pre-commit.
* **Action**: Run `ruff check --fix` and `ruff format`.
* **Outcome**: Consistent code style and automatic fix of common issues.
