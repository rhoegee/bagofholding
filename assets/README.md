# /assets

Visual assets for Packcheck. All source files and alternates live here.

## Live files (repo root)

| File | Served at | Used in |
|---|---|---|
| `../og-image.png` | `packcheck.app/og-image.png` | `splash/index.html` OG/Twitter tags |
| `../og-image-philmont.png` | `philmont.packcheck.app/og-image-philmont.png` | `index.html` OG/Twitter tags |

## Source / alternates (this folder)

| File | Notes |
|---|---|
| `og-image-generic-cream.png` | Cream bg alternate for `packcheck.app` — not live |
| `og-image-philmont-cream.png` | Cream bg alternate for Philmont app — not live |
| `packcheck-topo.jpg` | USGS Philmont topo map source — used in OG image render + splash bg |

## Re-rendering OG images

Script: `/tmp/render_og.py` (not committed — recreate from `OG_Image_Brief.md`)
Fonts needed: Oswald Bold TTF, Oswald Regular TTF, Zilla Slab 500 Italic TTF
Topo source: `assets/packcheck-topo.jpg`

Key approved values (do not change without review):
- Topo opacity on pine bg: 30%
- Topo opacity on cream bg: 60%
- Tagline font: Zilla Slab 500 Italic at 34px
- Kicker/wordmark gap: 17px
- Wordmark: Oswald Bold 700 at 88px
