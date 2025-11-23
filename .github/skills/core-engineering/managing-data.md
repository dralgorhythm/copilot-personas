---
name: managing-data
description: Designing and implementing data strategies using Serverless PostgreSQL (Neon), Object Storage (R2), and Edge SQL (D1) following the Graduated Hosting Strategy.
---

# Managing Data

## Workflows

### 1. Provision Neon Database (Serverless Postgres)

Sets up a Neon project with branching enabled.

```bash
# Pseudo-command for Neon CLI
neon project create --name my-app-db --region us-east-1
# Enable branching for PRs
neon branch create --name dev/feature-1
```

### 2. Configure Cloudflare R2 (Object Storage)

Sets up an R2 bucket for zero-egress object storage.

```bash
# Using Wrangler
npx wrangler r2 bucket create my-app-assets
```

### 3. Configure Cloudflare D1 (Edge SQL)

Sets up a D1 database for edge-local data.

```bash
# Using Wrangler
npx wrangler d1 create my-app-edge-db
```

## Feedback Loops

### 1. Database Migrations

* **Trigger**: Pre-deploy.
* **Action**: Run migrations (e.g., `drizzle-kit push` or `prisma migrate`).
* **Outcome**: Schema is up-to-date without downtime.

### 2. Branch Verification

* **Trigger**: Pull Request.
* **Action**: Create Neon branch -> Run Tests against branch -> Delete branch.
* **Outcome**: Isolated testing environment for every PR.

## Reference Implementation

### Connecting to Neon with Connection Pooling

```typescript
// db.ts
import { neonConfig, Pool } from '@neondatabase/serverless';
import ws from 'ws';

// Required for serverless environments
neonConfig.webSocketConstructor = ws;

const pool = new Pool({ connectionString: process.env.DATABASE_URL });

export const query = async (text: string, params: any[]) => {
  return pool.query(text, params);
};
```

### Using Cloudflare R2 with S3 SDK

```typescript
import { S3Client, PutObjectCommand } from "@aws-sdk/client-s3";

const R2 = new S3Client({
  region: "auto",
  endpoint: `https://${process.env.ACCOUNT_ID}.r2.cloudflarestorage.com`,
  credentials: {
    accessKeyId: process.env.R2_ACCESS_KEY_ID,
    secretAccessKey: process.env.R2_SECRET_ACCESS_KEY,
  },
});

await R2.send(new PutObjectCommand({
  Bucket: "my-bucket",
  Key: "hello.txt",
  Body: "Hello R2!",
}));
```

## Resources
- [Database Instructions](../../instructions/database.instructions.md)

- [Neon Documentation](https://neon.tech/docs)
- [Cloudflare R2 Docs](https://developers.cloudflare.com/r2/)
