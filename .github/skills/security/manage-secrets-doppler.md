---
name: manage-secrets-doppler
description: Manage application secrets using Doppler as the unified control plane.
---

# Manage Secrets with Doppler

## Workflows
<!-- Checklist for complex tasks -->
- [ ] **Prerequisites**: Is the Doppler CLI installed?
- [ ] **Project**: Is the project configured in Doppler?
- [ ] **Environment**: Are secrets defined for Dev, Staging, and Prod?
- [ ] **Sync**: Are integrations set up (GitHub Actions, Railway, AWS Parameter Store)?

## Feedback Loops
<!-- Validation steps -->
1. Login: `doppler login`.
2. Setup: `doppler setup`.
3. Inject: Run app with `doppler run -- command`.
4. Verify: Check process environment variables.

## Utility Scripts
<!-- Reference executable scripts -->
- `doppler.yaml`: Project configuration (optional, usually local).

```yaml
setup:
  project: my-app
  config: dev
```

## Reference Implementation
<!-- Code patterns -->
```bash
# Run local development server with secrets
doppler run -- pnpm dev

# Run production build with secrets
doppler run -- pnpm start
```

## Resources
<!-- Links to external docs or local reference files -->
- [Doppler Documentation](https://docs.doppler.com/)
- [Security Instructions](../../instructions/security.instructions.md)

