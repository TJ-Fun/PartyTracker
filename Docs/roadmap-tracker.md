# PartyTracker Roadmap Tracker

**Last updated:** 2026-11-22  
**Source roadmap:** `Docs/Roadmap.md`  
**Source vision:** `Docs/Project Vision.txt`

## 1. How to Use This Tracker

Update this file whenever a stage or release changes state.

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
2. Add release rows when a stage is split into releases.
3. Add a progress log entry for meaningful updates.
4. Record blockers and decisions in their dedicated sections.
5. Keep entries short and factual.

## 2. Current Status Snapshot

| Field | Value |
|---|---|
| Overall status | Not started |
| Current stage | Stage 1 — Foundation & Platform Architecture |
| Current focus | Roadmap documentation created; implementation has not started |
| Active release | None |
| Blockers | None |
| Next action | Split Stage 1 into releases and begin repository scaffolding |

## 3. Stage Status

| Stage | Name | Status | Owner | Started | Completed | Notes |
|---|---|---|---|---|---|---|
| 1 | Foundation & Platform Architecture | Not started | Unassigned | — | — | Establish deployable web/API, DB migrations, logging, notifications |
| 2 | Identity, Profiles & Privacy | Not started | Unassigned | — | — | Auth providers, profiles, sessions, privacy controls |
| 3 | Event Logging MVP | Not started | Unassigned | — | — | Standalone/festival logging, bands, venue, rating, notes, privacy |
| 4 | Personal Profile & Memory Navigation | Not started | Unassigned | — | — | Six profile tabs and privacy-aware archive views |
| 5 | Band Identification & Relational Metadata | Not started | Unassigned | — | — | MBID identification, metadata, filters, re-identification |
| 6 | Concert Detail, Media & Setlists | Not started | Unassigned | — | — | Detail page, bands seen, genres, media, setlists, attendance |
| 7 | Social Graph & Messaging | Not started | Unassigned | — | — | Follow/friend model, feeds, DMs, privacy modes |
| 8 | Moderation, Admin & Support Access | Not started | Unassigned | — | — | Silent suspension, admin dashboard, TTL support access |
| 9 | Enrichment, Notifications & Web Launch Polish | Not started | Unassigned | — | — | Enrichment pipeline, notifications, update checker, web hardening |
| 10 | Android Companion & Ecosystem Hardening | Not started | Unassigned | — | — | Kotlin/Room app, auth, sync, offline support, release build |

## 4. Release Tracker

Add one row per release after a stage is split. Use `TBD` until release scope is defined.

| Stage | Release | Scope | Status | Owner | Started | Completed | Notes |
|---|---|---|---|---|---|---|---|
| 1 | TBD | To be split | Not started | Unassigned | — | — | Foundation stage releases not yet defined |
| 2 | TBD | To be split | Not started | Unassigned | — | — | Identity stage releases not yet defined |
| 3 | TBD | To be split | Not started | Unassigned | — | — | Event logging releases not yet defined |
| 4 | TBD | To be split | Not started | Unassigned | — | — | Profile/navigation releases not yet defined |
| 5 | TBD | To be split | Not started | Unassigned | — | — | Band identification releases not yet defined |
| 6 | TBD | To be split | Not started | Unassigned | — | — | Concert detail/media releases not yet defined |
| 7 | TBD | To be split | Not started | Unassigned | — | — | Social/messaging releases not yet defined |
| 8 | TBD | To be split | Not started | Unassigned | — | — | Moderation/admin releases not yet defined |
| 9 | TBD | To be split | Not started | Unassigned | — | — | Enrichment/notifications releases not yet defined |
| 10 | TBD | To be split | Not started | Unassigned | — | — | Android releases not yet defined |

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
