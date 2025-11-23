---
name: deploy-to-cloudflare-pages
description: Deploy a static site or SPA to Cloudflare Pages (Static Tier) for maximum performance.
---

# Deploy to Cloudflare Pages

## Workflows
<!-- Checklist for complex tasks -->
- [ ] **Prerequisites**: Is `wrangler` installed (`pnpm add -D wrangler`)?
- [ ] **Build**: Does the project have a build script producing a static output directory (e.g., `dist`, `out`)?
- [ ] **Project**: Is the Cloudflare Pages project created?

## Feedback Loops
<!-- Validation steps -->
1. Run build: `pnpm build`.
2. Preview locally: `pnpm wrangler pages dev dist`.
3. Deploy: `pnpm wrangler pages deploy dist`.
4. Verify deployment URL.

## Utility Scripts
<!-- Reference executable scripts -->
- `package.json` scripts:

```json
{
  "scripts": {
    "build": "vite build",
    "preview": "wrangler pages dev dist",
    "deploy": "wrangler pages deploy dist"
  }
}
```

## Reference Implementation
<!-- Code patterns -->
```bash
# Direct deployment
npx wrangler pages deploy dist --project-name=my-app
```

## Resources
<!-- Links to external docs or local reference files -->
- [Cloudflare Pages Documentation](https://developers.cloudflare.com/pages/)
- [Cloud Native Instructions](../../instructions/cloud-native.instructions.md)

