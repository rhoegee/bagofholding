# packcheck.app — Content Page Brief
### Last updated: June 2026

---

## Goal

Transform `packcheck.app` from a single-screen splash into a real webpage — the brand hub for Packcheck and a genuine SEO-indexed resource for anyone preparing for a Philmont trek.

The page tells the broader Packcheck story (gear planning platform for outdoor adventures) while leading with Philmont content, which is where the real search demand is right now. This is not a blog. It is one well-written, authoritative page. The Philmont Edition app is the natural destination.

---

## Current State

The splash page (`splash/index.html` in bagofholding, served at `packcheck.app`) has:
- Logo lockup + tagline (Paper ground, topo map background, Gold rule)
- Mission statement paragraph (locked copy)
- One CTA → `philmont.packcheck.app`
- Correct SEO tags in `<head>`
- No indexable content of substance below the fold

**What's not done:** `rhoegee/packcheck.app` repo not yet created. Splash currently served from bagofholding. Needs its own repo + GitHub Pages + DNS before content additions go live. See `BRIEF_phase2.md` for deployment checklist.

---

## Page Structure

### Above the fold — DO NOT CHANGE
The existing splash design stays exactly as-is. Topo map background, logo lockup, tagline, Gold rule, mission statement, CTA button. This is locked.

### Below the fold — NEW CONTENT
All new content sits below the existing splash. The design should feel continuous with the splash — Paper ground, same typography, same palette. Not a jarring shift into a different page.

---

## Content Sections

### 1. What is Packcheck? (100–150 words)
Brand-level explainer for someone who found the page via search and doesn't know what they're looking at. Covers the platform vision — gear planning for any outdoor adventure — and introduces the Philmont Edition as the first release. Written in Rob's voice.

Key points to hit:
- Free, no account required, works in any browser
- Build a gear list, track weights, plan your crew's share
- Starts with Philmont, more editions coming
- Built by someone who actually uses it

### 2. Philmont Packing Basics (300–400 words)
**This is the primary SEO content.** Genuine, useful guidance from advisor experience. Written in Rob's voice — direct, practical, earned authority. Not a listicle, not generic advice.

Topics to cover:
- The 20–25 lb base weight target and why it matters at elevation (20–35% less oxygen)
- What base weight actually means vs. fully loaded pack weight
- The cotton rule — why it matters at altitude, what to use instead
- Bear bag protocol — what goes in, deodorant prohibition, smellables list
- Water requirements — 4L minimum, extra for dry camps, purification
- Key prohibited items (deodorant, hammocks, turkey bags, bear spray, drones, etc.)
- The crew gear reality — Philmont issues tents and pots; stoves and fuel are crew-provided

⚠ Rob to write or substantially revise this section in his own voice. Claude can draft, Rob approves.

### 3. How the App Works (150–200 words)
Walk through what the Philmont Edition actually does — the four tabs, what each one gives you. Brief and functional. Answers: "why would I use this instead of a spreadsheet?"

Key features to mention:
- Personal gear checklist with weight tracking
- Crew gear split calculator (adult/scout tent weight logic)
- Day-by-day pack weight simulator (food depletion, resupply, dry camps)
- All 48 Philmont 2026 itineraries built in — enter your itinerary number and your schedule loads
- Share your gear list with your crew via QR code

### 4. Sample Gear List (visual/scannable)
An abbreviated personal gear checklist — the most important items across the main categories. Not exhaustive — just enough to be useful and give Google something concrete to index. Ends with a CTA to the full app.

⚠ Pull from app defaults — they're already vetted.

### 5. About Packcheck (50–75 words)
Short. Built by a Philmont advisor. Free. No account required. More editions coming. One sentence on the broader vision. Link to the app.

---

## CTA Strategy

Three entry points into the app across the page:
- Hero CTA (existing) — "Open the Philmont Planner →"
- After Philmont Packing Basics — "Track your base weight in the app →"
- After Sample Gear List — "Build your full checklist in Packcheck →"

---

## SEO Notes

**Page title:** "Packcheck — Gear Planning for Outdoor Adventures" *(broader than Philmont — future-proofs the brand)*

**Meta description:** Already implemented. Covers Philmont content naturally.

Use these phrases naturally in the content — do not force them:
- Philmont packing list
- Philmont gear checklist
- Philmont base weight
- Philmont crew gear
- Philmont Scout Ranch packing
- Philmont 2026 / 2027

Do not stuff keywords. If a phrase doesn't fit naturally, skip it.

---

## Design Notes

- Content sits below the fold — Paper `#EFE6CF` background throughout
- Typography: Oswald for section headers, Zilla Slab for body text
- No new UI components needed — this is editorial content, not app UI
- Mobile-first — most users will be on phones

---

## Technical Notes

- All additions go into `splash/index.html` for now
- When `rhoegee/packcheck.app` repo is created, this becomes root `index.html`
- Add `robots.txt` → `https://packcheck.app/sitemap.xml` to that repo
- Add `sitemap.xml` listing `https://packcheck.app/` at priority 1.0
- Full deployment checklist in `SEO_Brief.md`
- Submit to Google Search Console after deployment

---

## What This Page Is Not

- Not a blog
- Not a gear store
- Not a community or forum
- Not a replacement for the app — it's the path to the app

---

## Open

- ⚠ Rob to write / approve "Philmont Packing Basics" section
- ⚠ `rhoegee/packcheck.app` repo creation — prerequisite for deployment
- ⚠ Page title tag update in `splash/index.html`
- ⚠ External video embeds — hold for now, revisit when Rob has own content
