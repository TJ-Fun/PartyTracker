# Stage 1 — Foundation & Platform Architecture Tracker

**Last updated:** 2026-11-22  
**Stage:** 1 — Foundation & Platform Architecture  
**Release plan:** `Docs/stage-1-release-plan.md`  
**Parent tracker:** `Docs/roadmap-tracker.md`

## 1. How to Use This Tracker

Track release-level progress for Stage 1 here. Task-level breakdowns are intentionally not planned yet; add tasks when a release starts.

### Status values

- **Not started** — no implementation work has begun.
- **Planned** — scope is understood but work has not started.
- **In progress** — active implementation is underway.
- **Blocked** — work cannot continue without a decision, dependency, or external input.
- **In review** — implementation is complete and awaiting validation.
- **Complete** — accepted and verified.
- **Deferred** — intentionally postponed.

### Update rules

1. Update the release status table when a release starts, blocks, or completes.
2. Add task rows only when a release begins execution.
3. Add a progress log entry for meaningful updates.
4. Record blockers and decisions in their dedicated sections.
5. Keep entries short and factual.

## 2. Current Status Snapshot

| Field | Value |
|---|---|
| Stage status | Planned |
| Active release | 1.1 — Repository Scaffold & Tooling Baseline |
| Current focus | Release 1.1 implementation plan generated; awaiting execution approval |
| Blockers | None |
| Next action | Review `ToDo/20261122_185701_plan_stage-1-release-1.1-repository-scaffold.md` and issue Go |

## 3. Release Status

| Release | Name | Status | Owner | Started | Completed | Notes |
|---|---|---|---|---|---|---|
| 1.1 | Repository Scaffold & Tooling Baseline | Planned | Unassigned | — | — | Plan: `ToDo/20261122_185701_plan_stage-1-release-1.1-repository-scaffold.md` |
| 1.2 | Configuration & Secrets Management | Not started | Unassigned | — | — | Depends on 1.1 |
| 1.3 | Web App Foundation | Not started | Unassigned | — | — | Depends on 1.1, 1.2 |
| 1.4 | API Server Foundation | Not started | Unassigned | — | — | Depends on 1.1, 1.2 |
| 1.5 | Shared Contracts & Types | Not started | Unassigned | — | — | Depends on 1.1 |
| 1.6 | Database Foundation | Not started | Unassigned | — | — | Depends on 1.1, 1.2 |
| 1.7 | Migration Pipeline & Seed Data | Not started | Unassigned | — | — | Depends on 1.6 |
| 1.8 | Structured Logging System | Not started | Unassigned | — | — | Depends on 1.3, 1.4 |
| 1.9 | Notification & Event Primitives | Not started | Unassigned | — | — | Depends on 1.5, 1.6 |
| 1.10 | CI/CD Pipeline | Not started | Unassigned | — | — | Depends on 1.1, 1.2 |
| 1.11 | Web Deployment Pipeline | Not started | Unassigned | — | — | Depends on 1.3, 1.2, 1.10 |
| 1.12 | API Deployment Pipeline | Not started | Unassigned | — | — | Depends on 1.4, 1.2, 1.10 |
| 1.13 | Observability & Health Checks | Not started | Unassigned | — | — | Depends on 1.8, 1.11, 1.12 |
| 1.14 | Stage 1 Hardening & Documentation | Not started | Unassigned | — | — | Depends on all previous |

## 4. Task Tracking

Tasks are not planned yet. When a release starts, add a task table here using this format:

| Task | Status | Owner | Started | Completed | Notes |
|---|---|---|---|---|---|
| TBD | Not started | Unassigned | — | — | Add tasks when release execution begins |

## 5. Stage Gate Checklist

- [ ] All planned releases are complete or explicitly deferred.
- [ ] Required tests pass.
- [ ] Documentation is updated.
- [ ] Privacy and authorization rules are verified where applicable.
- [ ] Logging and notification hooks are in place.
- [ ] Deployment paths are documented.
- [ ] Known limitations are recorded.

## 6. Blockers and Risks

| Item | Type | Impact | Status | Owner | Notes |
|---|---|---|---|---|---|
| Neon PostgreSQL + Better Auth compatibility | Risk | High | Open | Unassigned | Validate during Stage 1/2 |
| Cloudflare Workers + Fastify API boundaries | Risk | Medium | Open | Unassigned | Confirm before feature endpoints |
| Oracle Cloud deployment access/process | Risk | Medium | Open | Unassigned | Needed for Release 1.12 |
| Cloudflare/Neon credentials and environments | Risk | Medium | Open | Unassigned | Needed for deployment releases |
| Migration tool/ORM choice | Decision | Medium | Open | Unassigned | Decide during Release 1.6/1.7 |

## 7. Decisions Log

| Date | Decision | Context | Owner |
|---|---|---|---|
| 2026-11-22 | Stage 1 split into 14 releases | Foundation release planning | Unassigned |
| 2026-11-22 | Task breakdown deferred until release execution | Keep tracker lightweight | Unassigned |

## 8. Progress Log

| Date | Release | Update | Status | Next Action |
|---|---|---|---|---|
| 2026-11-22 | Stage 1 | Created release plan and dedicated tracker | Complete | Begin Release 1.1 |
| 2026-11-22 | 1.1 | Generated implementation plan for Repository Scaffold & Tooling Baseline | Planned | Review plan and issue Go |
