# PartyTracker Roadmap Tracker

**Last updated:** 2026-11-22  
**Source roadmap:** `Docs/Roadmap.md`  
**Source vision:** `Docs/Project Vision.txt`

## 1. How to Use This Tracker

Update this file whenever a stage changes state. Use dedicated stage tracker files for release-level progress.

### Status values

- **Not started** — no implementation work has begun.
- **Planned** — scope is understood but work has not started.
- **In progress** — active implementation is underway.
- **Blocked** — work cannot continue without a decision, dependency, or external input.
- **In review** — implementation is complete and awaiting validation.
- **Complete** — accepted and verified.
- **Deferred** — intentionally postponed.

### Update rules

1. Update the stage status table when a stage starts, blocks, or completes.
2. Track release-level progress in dedicated stage tracker files, such as `Docs/stage-1-tracker.md`.
3. Add a progress log entry for meaningful updates.
4. Record blockers and decisions in their dedicated sections.
5. Keep entries short and factual.

## 2. Current Status Snapshot

| Field | Value |
|---|---|
| Overall status | Not started |
| Current stage | Stage 1 — Foundation & Platform Architecture |
| Current focus | Stage 1 Release 1.1 plan generated; implementation has not started |
| Active release | 1.1 — Repository Scaffold & Tooling Baseline (planned) |
| Blockers | None |
| Next action | Review Release 1.1 plan and issue Go |

## 3. Stage Status

| Stage | Name | Status | Owner | Started | Completed | Notes |
|---|---|---|---|---|---|---|
| 1 | Foundation & Platform Architecture | Planned | Unassigned | — | — | Release plan: `Docs/stage-1-release-plan.md`; tracker: `Docs/stage-1-tracker.md`; Release 1.1 plan: `ToDo/20261122_185701_plan_stage-1-release-1.1-repository-scaffold.md` |
| 2 | Identity, Profiles & Privacy | Not started | Unassigned | — | — | Auth providers, profiles, sessions, privacy controls |
| 3 | Event Logging MVP | Not started | Unassigned | — | — | Standalone/festival logging, bands, venue, rating, notes, privacy |
| 4 | Personal Profile & Memory Navigation | Not started | Unassigned | — | — | Six profile tabs and privacy-aware archive views |
| 5 | Band Identification & Relational Metadata | Not started | Unassigned | — | — | MBID identification, metadata, filters, re-identification |
| 6 | Concert Detail, Media & Setlists | Not started | Unassigned | — | — | Detail page, bands seen, genres, media, setlists, attendance |
| 7 | Social Graph & Messaging | Not started | Unassigned | — | — | Follow/friend model, feeds, DMs, privacy modes |
| 8 | Moderation, Admin & Support Access | Not started | Unassigned | — | — | Silent suspension, admin dashboard, TTL support access |
| 9 | Enrichment, Notifications & Web Launch Polish | Not started | Unassigned | — | — | Enrichment pipeline, notifications, update checker, web hardening |
| 10 | Android Companion & Ecosystem Hardening | Not started | Unassigned | — | — | Kotlin/Room app, auth, sync, offline support, release build |

## 4. Stage Trackers

| Stage | Release Plan | Tracker | Status |
|---|---|---|---|
| 1 | `Docs/stage-1-release-plan.md` | `Docs/stage-1-tracker.md` | Planned |
| 2 | TBD | TBD | Not started |
| 3 | TBD | TBD | Not started |
| 4 | TBD | TBD | Not started |
| 5 | TBD | TBD | Not started |
| 6 | TBD | TBD | Not started |
| 7 | TBD | TBD | Not started |
| 8 | TBD | TBD | Not started |
| 9 | TBD | TBD | Not started |
| 10 | TBD | TBD | Not started |

## 5. Stage Gate Checklist

Use this checklist before marking a stage complete.

- [ ] All planned releases for the stage are complete or explicitly deferred.
- [ ] Required tests pass.
- [ ] Documentation is updated.
- [ ] Privacy and authorization rules are verified.
- [ ] Logging and notification hooks are in place where applicable.
- [ ] Admin or operational controls are verified where applicable.
- [ ] Deployment path is documented.
- [ ] Known limitations are recorded.

## 6. Blockers and Risks

| Item | Type | Impact | Status | Owner | Notes |
|---|---|---|---|---|---|
| Neon PostgreSQL + Better Auth compatibility | Risk | High | Open | Unassigned | Validate during Stage 1/2 |
| Cloudflare Workers + Fastify split architecture | Risk | Medium | Open | Unassigned | Confirm API boundaries and deployment model |
| Setlist.fm quota limits | Risk | Medium | Open | Unassigned | Requires budget-aware scheduler |
| Media provider quotas | Risk | Medium | Open | Unassigned | Requires abstraction and quota controls |
| Android sync/conflict design | Risk | Medium | Open | Unassigned | Design API contracts before Stage 10 |
| Naming inconsistency: PartyTracker vs GigVault | Decision | Low | Open | Unassigned | Standardize before user-facing copy |

## 7. Decisions Log

| Date | Decision | Context | Owner |
|---|---|---|---|
| 2026-11-22 | Roadmap created with 10 stages | Initial planning based on Project Vision | Unassigned |

## 8. Progress Log

| Date | Stage/Release | Update | Status | Next Action |
|---|---|---|---|---|
| 2026-11-22 | Roadmap | Created `Docs/Roadmap.md` and `Docs/roadmap-tracker.md` | Complete | Split Stage 1 into releases |
| 2026-11-22 | Stage 1 | Created `Docs/stage-1-release-plan.md` and `Docs/stage-1-tracker.md`; replaced global release tracker with stage tracker index | Complete | Begin Stage 1 Release 1 |
| 2026-11-22 | Stage 1 / Release 1.1 | Generated `ToDo/20261122_185701_plan_stage-1-release-1.1-repository-scaffold.md` | Planned | Review plan and issue Go |
