# Packcheck — Brand Reference
### Last updated: June 2026

---

## What Packcheck Is

Packcheck is a free gear planning platform for outdoor adventures. The core idea is simple: know what you're carrying before you leave for the trailhead. It helps anyone heading outside build a gear list, track weights, and prepare with confidence — whether that's a 12-day backcountry trek or a family camping trip. It's just as easy to over-pack as it is to forget some crucial items. Packcheck makes sure you have everything you need — and not one ounce more.

The first release is **Packcheck: Philmont Edition** — purpose-built for Philmont Scout Ranch crews because that's where the real need was. Philmont is one of the most logistically complex backcountry experiences available, with crew-shared gear, resupply points, dry camps, and strict weight guidelines. The Philmont Edition addresses all of that specifically.

The broader vision is a **platform of editions** — Philmont is the proof of concept, but the same engine applies to any outdoor trip: BWCA, JMT, PCT, family camping, overlanding, cabin trips. The target audience isn't the ultralight obsessive — it's the regular person who wants to go outside and be prepared. Think of it as a scout handbook for non-scouts.

The brand — **Packcheck** — is the through-line across all editions.

---

## Voice & Positioning

- Confident, direct, a little bit of a nudge — like a senior scout who's done it three times and genuinely wants your trip to go well
- Never over-marketed, never AI-sounding
- Functional over decorative — this is a gear checklist first, design serves use
- The human behind it: Eagle Scout, Assistant Scoutmaster, Wood Badge trained, Philmont advisor — background credibility, not overt branding
- Model: Christopher Kimball / Milk Street — the human soul behind it without being the explicit name on it

**Locked tagline:** Pack Smart. Go Far.

**Locked mission copy (splash page):** *"Packcheck helps you get ready so you can hit the trail with confidence. We're a gear checklist built for the backcountry — and so much more. It starts with Packcheck: Philmont Edition, a free gear-planning app custom-designed for Philmont Scout Ranch crews."*

---

## Visual Identity

### Palette — "Trailhead v2" — LOCKED

| Token | Hex | RGB | Role |
|---|---|---|---|
| Ink / Charcoal | `#1C1C1A` | (28, 28, 26) | Type, icon base lines, silhouettes |
| Pine | `#2E4A39` | (46, 74, 57) | Anchor / primary brand color |
| Pine-deep | `#243B2D` | — | Shadow / deep variant |
| Spruce | `#3C5E49` | — | Secondary green |
| Scout Red | `#C5172B` | (197, 23, 43) | The pop — completion, key actions, brand accent |
| Scout-deep | `#9E1322` | — | Pressed / deep red |
| Gold | `#D6A93F` | (214, 169, 63) | Keylines, kickers, badge trim, caution states |
| Gold Dark | `#AA7814` | (170, 120, 20) | Cream bg use only |
| Canvas | `#D8C39E` | — | Warm tan surface |
| Cream | `#F4ECD8` | (244, 236, 216) | Light background / reversed type |
| Paper | `#EFE6CF` | (239, 230, 207) | Default page background |
| Ink-soft | `#5D5240` | — | Muted body text |

**Critical color rule:** Scout Red = checked / completion / key action / brand accent ONLY. Never error, never caution. Cautions (cotton, dry camp, prohibited) → Gold. Destructive actions → Scout-deep with label. Difficulty ramp → Spruce → Gold → Scout-deep.

### Typography — LOCKED

| Face | Weights | Role |
|---|---|---|
| Oswald | 700 / 600 / 500 | Wordmark, headings, UI labels — condensed industrial caps |
| Zilla Slab | Italic | Rationale, body serif, taglines |
| JetBrains Mono | Regular | Kickers, captions, specs, data, IDs |

### Logo — LOCKED ("The Checkbox Lockup")

A cap-height square checkbox holding a solid Scout Red check, set to the left of the PACKCHECK wordmark in live Oswald 700 caps.

**Color logic:**
- On Pine → word & box Cream, check Scout Red
- On Cream → word & box Pine, check Scout Red
- Check always stays Scout Red regardless of surface

**Specs:**
- Box outer edge sits exactly on cap line + baseline
- Wall thickness ≈ 4.5% of cap height
- Check ≈ 78% of box height, vertically centered
- Box-to-P gap ≈ 0.16em (matches the word's own H–E spacing)
- Favicon = checkbox crop only

**Implementation:** `wordmark-core.js` — `PCWordmark.render()`. Do not redraw without explicit go-ahead.

### OG Images — LOCKED

Four versions rendered at 1200×630px. Pine versions deployed, cream versions archived.

| File | Location | Status |
|---|---|---|
| `og-image.png` | repo root | Live — packcheck.app |
| `og-image-philmont.png` | repo root | Live — philmont.packcheck.app |
| `og-image-generic-cream.png` | `assets/` | Archived alternate |
| `og-image-philmont-cream.png` | `assets/` | Archived alternate |

**Topo background treatment:** 1956 USGS Tooth of Time quadrangle. Contour lines extracted and rendered as Cream lines on Pine background at 30% opacity. Cream versions at 60% opacity on Paper background. Source: `assets/packcheck-topo.jpg`. Re-render script: `assets/render_og.py`. Full spec in `OG_Image_Brief.md`.

---

## Iconography — LOCKED

Three treatments, all active. App selects by surface:

| ID | Name | When used |
|---|---|---|
| A | Trail Monoline | Reversed in pine chrome / inline in text rows |
| B | Camp Badge | Default — app's cream ground |
| C | Field Two-Tone | Canvas surfaces |

**Spec:** 100×100 viewBox, charcoal base lines + Scout Red accent. PNG icons embedded as base64 data URIs in `pc-icons.js` (v6). Stroke icons (SVG paths) for icons without a PNG.

**Current glyph inventory (from `pc-icons.js` v6):**

PNG keys (17): `pack, sleep, poles, jacket, rain, soap, food, bottle, firstaid, chair, cook, compass, trowel, tape, consum, lantern, tent`

Stroke keys (1): `fly` (dining fly — wide inverted-V shape)

In ALL_KEYS but no PNG: `bear` — maps to `food` icon in crew gear rendering

**Locked glyph decisions:**

| Category | Glyph | Key detail |
|---|---|---|
| Clothing | Pants | Bootcut silhouette, red belt + buckle |
| Equipment | Trekking poles | Knob grips, baskets, red wrist straps |
| Sleep System | Sleeping bag in stuff sack | Solid charcoal caps, red center cinch |
| Consumables | Sunscreen tube | Stands on cap, crimped top, red label band |
| Rain Gear | Umbrella | — |
| Utility | Pocketknife | Folding; red hinge dot only |
| Cook System | Camping pot + bale | Taller pot, red bail handle |
| Luxury | Camp chair | Sling seat, crossed legs, red top rail |
| Other Shelter | Dining fly | Wide inverted-V, base + inner accent V |
| Bear | No PNG | Maps to `food` icon in crew gear |

---

## Data Visualization Palette (app only — not brand colors)

Used for gear category charts. Scout Red is reserved and never assigned to a category.

Emerald `#1F8A4D` · Berry `#A83C72` · Cobalt `#2E73C4` · Olive-lime `#94B021` · Turquoise `#14A8A0` · Pumpkin `#E97B2E` · Grass `#5DAE37` · Sky-cyan `#2BA8CC` · Amber `#EBB019` · Clay `#BC4B33` · Ochre `#8C7A4E`

Day-bar chart: bars ramp light grass → deep pine by weight; heaviest day(s) pop Scout Red.

---

## URL Structure

| URL | Purpose |
|---|---|
| `packcheck.app` | Brand hub, content, product landing |
| `philmont.packcheck.app` | Philmont Edition app (live) |
| `beta.packcheck.app` | Dev CNAME (bagofholding main branch — active dev on `claude/beautiful-babbage-biA91`) |
| Future: `[destination].packcheck.app` | Each additional edition |

---

## What We Are Not

- Not affiliated with Philmont Scout Ranch or Scouting America
- Not a gear retailer (affiliate links planned for future, never the primary identity)
- Not an AI product
- Footer: "© 2026 Packcheck · Not affiliated with Philmont Scout Ranch or Scouting America"

---

## Open / Unresolved

- ⚠ Parent company name beyond "Packcheck" — undecided
- ⚠ Email list / Mailchimp — removed from current build, revisit post-trek
