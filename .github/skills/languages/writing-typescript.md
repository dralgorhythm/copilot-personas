---
name: Writing TypeScript
description: Writing type-safe, maintainable TypeScript code with modern language features, strict typing, and integration with popular frameworks.
---

# Writing TypeScript

## Workflows

### 1. Scaffold TypeScript Node Project

Creates a TypeScript Node.js project with modern tooling.

```bash
#!/bin/bash
# create-ts-node-project.sh
# Usage: ./create-ts-node-project.sh <project-name>

PROJECT_NAME=$1

if [ -z "$PROJECT_NAME" ]; then
  echo "Usage: $0 <project-name>"
  exit 1
fi

mkdir -p "$PROJECT_NAME/src"
cd "$PROJECT_NAME"

# Initialize npm project
npm init -y

# Install TypeScript and tools
npm install -D typescript @types/node tsx nodemon
npm install -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
npm install -D prettier eslint-config-prettier

# Create tsconfig.json
cat <<EOF > tsconfig.json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist"]
}
EOF

# Create initial source file
cat <<EOF > src/index.ts
function main(): void {
  console.log('Hello from TypeScript!');
}

main();
EOF

# Update package.json scripts
npm pkg set scripts.dev="tsx watch src/index.ts"
npm pkg set scripts.build="tsc"
npm pkg set scripts.start="node dist/index.js"
npm pkg set scripts.lint="eslint src/**/*.ts"
npm pkg set scripts.format="prettier --write src/**/*.ts"

echo "TypeScript Node.js project created: $PROJECT_NAME"
```

## Feedback Loops

### 1. Type Checking

* **Trigger**: On save or Pre-commit.
* **Action**: Run `tsc --noEmit`.
* **Outcome**: Catch type errors early.

### 2. Linting

* **Trigger**: On save or Pre-commit.
* **Action**: Run `eslint src/**/*.ts`.
* **Outcome**: Enforce code quality and best practices.

### 3. Formatting

* **Trigger**: On save.
* **Action**: Run `prettier --write src/**/*.ts`.
* **Outcome**: Consistent code style.
