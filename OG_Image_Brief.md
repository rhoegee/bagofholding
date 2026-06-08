# Packcheck — OG Image Brief

## Status: Implemented ✅

All four images rendered and committed. Pine versions are live. Cream versions archived.

---

## Deployed files

| File | Location | Served at | Status |
|---|---|---|---|
| `og-image-philmont.png` | repo root | `https://philmont.packcheck.app/og-image-philmont.png` | **Live** |
| `og-image.png` | repo root | `https://packcheck.app/og-image.png` | Ready — pending `packcheck.app` deploy |
| `og-image-philmont-cream.png` | `assets/` | — | Archived alternate |
| `og-image-generic-cream.png` | `assets/` | — | Archived alternate |

---

## Brand palette

| Token | Hex | RGB |
|---|---|---|
| Pine | `#2E4A39` | (46, 74, 57) |
| Cream | `#F4ECD8` | (244, 236, 216) |
| Paper | `#EFE6CF` | (239, 230, 207) |
| Gold | `#D6A93F` | (214, 169, 63) |
| Gold Dark | `#AA7814` | (170, 120, 20) — cream bg only |
| Scout Red | `#C5172B` | (197, 23, 43) |

---

## Approved font spec

| Role | Font | Weight | Size |
|---|---|---|---|
| Wordmark (PACKCHECK) | Oswald | Bold / 700 | **124px** |
| Kicker (PHILMONT EDITION) | Oswald | Regular / 400 | **36px** |
| Tagline (Pack Smart. Go Far.) | Zilla Slab Italic | **500** | **46px** |

Font TTFs needed for re-render: Oswald Bold, Oswald Regular, Zilla Slab 500 Italic.
Source woff2 files are in `fonts/` — convert with fonttools: `TTFont(src); t.flavor=None; t.save(dst)`.

---

## Topo background treatment

Source file: `assets/packcheck-topo.jpg`

### Pine versions
```python
# Key values — do not change without review
threshold_offset = 40
ramp_multiplier  = 4.0
opacity          = 0.30   # 30% — cream lines on pine background
line_color       = CREAM  # (244, 236, 216)
background       = PINE   # (46, 74, 57)
```

### Cream versions
```python
opacity = 0.60   # 60% — full topo detail visible on paper background
```

Full pipeline code is in `assets/render_og.py`.

---

## Checkbox spec

- Size = wordmark ink height (cap height of PACKCHECK at 124px)
- Wall thickness = 4.5% of checkbox size
- Gap between checkbox and P = H–E kerning of Oswald Bold
- Check mark = 78% of box height, vertically centered
- Check color = always Scout Red `#C5172B`

---

## Vertical layout — Philmont versions

```
kicker ink top    → base_y
[17px gap]         ← approved spacing
wordmark ink top  → base_y + kicker_height + 17
[12px gap]
tagline ink top   → base_y + kicker_height + 17 + wordmark_height + 12

checkbox top = wordmark ink top
checkbox size = wordmark ink height
```

---

## Four files

### A — Generic / Pine (`og-image.png`)
- Background: Pine + topo lines (30%)
- Checkbox: Cream
- PACKCHECK: Cream
- Tagline: Gold `#D6A93F`
- No kicker

### B — Generic / Cream (`assets/og-image-generic-cream.png`)
- Background: Paper blended with topo at 60%
- Checkbox: Pine
- PACKCHECK: Pine
- Tagline: Scout Red `#C5172B`
- No kicker

### C — Philmont / Pine (`og-image-philmont.png`) ← live
- Background: Pine + topo lines (30%)
- Checkbox: Cream, sized to PACKCHECK ink height
- PHILMONT EDITION kicker: Gold, 36px, 17px gap above PACKCHECK
- PACKCHECK: Cream, 124px
- Tagline: Cream, Zilla Slab 500 Italic 46px

### D — Philmont / Cream (`assets/og-image-philmont-cream.png`)
- Background: Paper blended with topo at 60%
- Checkbox: Pine
- PHILMONT EDITION kicker: Gold Dark `#AA7814`
- PACKCHECK: Pine
- Tagline: Pine

---

## Re-rendering

Script: `assets/render_og.py`
Run: `python3 assets/render_og.py` (requires Pillow, numpy, fonttools)

Output goes to `/tmp/` — copy to repo root and `assets/` as appropriate.

---

## Meta tag references

`index.html` (philmont app):
```html
<meta property="og:image" content="https://philmont.packcheck.app/og-image-philmont.png">
<meta property="og:image:alt" content="Packcheck: Philmont Edition — Pack Smart. Go Far.">
<meta name="twitter:image" content="https://philmont.packcheck.app/og-image-philmont.png">
```

`splash/index.html` (packcheck.app):
```html
<meta property="og:image" content="https://packcheck.app/og-image.png">
<meta name="twitter:image" content="https://packcheck.app/og-image.png">
```
