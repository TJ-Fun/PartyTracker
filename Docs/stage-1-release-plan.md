# Stage 1 — Foundation & Platform Architecture Release Plan

**Last updated:** 2026-11-22  
**Stage:** 1 — Foundation & Platform Architecture  
**Status:** Planned  
**Parent roadmap:** `Docs/Roadmap.md`  
**Parent tracker:** `Docs/roadmap-tracker.md`  
**Dedicated tracker:** `Docs/stage-1-tracker.md`

## 1. Purpose

This release plan splits Stage 1 into independently deliverable releases. It defines release scope, dependencies, and exit criteria only. Task-level breakdowns will be created when each release starts.

## 2. Planning Rules

- Keep the application deployable after every release.
- Prefer small, reversible changes.
- Use feature flags for incomplete capabilities.
- Establish logging and notification primitives before feature work depends on them.
- Keep external service credentials out of source control.
- Validate Neon PostgreSQL + Better Auth compatibility early.
- Confirm Cloudflare Workers + Fastify API boundaries before building feature endpoints.

## 3. Release Overview

| Release | Name | Objective | Depends On | Status |
|---|---|---|---|---|
| 1.1 | Repository Scaffold & Tooling Baseline | Create a clean monorepo with consistent tooling | — | Not started |
| 1.2 | Configuration & Secrets Management | Establish environment config and secrets handling | 1.1 | Not started |
| 1.3 | Web App Foundation | Create the SvelteKit + Cloudflare Workers app shell | 1.1, 1.2 | Not started |
| 1.4 | API Server Foundation | Create the Fastify API shell with health checks | 1.1, 1.2 | Not started |
| 1.5 | Shared Contracts & Types | Define shared API/event/error contracts | 1.1 | Not started |
| 1.6 | Database Foundation | Connect to Neon PostgreSQL and establish schema baseline | 1.1, 1.2 | Not started |
| 1.7 | Migration Pipeline & Seed Data | Make database migrations repeatable and safe | 1.6 | Not started |
| 1.8 | Structured Logging System | Add leveled, tagged, filterable logging | 1.3, 1.4 | Not started |
| 1.9 | Notification & Event Primitives | Add internal event/notification abstractions | 1.5, 1.6 | Not started |
| 1.10 | CI/CD Pipeline | Automate lint, typecheck, tests, and builds | 1.1, 1.2 | Not started |
| 1.11 | Web Deployment Pipeline | Deploy the web app to Cloudflare Workers | 1.3, 1.2, 1.10 | Not started |
| 1.12 | API Deployment Pipeline | Deploy the API to Oracle Cloud | 1.4, 1.2, 1.10 | Not started |
| 1.13 | Observability & Health Checks | Add readiness, logging, and operational visibility | 1.8, 1.11, 1.12 | Not started |
| 1.14 | Stage 1 Hardening & Documentation | Complete security, reliability, and docs | All previous | Not started |

## 4. Parallelization Notes

After Release 1.1, several tracks can run in parallel:

- Web foundation: 1.3
- API foundation: 1.4
- Shared contracts: 1.5
- Database foundation: 1.6
- Configuration/secrets: 1.2 should finish before deployment work.

Logging should follow web/API foundations. Notification primitives should follow shared contracts and database foundation. Deployment pipelines should follow CI.

## 5. Detailed Releases

### Release 1.1 — Repository Scaffold & Tooling Baseline

**Objective:** Establish a clean, consistent development baseline.

**Scope:**
- Monorepo structure for web app, API server, shared packages, and future Android contracts.
- Package manager and workspace configuration.
- TypeScript configuration.
- Linting and formatting tools.
- `.gitignore` and environment file templates.
- README/CONTRIBUTING documentation.
- Basic test runner setup.

**Dependencies:** None.

**Exit criteria:**
- A fresh clone can install dependencies.
- Lint, format, typecheck, and test commands run successfully.
- Web, API, and shared package boundaries are clear.

**Status:** Not started

---

### Release 1.2 — Configuration & Secrets Management

**Objective:** Centralize environment configuration and secrets handling.

**Scope:**
- Environment variable schema/validation.
- Local, staging, and production config separation.
- Secrets handling guidance for Cloudflare, Neon, Oracle, and external APIs.
- Safe defaults and fail-fast validation.
- Configuration documentation.

**Dependencies:** 1.1

**Exit criteria:**
- Apps fail fast on missing required configuration.
- No secrets are committed to source control.
- Environment templates are documented.

**Status:** Not started

---

### Release 1.3 — Web App Foundation

**Objective:** Create the SvelteKit web application shell.

**Scope:**
- SvelteKit project setup.
- Cloudflare Workers adapter configuration.
- Base layout and routing shell.
- Static asset handling.
- Local development workflow.
- Basic health/status page.

**Dependencies:** 1.1, 1.2

**Exit criteria:**
- The web app runs locally.
- The app builds for Cloudflare Workers.
- A minimal status page is reachable.

**Status:** Not started

---

### Release 1.4 — API Server Foundation

**Objective:** Create the Fastify API shell.

**Scope:**
- Fastify project setup.
- Health/readiness endpoint.
- Graceful shutdown handling.
- Request ID middleware.
- Basic error handling.
- Local development workflow.

**Dependencies:** 1.1, 1.2

**Exit criteria:**
- The API runs locally.
- `/health` returns a healthy status.
- The API handles shutdown cleanly.

**Status:** Not started

---

### Release 1.5 — Shared Contracts & Types

**Objective:** Define shared API, event, and error contracts.

**Scope:**
- Shared TypeScript types package.
- API request/response contracts.
- Standard error shape.
- Internal event/notification type definitions.
- Versioning strategy for contracts.

**Dependencies:** 1.1

**Exit criteria:**
- Web and API can import shared contracts.
- API errors use a consistent shape.
- Event/notification types are defined for later use.

**Status:** Not started

---

### Release 1.6 — Database Foundation

**Objective:** Connect the platform to Neon PostgreSQL.

**Scope:**
- PostgreSQL client/ORM setup.
- Neon connection configuration.
- Initial schema baseline.
- Migration table infrastructure.
- Basic database health check.
- Connection pooling guidance.

**Dependencies:** 1.1, 1.2

**Exit criteria:**
- The API can connect to Neon PostgreSQL.
- Database health is verifiable.
- Initial schema/migration infrastructure exists.

**Status:** Not started

---

### Release 1.7 — Migration Pipeline & Seed Data

**Objective:** Make schema changes repeatable and safe.

**Scope:**
- Migration commands for local/staging/production.
- Migration validation in CI.
- Seed data strategy.
- Rollback or forward-fix guidance.
- Migration documentation.

**Dependencies:** 1.6

**Exit criteria:**
- A fresh database can be migrated from scratch.
- Migrations are repeatable and validated.
- Seed data can be loaded safely.

**Status:** Not started

---

### Release 1.8 — Structured Logging System

**Objective:** Add consistent structured logging across web and API.

**Scope:**
- Logger abstraction.
- Log levels: debug, info, warn, error.
- Tags/categories for features.
- Request correlation IDs.
- Sensitive data redaction.
- Log filtering guidance.

**Dependencies:** 1.3, 1.4

**Exit criteria:**
- Web and API emit structured logs.
- Logs include level, timestamp, service, request ID, and tags.
- Sensitive values are redacted.

**Status:** Not started

---

### Release 1.9 — Notification & Event Primitives

**Objective:** Create internal primitives for future notifications and events.

**Scope:**
- Internal event bus or dispatcher interface.
- Notification domain types.
- Outbox/persistence strategy.
- Delivery adapter interface.
- Test notification flow.

**Dependencies:** 1.5, 1.6

**Exit criteria:**
- The system can emit and consume internal events.
- Notification records can be persisted.
- Delivery is abstracted for future providers.

**Status:** Not started

---

### Release 1.10 — CI/CD Pipeline

**Objective:** Automate quality checks and build validation.

**Scope:**
- GitHub Actions workflows.
- Install, lint, format, typecheck, and test jobs.
- Build jobs for web and API.
- Migration validation job.
- Branch protection guidance.

**Dependencies:** 1.1, 1.2

**Exit criteria:**
- Pull requests run automated checks.
- Builds fail on lint/type/test errors.
- Migration validation is part of CI.

**Status:** Not started

---

### Release 1.11 — Web Deployment Pipeline

**Objective:** Deploy the web app to Cloudflare Workers.

**Scope:**
- Wrangler deployment configuration.
- Environment-specific deploys.
- Static asset deployment.
- Preview/staging deployment path.
- Rollback guidance.

**Dependencies:** 1.3, 1.2, 1.10

**Exit criteria:**
- The web app deploys to Cloudflare Workers.
- Staging/preview deployment works.
- Rollback steps are documented.

**Status:** Not started

---

### Release 1.12 — API Deployment Pipeline

**Objective:** Deploy the Fastify API to Oracle Cloud.

**Scope:**
- Oracle Cloud deployment process.
- Process manager or container strategy.
- Environment configuration on server.
- Health check verification.
- Rollback guidance.

**Dependencies:** 1.4, 1.2, 1.10

**Exit criteria:**
- The API deploys to Oracle Cloud.
- Health checks pass after deployment.
- Rollback steps are documented.

**Status:** Not started

---

### Release 1.13 — Observability & Health Checks

**Objective:** Add operational visibility across deployed services.

**Scope:**
- Liveness and readiness endpoints.
- Structured log aggregation guidance.
- Error tracking hooks.
- Uptime/health monitoring.
- Alerting thresholds.

**Dependencies:** 1.8, 1.11, 1.12

**Exit criteria:**
- Services expose health/readiness endpoints.
- Logs are collectable and filterable.
- Basic alerts exist for critical failures.

**Status:** Not started

---

### Release 1.14 — Stage 1 Hardening & Documentation

**Objective:** Complete Stage 1 reliability, security, and documentation.

**Scope:**
- Security headers and dependency audit.
- Backup/restore guidance for Neon.
- Runbooks for deployment and rollback.
- Architecture documentation.
- Stage gate checklist verification.
- Known limitations documentation.

**Dependencies:** All previous releases.

**Exit criteria:**
- Stage 1 gate checklist is complete.
- Documentation is current.
- Known risks and limitations are recorded.

**Status:** Not started

## 6. Stage Exit Criteria

Stage 1 is complete when:

- Web and API deploy successfully to their target environments.
- Database migrations are repeatable and validated.
- Structured logging and notification primitives exist.
- CI/CD checks are enforced.
- Health checks and basic observability are in place.
- Stage 1 documentation and runbooks are complete.
