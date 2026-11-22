# PartyTracker Roadmap

**Last updated:** 2026-11-22  
**Source:** `Docs/Project Vision.txt`  
**Status:** Proposed

## 1. Product Direction

PartyTracker is a personal live-music memory vault. Users log concerts and festivals with flexible free-text input, identify bands using external music metadata, build a rich personal archive, and control visibility through public/friends/private privacy settings. The web application is the primary product. The Android app is a later companion client that syncs through the API.

The roadmap is ordered by dependency and user value: foundation first, then identity, core logging, profile/history, band enrichment, event detail, social features, moderation/admin tools, enrichment operations, and finally Android.

## 2. Planning Rules

- Build the **web platform first**; start Android only after the web/API is stable.
- Split every stage into smaller releases later; each release should be independently deployable.
- Keep the app functional after every release.
- Use feature flags for incomplete social, admin, media, and enrichment features.
- Put structured logging and notification primitives in place early.
- Keep external APIs behind adapters with mock/fixture support.
- Treat privacy and authorization as cross-cutting requirements, not late additions.
- Prefer incremental schema migrations over big-bang database changes.

## 3. Stage Overview

| Stage | Name | Primary Goal | Status |
|---|---|---|---|
| 1 | Foundation & Platform Architecture | Establish deployable apps, database, logging, and engineering baseline | Not started |
| 2 | Identity, Profiles & Privacy | Add authentication, profiles, sessions, and privacy controls | Not started |
| 3 | Event Logging MVP | Enable standalone and festival concert logging | Not started |
| 4 | Personal Profile & Memory Navigation | Build the six-tab personal archive | Not started |
| 5 | Band Identification & Relational Metadata | Enrich bands with MBID-backed metadata and filters | Not started |
| 6 | Concert Detail, Media & Setlists | Complete the individual event experience | Not started |
| 7 | Social Graph & Messaging | Add follows, friends, feeds, and DMs | Not started |
| 8 | Moderation, Admin & Support Access | Add block/suspension engine and admin controls | Not started |
| 9 | Enrichment, Notifications & Web Launch Polish | Complete enrichment pipeline, notifications, and release readiness | Not started |
| 10 | Android Companion & Ecosystem Hardening | Deliver the Android app and final platform hardening | Not started |

## 4. Detailed Stages

### Stage 1 — Foundation & Platform Architecture

**Objective:** Create the technical foundation before feature development.

**Includes:**
- Monorepo structure for web app, API server, shared types, and future Android contracts.
- SvelteKit + Cloudflare Workers setup.
- Fastify API skeleton for Oracle Cloud deployment.
- Neon PostgreSQL schema and migration pipeline.
- Environment and secrets management.
- CI pipeline, linting, formatting, and automated tests.
- Structured logging with levels, tags, filters, and request correlation.
- Notification/event primitives for future user alerts.
- Deployment skeletons for web, API, and database migrations.

**Likely release slices:**
1. Repository scaffold and tooling.
2. Web app deployment skeleton.
3. API deployment skeleton.
4. Database migration pipeline.
5. Logging and notification primitives.

**Exit criteria:** A minimal web app and API deploy successfully, logs are structured and filterable, and the notification abstraction exists for later use.

---

### Stage 2 — Identity, Profiles & Privacy

**Objective:** Establish secure account access and user profile foundations.

**Includes:**
- Google and Facebook authentication.
- Magic-link/passwordless email authentication.
- Cloudflare Turnstile registration protection.
- Canonical email normalization.
- User profile creation and basic profile fields.
- Session management and account settings.
- Default privacy preferences.
- Authorization model for public/friends/private content.

**Likely release slices:**
1. Auth provider configuration.
2. Registration and login flow.
3. Email canonicalization and Turnstile.
4. Profile shell and account settings.
5. Privacy defaults and authorization helpers.

**Exit criteria:** Users can register, log in, manage sessions, and have a persistent profile with privacy settings.

---

### Stage 3 — Event Logging MVP

**Objective:** Deliver the core product loop: logging live music memories.

**Includes:**
- Concert and festival data model.
- Required fields: date, band names, and venue where applicable.
- Optional fields: city/country, rating, and notes.
- Free-text artist/venue/location input.
- Multi-band support with headliner flags.
- Public/friends/private visibility per event.
- Festival parent events with child show logs.
- Festival location inheritance.
- Multi-day date sequence selection.
- Basic local autocomplete/suggestions.

**Likely release slices:**
1. Concert schema and API.
2. Standalone concert logging UI.
3. Festival parent/child model.
4. Multi-band and headliner support.
5. Privacy, validation, and edit/delete flows.

**Exit criteria:** A user can create, edit, delete, and list standalone concerts and multi-day festival logs.

---

### Stage 4 — Personal Profile & Memory Navigation

**Objective:** Turn logged events into a useful personal archive.

**Includes:**
- Profile page shell.
- Overview tab with totals, charts, top headliners, and recent activity.
- Concerts tab with search, sorting, festival cards, ratings, and privacy-aware visibility.
- Bands tab with identified/unidentified states and times-seen counts.
- Venues tab grouped by city/country.
- Locations tab grouped by country/city.
- Years tab grouped chronologically.
- Privacy filtering across all profile views.

**Likely release slices:**
1. Profile shell and navigation.
2. Concerts tab.
3. Bands tab.
4. Venues and Locations tabs.
5. Years tab and Overview analytics.

**Exit criteria:** The six profile tabs render real user data and correctly respect public/friends/private visibility.

---

### Stage 5 — Band Identification & Relational Metadata

**Objective:** Enrich free-text bands with verified music metadata.

**Includes:**
- Unidentified vs. identified band states.
- Identify Band flow with search modal.
- MusicBrainz/Setlist.fm/local candidate search.
- Live preview card before confirmation.
- MBID binding, cancellation, and re-identification.
- Name-collision handling through unique MBIDs.
- Band metadata: logo, country, active years, genres, members, and links.
- Relational filters for country, genre, activity status, and members.

**Likely release slices:**
1. Band identification data model.
2. Search and preview modal.
3. MBID confirmation and re-identification.
4. Metadata display and member/genre/country filters.
5. Name-collision and correction flows.

**Exit criteria:** Users can identify, correct, and re-identify bands, and metadata-driven filters work across their personal archive.

---

### Stage 6 — Concert Detail, Media & Setlists

**Objective:** Complete the individual event experience.

**Includes:**
- Concert/festival detail page.
- Full event lineup section.
- Personal “Bands Seen” tracking.
- Concert details sidebar.
- Genres Seen tag cloud.
- Personal journal, rating, favorite toggle, and notes.
- Photo/media gallery.
- Client-side image compression.
- Per-user media quotas.
- Cloudflare R2 storage with optional Cloudinary/ImageKit abstraction.
- Setlist.fm integration for identified bands.
- Community attendance feed for the same event.

**Likely release slices:**
1. Concert detail page shell.
2. Bands Seen and Genres Seen.
3. Personal journal and ratings.
4. Media upload pipeline and gallery.
5. Setlists and community attendance.

**Exit criteria:** A concert detail page supports lineup tracking, personal notes, media uploads, genres, setlists, and attendance visibility.

---

### Stage 7 — Social Graph & Messaging

**Objective:** Add the two-tier social model and private communication.

**Includes:**
- One-way follow system.
- Mutual friend requests and acceptance.
- Friend feed behavior with optional unfollow.
- Privacy-aware activity feeds.
- Direct message threads.
- PM permission modes: anyone, friends only, or nobody.
- Message privacy enforcement.
- Basic user blocking mechanics needed for messaging safety.

**Likely release slices:**
1. Follow system.
2. Friend requests and mutual friends.
3. Privacy-aware activity feed.
4. DM threads and permissions.
5. Blocking and abuse safeguards.

**Exit criteria:** Users can follow, friend, unfollow, and exchange DMs according to configured privacy rules.

---

### Stage 8 — Moderation, Admin & Support Access

**Objective:** Protect the community and give administrators operational control.

**Includes:**
- Silent individual blocks.
- Net active block calculation.
- Silent PM suspension at 25 net blocks.
- Friend exception rule for suspended users.
- Admin analytics dashboard.
- Flagged-account moderation queue.
- Manual ban/unban/clear-flag controls.
- Default system block preventing unsolicited admin DMs.
- TTL-based admin appeal/support access.
- Automatic re-lock after TTL expiration.
- Support inbox for unblock/appeal requests.

**Likely release slices:**
1. Block relationship model.
2. Net block calculation and silent suspension.
3. Admin metrics dashboard.
4. Moderation queue and overrides.
5. TTL support access and support inbox.

**Exit criteria:** The block/suspension engine works silently as specified, and admins can review flags, override states, and grant temporary support access.

---

### Stage 9 — Enrichment, Notifications & Web Launch Polish

**Objective:** Complete backend intelligence, operational visibility, and web release readiness.

**Includes:**
- Daily band enrichment pipeline.
- MusicBrainz metadata refresh.
- Setlist.fm quota-aware scheduling.
- Nightly utilization window and reserved user-request budget.
- Periodic refresh ordering by `last_enriched_at` and `log_count`.
- Inactive-band monthly scan.
- Data Enrichment Management admin page.
- API quota/health dashboards.
- Manual band import workflow.
- Queue controls and recent activity log.
- User notification system.
- App update checker and update notifications.
- PWA/responsive web polish.
- Performance, security, and reliability hardening.

**Likely release slices:**
1. Enrichment queue and workers.
2. MusicBrainz refresh pipeline.
3. Setlist.fm budget scheduler.
4. Data Enrichment Management UI.
5. Notifications and update checker.
6. Web launch hardening and PWA polish.

**Exit criteria:** Enrichment runs within API budgets, admins can manage it, users receive notifications, and the web app is stable enough for release.

---

### Stage 10 — Android Companion & Ecosystem Hardening

**Objective:** Deliver the mobile companion after the web platform is stable.

**Includes:**
- Kotlin Android app.
- Room local database.
- Authentication/session sync.
- Event read synchronization.
- Event write synchronization.
- Conflict handling and offline support.
- Profile and concert browsing.
- API contract hardening for mobile clients.
- Android release build and rollout.

**Likely release slices:**
1. Android project scaffold.
2. Authentication and session handling.
3. Read-only sync for profile/concerts.
4. Offline event creation and sync.
5. Conflict resolution and release hardening.

**Exit criteria:** Android users can authenticate and sync core logging/profile flows with the web platform.

## 5. Critical Path

The main dependency chain is:

**Foundation → Auth → Event Logging → Profile → Band Identification → Concert Detail → Social → Moderation/Admin → Enrichment/Notifications → Android**

Parallelizable work after the foundation:

- Media storage abstraction after event logging exists.
- Notification infrastructure can be built early and populated later.
- Android API contracts should be considered early, but implementation waits for web/API stability.
- External API adapters should be mocked early to avoid blocking feature work.

## 6. Out of Scope

- iOS app.
- Real-time chat.
- Video uploads.
- Multi-language support.
- Data export/import.
- Ticket purchasing/resale.
- Algorithmic recommendations.
- Public forums/comments.
- Monetization.

## 7. Risks and Decisions Needed

- Validate Neon PostgreSQL compatibility with Better Auth early.
- Decide whether all web API calls route through Fastify or whether SvelteKit server routes handle early web-only endpoints.
- Standardize naming: the vision references both “PartyTracker” and “GigVault.”
- Abstract media providers behind one upload interface.
- Design Android sync/conflict rules before mobile implementation.
- Keep Setlist.fm usage quota-aware from the first integration.
