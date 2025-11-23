---
name: manage-database-neon
description: Manage serverless PostgreSQL databases with Neon, including branching and local development.
---

# Manage Database with Neon

## Workflows
<!-- Checklist for complex tasks -->
- [ ] **Prerequisites**: Is the Neon CLI installed?
- [ ] **Project**: Is the Neon project created?
- [ ] **Branching**: Is a branch created for the current feature/environment?
- [ ] **Connection**: Is the connection string retrieved (pooled or direct)?

## Feedback Loops
<!-- Validation steps -->
1. Create branch: `neon branches create`.
2. Get connection string: `neon connection-string`.
3. Connect: `psql <connection-string>`.
4. Run migrations.

## Utility Scripts
<!-- Reference executable scripts -->
- `docker-compose.yml` for Local Neon (simulation):

```yaml
version: '3.8'
services:
  postgres:
    image: postgres:16
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
      POSTGRES_DB: main
```
*(Note: True Neon Local is more complex, this is a standard Postgres fallback for simple cases)*

## Reference Implementation
<!-- Code patterns -->
```bash
# Create a branch for a PR
neon branches create --name pr-123

# Get connection string for the branch
neon connection-string --branch pr-123
```

## Resources
<!-- Links to external docs or local reference files -->
- [Neon Documentation](https://neon.tech/docs/introduction)
