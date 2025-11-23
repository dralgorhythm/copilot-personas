# Database Engineering Instructions
> **Apply To**: `**/*.sql`, `**/*.prisma`, `migrations/*`

Guidelines for database design, management, and optimization following modern engineering practices.

## <coding_standards>
1.  **Primary Keys**: MUST use UUIDv7 (time-sortable) for primary keys in distributed systems to ensure index locality and prevent fragmentation.
2.  **Foreign Keys**: MUST enforce referential integrity at the database level using Foreign Key constraints.
3.  **Migrations**: Database schema changes MUST be version-controlled and applied via automated migration tools (e.g., Atlas, Prisma Migrate, sqlx-cli).
4.  **Connection Pooling**: Serverless applications (Workers, Lambdas) MUST use an external connection pooler (Hyperdrive, Supavisor, PgBouncer) to prevent connection exhaustion.
5.  **Zero Egress**: Prefer object storage providers with zero egress fees (e.g., Cloudflare R2) for high-bandwidth public assets.
</coding_standards>

## <best_practices>
1.  **Database Branching**: Use copy-on-write database branching (Neon) for every Pull Request to provide isolated, production-like preview environments.
2.  **Edge vs. Core**: Use Cloudflare D1/KV for edge-local, read-heavy, or per-tenant data. Use centralized Postgres (Neon) for core relational data requiring strict ACID guarantees across complex models.
3.  **Local Fidelity**: Use Docker-based emulators (MinIO for S3, Neon Local for Postgres) to mirror production infrastructure locally.
4.  **Vector Search**: Use `pgvector` within the primary Postgres instance for hybrid search (relational + semantic) rather than a separate vector database, unless latency requirements dictate edge-only processing (Vectorize).
</best_practices>

## <testing_protocols>
*   **Migration Testing**: Test migrations on a branched database before applying to production.
</testing_protocols>

## <tooling>
*   **Neon**: Serverless Postgres with scale-to-zero and branching. Primary relational store.
*   **Cloudflare R2**: S3-compatible object storage with zero egress fees.
*   **Cloudflare Hyperdrive**: Global connection pooler for accessing centralized databases from the edge.
*   **Supavisor**: Scalable connection pooler for Supabase/Postgres.
*   **MinIO**: Local S3 emulator.
*   **Atlas**: Declarative database schema management and migration tool.
</tooling>

## <additional_section>
### Driver Standards
*   **Rust**: `sqlx` (Async, Compile-time checked queries). Alternative: `diesel` (only if sync/ORM is strictly required).
*   **Go**: `pgx` (High performance, native pooling). Tune `max_conns` to be less than the upstream pooler limit.
*   **Python**: `psqlpy` (Rust-backed, high perf) or `SQLAlchemy` (Async 2.0+). Avoid sync drivers like `psycopg2` in async contexts.

### Migration Patterns
#### Zero-Downtime
Schema changes must be backward compatible.
1.  Add column (nullable).
2.  Deploy code writing to both.
3.  Backfill data.
4.  Add constraint (not null).
5.  Remove old column.

#### Branching Workflow
1.  PR created -> Trigger CI.
2.  CI calls Neon API to create branch from `main`.
3.  Run migrations on branch.
4.  Run tests against branch.
5.  Merge PR -> Delete branch.
</additional_section>

