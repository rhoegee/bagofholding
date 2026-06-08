# Packcheck — Phase 2 Brief
### Status: Active development · Branch `claude/beautiful-babbage-biA91` · June 2026

---

## What Phase 2 is

Phase 2 transformed the single-crew proof-of-concept from Phase 1 into a public beta platform. The app moved from a single hardcoded itinerary to all 48 Philmont 2026 itineraries, gained a full sharing/sync system, a dynamic crew gear system, and a complete visual and UX overhaul. It is live at `philmont.packcheck.app` and in active use by Philmont crews for the 2026 season.

---

## What was shipped in Phase 2

### Architecture
- Renamed primary file from `Packcheck Planner.html` → `index.html`
- Split itinerary data into `itinerary-data.js` (all 48 itineraries + 10-meal rotation)
- Added `help-content.js` (in-app user guide Q&A)
- Self-hosted fonts in `/fonts/` (Oswald, Zilla Slab, JetBrains Mono) — eliminates Google Fonts CDN dependency for performance
- Deployed via GitHub Actions: push to `claude/beautiful-babbage-biA91` → force-push to `rhoegee/philmont.packcheck.app` main → live in ~30s

### Itinerary system
- All 48 Philmont 2026 itineraries loaded from `itinerary-data.js` (24 twelve-day, 12 nine-day, 12 seven-day)
- Dynamic itinerary selection from profile — enters itinerary number (e.g. `12-10`), loads camp sequence, miles, elevation, difficulty
- Crew number auto-fills arrival date (MMDD format)
- Day-by-day pack weight simulator syncs dry camps, resupply days, staff days from selected itinerary
- Itinerary tab renders full schedule with menus, elevation data, difficulty

### Crew gear system
- Google Sheets CSV fetch on load (falls back to hardcoded defaults silently)
- `crewGearCustomized` flag — once user edits crew gear, sheet no longer overwrites
- Advisor weight override (`crewOverrideOz`) — enter total crew gear weight in lbs, app divides per person
- Tent weight override (`tentOverrideOz`) — separate override for tent weight
- Adult/scout split: tent weight distributed only among scouts; adults carry equal share of everything else
- `profile.role` (scout/leader) — leader carries own tent, excluded from tent weight share
- `resetCrewGear()` — clears customization, re-fetches sheet
- Crew gear share link — Cloudflare Worker short URL + QR code

### Sharing system
- **Personal gear share:** Cloudflare Worker at `packcheck-share.rob-56e.workers.dev` — POST compact JSON, get short `?share=<id>` URL + QR code. Falls back to LZ-String `?g=` URL if Worker unavailable.
- **Crew gear share:** same Worker, `?crew=<id>` param. Prompts recipient to load crew gear list.
- **Save/Load:** JSON file export/import (full state)
- **QR code:** QRious canvas-based, shown in modal

### Mobile
- Two-row nav at ≤1024px
- Gear table hides brand + notes columns at ≤640px
- Long-press (500ms) to edit on mobile
- Move-to-category dropdown hidden on mobile (desktop only)
- Save button added to hamburger menu
- Arrival date input changed from `type="date"` to `type="text"` (M/D/YY) — native date inputs have unoverrideable minimum width on iOS/Chrome
- Number input spinners hidden on edit row (were clipping values)
- Gear table column breakpoint at ≤900px covers both portrait and landscape phones

### Profile modal
- Name, crew number, troop, council, arrival date, itinerary number, trek length, day 0 toggle, role (scout/leader)
- Crew number auto-fills arrival date; itinerary number auto-fills trek length
- Arrival date and trek length fields are side-by-side (not stacked)
- Hint text on crew and itinerary fields explains format and what auto-fills

### UI / design
- Full Trailhead v2 design system (`packcheck-theme.css`) — paper/cream/pine/scout-red/gold palette
- Light + dark theme toggle
- Three gear layout options: Default, Comfort, Cards
- Help (?) modal — content from `help-content.js`, sectioned Q&A
- Print and Excel export

### SEO (added end of Phase 2)
- `index.html`: meta description, canonical, OG tags, Twitter Card, WebApplication JSON-LD
- `splash/index.html`: meta description, canonical, favicon, OG tags, Twitter Card, WebSite JSON-LD
- `robots.txt` at repo root → points to `philmont.packcheck.app/sitemap.xml`
- `sitemap.xml` at repo root → lists `philmont.packcheck.app` only
- See `SEO_Brief.md` for full details

---

## Active deployment

| Property | Value |
|---|---|
| Live URL | `https://philmont.packcheck.app` |
| Source repo | `rhoegee/bagofholding`, branch `claude/beautiful-babbage-biA91` |
| Deploy target | `rhoegee/philmont.packcheck.app`, branch `main` |
| Deploy time | ~30 seconds after push |
| Deploy workflow | `.github/workflows/deploy-philmont.yml` |

**Never push directly to `rhoegee/philmont.packcheck.app`** — it will be overwritten on the next bagofholding push.

---

## Pending / known issues

### packcheck.app splash page
- Lives at `splash/index.html` in bagofholding during development
- Needs its own repo: `rhoegee/packcheck.app` (not yet created)
- When created: add `robots.txt` → `https://packcheck.app/sitemap.xml` and `sitemap.xml` listing `https://packcheck.app/`
- See `SEO_Brief.md` for full deployment checklist

### OG image
- Both sites reference `https://packcheck.app/og-image.png` — **file does not exist yet**
- Must be 1200×630px PNG
- Drop into `bagofholding` repo root (and later `packcheck.app` repo root)
- Social platforms will show text-only cards until this exists

### Visual assets
- All source visual assets live in `/assets/` — see `assets/README.md`
- `topo-map.png` — USGS Philmont topo map (cream-tinted); used in splash background and OG image
- `og-image.png` — to be created (1200×630px)

### Move-to-category on mobile
- Desktop: inline category dropdown in actions column
- Mobile: dropdown hidden; no move-to-category available
- Decision pending: remove inline dropdown entirely and add to edit row only, or keep desktop-only as-is

### Qty input (mobile)
- Resolved: number spinners hidden, column width 12% on phones (≤900px breakpoint)
- Edit input fills column width; visible for 2-digit quantities

---

## Key implementation notes (critical — read before editing)

1. **`item.included` not `item.checked`** — packed state field
2. **`saveLocal()` not `saveData()`** — persistence function
3. **`crewOverrideOz` is in oz internally** — UI input accepts lbs, converts on entry
4. **`CREW_CAT_ORDER` array** — always use when iterating `crewGearData`; object key order unreliable
5. **`overflow-x:clip` not `overflow-x:hidden`** — `hidden` breaks `position:sticky` on nav
6. **`border-collapse:separate`** — required on `.gear-table` for sticky headers
7. **Gear table breakpoint is ≤900px** (not ≤640px) for column overrides — covers landscape phones
8. **Inline `style=` on `<col>`/`<th>`** beats CSS even with `!important` during table layout — qty column uses `.col-qty` / `.th-qty` CSS classes to allow media query overrides
9. **Deploy is a force-push** — do not push to `rhoegee/philmont.packcheck.app` directly
10. **`itinerary-data.js` is DO NOT HAND-EDIT** — always ask before modifying dates or itinerary data

---

## Phase 3 planning (not yet built)

- `packcheck.app` apex domain: splash page deployed to `rhoegee/packcheck.app`
- Additional editions: BWCA, JMT, PCT, other high-adventure bases
- Backend + user accounts
- Crew number lookup → auto-assign itinerary from Philmont registry
- Monetization layer (gear suggestions, premium features)
