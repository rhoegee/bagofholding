# Packcheck — Strategy & Rollout
### Last updated: June 2026

---

## The Platform

Packcheck is a free, browser-based gear planning platform. No logins, accounts or paywalls required. It works offline, saves locally, and loads fast. It should feel like a well-made tool, not a web app.

The Philmont Edition is the proof of concept. Future editions follow the same model — same engine, tailored defaults and itinerary system for each destination. The target audience is not the ultralight obsessive. It's the regular person — the novice camper, the family heading out for the first time, the scout troop advisor who needs to get eight people ready for a 12-day trek. A scout handbook for non-scouts.

---

## Current State — June 2026

| Property | Status |
|---|---|
| `philmont.packcheck.app` | Live, open beta — all 48 2026 itineraries |
| `packcheck.app` | DNS live, splash served from bagofholding — `rhoegee/packcheck.app` repo not yet created |
| `rhoegee/packcheck.app` repo | Not yet created — splash served from bagofholding |
| Google Search Console | Not yet submitted |
| OG images | Live and correctly referenced on both URLs |
| SEO tags | Implemented on both URLs |
| Email list | Removed from current build — revisit post-trek |
| User community | None yet — distribution just beginning |

---

## Goals — Summer 2026

**Primary: Drive awareness and first users to `philmont.packcheck.app` during Philmont season (May–August 2026).**

This is a seed season. The goal is not scale — it's signal. Real users, real feedback, and enough organic presence to build on for the 2027 planning season. The app is feature-complete for 2026. Unless a critical bug surfaces or an obvious missing feature emerges, no further development this season.

**Secondary:** Get `packcheck.app` indexed and begin building SEO authority before the season ends.

**Not goals this summer:** Monetization, user accounts, backend, additional editions, email list.

---

## Audience

**Primary — right now:** Philmont advisors and scout crew leaders preparing for a 2026 trek. They are researching gear, weight targets, and itinerary details right now. They share resources actively with each other and with their crews.

**Secondary — right now:** Scouts and parents on those same crews. Less likely to find the app via search — more likely to receive a direct link from their advisor. The `philmont.packcheck.app` URL is intentionally clean for this reason.

**Future:** Novice backpackers, family campers, overland travelers, day hikers — once additional editions exist. This is the larger long-term audience and the reason `packcheck.app` needs to tell a broader brand story from the start.

---

## Distribution Strategy

### This summer — community seeding

Organic search will not be a major driver in 2026. New domains need 3–6 months to build authority. The window for Philmont season is too short. **Community distribution is the highest-leverage channel right now.**

The credibility advantage: the person behind Packcheck is an active advisor taking a crew to Philmont in June 2026. This is not a marketing post — it's a peer sharing a tool they built and use. That framing matters enormously in these communities.

**Target channels:**
- r/Philmont — most active Philmont-specific Reddit community
- r/scoutingamerica — broader Scouting audience
- Facebook groups — Philmont advisor and crew prep groups (where most advisors actually are)
- Direct advisor-to-crew sharing via the clean `philmont.packcheck.app` URL

**Photography:** Capturing trail photography at Philmont in June 2026 for future content use.

### Fall 2026 / Spring 2027 — content and SEO

The 2027 Philmont planning season begins in earnest around January. Content built this fall will have time to index and rank before that window opens.

**The content gap:** `packcheck.app` currently has no indexable prose. Google has nothing to rank. Fixing this is the #1 SEO priority after the trek.

**Architecture:**
- `packcheck.app` — SEO content hub. Real prose, broader brand story, Philmont content as primary example, links to app.
- `philmont.packcheck.app` — app destination. Clean and direct for community sharing. Not the SEO target page.

**Content approach:** One genuinely useful, authoritative page at `packcheck.app` covering Philmont packing — written from real advisor experience. 800–1200 words of genuine guidance. This outperforms a half-built content site every time. See `PACKCHECK_APP_BRIEF.md` for full content spec.

**Keyword targets (long-tail, low competition):**
- "Philmont packing list 2026 / 2027"
- "Philmont base weight"
- "Philmont crew gear list"
- "Philmont gear checklist"
- "what to bring to Philmont"
- "Philmont itinerary [number] packing"

Avoid competing directly on head terms ("Philmont packing list") until domain authority builds.

**Immediate action (no development required):** Submit both URLs to Google Search Console. Free, 10 minutes, gets the site indexed now.

### Future — monetization and community

**Revenue model (not yet active):**
- Affiliate gear links — integrated into app recommendations, not intrusive
- Brand partnerships
- Produced video content (trail footage from Philmont trek and future trips)
- No ads, no paywall, no freemium

**Community:**
- Reddit and Facebook groups serve the community need for now
- Discord — revisit once a real user base exists (hundreds of active users minimum)
- Email list — revisit fall 2026; Mailchimp was the chosen platform

---

## SEO Implementation Status

**Implemented ✅**
- Meta descriptions and canonical tags on both URLs
- Open Graph and Twitter Card tags on both URLs
- JSON-LD structured data (WebSite on splash, WebApplication on Philmont app)
- robots.txt and sitemap.xml
- Self-hosted fonts (no Google Fonts CDN dependency)
- OG images live and correctly referenced

**Pending:**
- Google Search Console submission — do this now
- `packcheck.app` content page — primary SEO work, see `PACKCHECK_APP_BRIEF.md`
- `rhoegee/packcheck.app` repo creation and proper deployment

---

## Phase Roadmap

**Phase 1 (complete):** Single-crew proof of concept. One hardcoded itinerary. Built in Claude chat. Proved the concept works.

**Phase 2 (current):** Public beta. All 48 Philmont 2026 itineraries. Full sharing and sync system. Dynamic crew gear. Complete Trailhead v2 design overhaul. Live at `philmont.packcheck.app`.

**Phase 3 (not yet started):**
- `packcheck.app` as full content hub with SEO-optimized pages
- Additional editions: BWCA, JMT, PCT, other high-adventure bases
- Options for non-scout families and individuals
- Backend + user accounts
- Crew number lookup → auto-assign itinerary from Philmont registry
- Monetization layer (affiliate links, brand partnerships)

---

## Open Questions

- ⚠ Parent company name — undecided
- ⚠ Post-trek content creation plan — photography captured at PSR June 2026, production TBD
- ⚠ Community platform (Discord vs. forum vs. nothing) — revisit after trek with usage data
- ⚠ Email list setup — Mailchimp, revisit fall 2026
