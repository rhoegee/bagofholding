# Packcheck — SEO Implementation Brief

## Overview

Two URLs, two purposes, one brand.

- **packcheck.app** — brand hub and product portfolio landing page
- **philmont.packcheck.app** — the Philmont Gear Planner app (live, in use)

Neither URL has meta descriptions, Open Graph tags, Twitter cards, structured data, a canonical tag, a favicon declaration (splash), robots.txt, or a sitemap. This brief covers everything needed for both.

Do not change any visual layout, copy, or functionality. SEO additions go in `<head>` only, plus two new files in the repo root.

---

## Deployment note — packcheck.app file location

During development, the packcheck.app landing page lives at `splash/index.html` inside the `bagofholding` repo. When deployed, it will move to a separate repo (`rhoegee/packcheck.app`) as a root `index.html`. All canonical URLs and asset paths in this brief are already written for the production URL (`https://packcheck.app/`) — no changes will be needed when the file moves. Make edits to `splash/index.html` for now.

---

## 1. packcheck.app — splash/index.html

Insert the following after the existing `<title>` tag:

```html
<!-- Primary SEO -->
<meta name="description" content="Packcheck is a free gear planning checklist for outdoor adventures. Start with the Philmont Edition — build your packing checklist, track pack weight, and plan your crew's resupply before your trek.">
<link rel="canonical" href="https://packcheck.app/">

<!-- Favicon -->
<link rel="icon" type="image/svg+xml" href="/favicon.svg">

<!-- Open Graph -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://packcheck.app/">
<meta property="og:title" content="Packcheck — Pack Smart. Go Far.">
<meta property="og:description" content="Free gear planning checklist for outdoor adventures. Philmont Edition available now — build your packing checklist, track weight, and plan your crew's resupply.">
<meta property="og:image" content="https://packcheck.app/og-image.png">
<meta property="og:site_name" content="Packcheck">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Packcheck — Pack Smart. Go Far.">
<meta name="twitter:description" content="Free gear planning checklist for outdoor adventures. Philmont Edition available now.">
<meta name="twitter:image" content="https://packcheck.app/og-image.png">

<!-- Structured Data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Packcheck",
  "url": "https://packcheck.app",
  "description": "Free gear planning checklists for outdoor adventures."
}
</script>
```

Note: The `SearchAction` block has been removed from the JSON-LD. The hub page has no search functionality, so including it would be inaccurate.

---

## 2. philmont.packcheck.app — index.html

Insert the following after the existing `<title>` tag:

```html
<!-- Primary SEO -->
<meta name="description" content="Free Philmont Scout Ranch packing checklist and gear planner. Build your personal checklist, track base weight, manage crew gear, and map your resupply by itinerary number. Built by a Philmont advisor.">
<link rel="canonical" href="https://philmont.packcheck.app/">

<!-- Open Graph -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://philmont.packcheck.app/">
<meta property="og:title" content="Packcheck: Philmont Edition — Free Packing Checklist">
<meta property="og:description" content="Free Philmont Scout Ranch packing checklist and gear planner. Build your list, track pack weight, and plan crew resupply by itinerary number.">
<meta property="og:image" content="https://packcheck.app/og-image.png">
<meta property="og:site_name" content="Packcheck">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Packcheck: Philmont Edition — Free Packing Checklist">
<meta name="twitter:description" content="Free Philmont Scout Ranch packing checklist and gear planner. Build your list, track pack weight, and plan crew resupply by itinerary number.">
<meta name="twitter:image" content="https://packcheck.app/og-image.png">

<!-- Structured Data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "Packcheck: Philmont Edition",
  "url": "https://philmont.packcheck.app",
  "description": "Free packing checklist and gear planning tool for Philmont Scout Ranch treks. Build your checklist, track base weight, manage crew gear, and plan resupply by itinerary number.",
  "applicationCategory": "UtilitiesApplication",
  "operatingSystem": "Any",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "USD"
  },
  "author": {
    "@type": "Organization",
    "name": "Packcheck",
    "url": "https://packcheck.app"
  }
}
</script>
```

---

## 3. Title tags — no changes needed

The current titles are correct as-is:
- `packcheck.app`: `Packcheck — Pack Smart. Go Far.` ✅
- `philmont.packcheck.app`: `Packcheck: Philmont Edition` ✅

The title tag is what appears in the browser tab and as the blue headline in Google results. Short and clean is the right call. The meta description carries the keyword weight.

---

## 4. New file: /robots.txt (bagofholding repo root)

Each repo owns its own sitemap. Cross-linking between the two sites is handled via OG tags and JSON-LD `author.url`, not robots/sitemap.

```
User-agent: *
Allow: /

Sitemap: https://philmont.packcheck.app/sitemap.xml
```

> **When `rhoegee/packcheck.app` is created:** add its own `robots.txt` pointing to `https://packcheck.app/sitemap.xml`.

---

## 5. New file: /sitemap.xml (bagofholding repo root)

Lists only the URLs served by this repo.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://philmont.packcheck.app/</loc>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

> **When `rhoegee/packcheck.app` is created:** add its own `sitemap.xml` listing `https://packcheck.app/` at priority 1.0.

---

## 6. OG image

Both URLs reference `https://packcheck.app/og-image.png`. This file does not exist yet and is being designed separately. It should be **1200×630px PNG**, dropped into the `bagofholding` repo root (and later the `packcheck.app` repo root).

Until it exists, OG tags will still parse correctly — social platforms will just show a text-only preview card. Do not block the SEO tag implementation on this.

---

## Summary of changes

| File | Repo | Action |
|---|---|---|
| `splash/index.html` | `bagofholding` | Add meta description, canonical, OG, Twitter, JSON-LD, favicon |
| `index.html` (philmont app) | `bagofholding` | Add meta description, canonical, OG, Twitter, JSON-LD |
| `robots.txt` | `bagofholding` root | Created — points to `philmont.packcheck.app/sitemap.xml` |
| `sitemap.xml` | `bagofholding` root | Created — lists `philmont.packcheck.app` only |
| `og-image.png` | `bagofholding` root | Add when ready — 1200×630px |

**When `rhoegee/packcheck.app` is created, also add:**

| File | Repo | Action |
|---|---|---|
| `robots.txt` | `packcheck.app` root | Create — points to `https://packcheck.app/sitemap.xml` |
| `sitemap.xml` | `packcheck.app` root | Create — lists `https://packcheck.app/` at priority 1.0 |
