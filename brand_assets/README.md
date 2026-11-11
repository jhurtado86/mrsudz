# brand_assets/ — required client assets

Drop the real client files here using the **exact filenames** below. Until a file exists,
the template ships that slot on `https://placehold.co/WxH` at the final dimensions, so the
site is never broken — it just shows a placeholder. Replacing a placeholder is a
find-and-replace of the `placehold.co/WxH` URL with the root-relative `/brand_assets/…`
path; **alt text is already written in final form and must not change on swap.**

All paths are root-relative (`/brand_assets/…`).

## Named background slots — dedicated files ONLY (never a content/gallery photo)

| File | Ratio | Dimensions | Used by |
|---|---|---|---|
| `hero-background.webp` | 16:9 | 1920×1080 | Hero background on every page (incl. `about.html`, `thank-you.html`) — **AI-generated — replace with real photo later.** |
| `cta-background.webp` | 16:9 | 1920×1080 | Final-CTA background on every page with a final-CTA — **AI-generated — replace with real photo later.** |

> These two slots are marked `<!-- OFF-LIMITS: … -->` in the HTML. A client content photo
> or gallery image is **never** promoted into either one.

## Social / Open Graph

| File | Ratio | Dimensions | Used by |
|---|---|---|---|
| `og-image.jpg` | 1.91:1 | 1200×630 | `og:image` + `twitter:image` on every page — built locally (navy `#153E66`, logo card, "Laundry Day Made Easy"). Rebuild when the client's high-res logo arrives. |

## Content photos — uniform container (`.photo-frame`)

Every content photo uses the shared `.photo-frame` class (one ratio site-wide). Export at
these sizes:

| Type | Ratio | Dimensions | Notes |
|---|---|---|---|
| Content photo (standard) | 4:3 | 1200×900 | Service/city/about body photos |

### Photo-tier counts (how many content photos per page)

| Page | Content photos |
|---|---|
| Flagship service (`services/wash-and-fold.html`) | 5 |
| Secondary push service (`services/laundry-pickup-delivery.html`) | 3 |
| Standard service (`self-service-laundry`, `ironing-steaming`, `comforter-cleaning`, `dry-cleaning`) | 2 each |
| City page (`areas/*.html`) | 1 each |
| `about.html` | 2 body (no owner portrait — the owner is never published) |

## Optional (per client, not shipped by default)
- `logo.png` — present (interim, from the current site; the client's original replaces it). Favicon, and any gallery-module photos (gallery stays blocked until real photos exist).

## Placed client photos (confirmed by `ls brand_assets/`, Oct 28 2026)

| File | Source | Size | Used on |
|---|---|---|---|
| `photo-washers-row.webp` | client batch 1 | 680×510 (low-res — request original) | index (intro), areas/san-juan |
| `photo-dryers-carts.webp` | client batch 1 | 680×510 (low-res — request original) | services/wash-and-fold (your-way), services/self-service-laundry (intro), areas/alamo |
| `photo-aisle-folding-tables.webp` | client batch 1 | 680×510 (low-res — request original) | services/wash-and-fold (intro), services/self-service-laundry (tips), areas/mcallen |
| `photo-seating-tvs.jpg` | client batch 1, resized from 1600×1200 | 1200×900 | index (amenities), about (amenities), areas/edinburg |
| `photo-logo-payment-wall.jpg` | client batch 1, cropped 4:3 from 960×1280 portrait | 960×720 | about (who we are) |

Never used for `hero-background` / `cta-background` (dedicated slots only).

## AI-generated images (Nov 11 2026) — **AI-generated — replace with real photo later**

Generated with Gemini `gemini-3.1-flash-lite-image` (Nano Banana 2 Lite), one call per image,
cropped to slot size and saved as webp. Stand-ins only: they do not show the real Mr. Sudz
facility, and their alt text describes the image without claiming it is Mr. Sudz.

| File | Size | Used on | Status |
|---|---|---|---|
| `hero-background.webp` | 1920×1080 | Hero on every page | AI-generated — replace with real photo later |
| `cta-background.webp` | 1920×1080 | Final CTA on every page with one | AI-generated — replace with real photo later |
| `ai-laundry-baskets.webp` | 1200×900 | services/wash-and-fold (who it's for) | AI-generated — replace with real photo later |
| `ai-laundry-bag-folded.webp` | 1200×900 | services/wash-and-fold (pickup option) | AI-generated — replace with real photo later |
| `ai-delivery-bag-carry.webp` | 1200×900 | services/laundry-pickup-delivery (intro) | AI-generated — replace with real photo later |
| `ai-pickup-bag-door.webp` | 1200×900 | services/laundry-pickup-delivery (get ready) | AI-generated — replace with real photo later |
| `ai-ironing-collar.webp` | 1200×900 | services/ironing-steaming (intro) | AI-generated — replace with real photo later |
| `ai-starched-shirts.webp` | 1200×900 | services/ironing-steaming (starch) | AI-generated — replace with real photo later |
| `ai-comforter-folded.webp` | 1200×900 | services/comforter-cleaning (intro) | AI-generated — replace with real photo later |
| `ai-blankets-stack.webp` | 1200×900 | services/comforter-cleaning (what we clean) | AI-generated — replace with real photo later |
| `ai-dry-cleaning-shirts-blazer.webp` | 1200×900 | services/dry-cleaning (intro) | AI-generated — replace with real photo later |
| `ai-dry-cleaning-blazer-coat.webp` | 1200×900 | services/dry-cleaning (tips) | AI-generated — replace with real photo later |

### Real client photos placed in storefront/interior slots (Nov 11 2026)

`photo-storefront.webp` — 510×383, cropped 4:3 from the client's `storefront.png` (510×510,
low-res — request original). No counter photo exists yet, so the counter slot uses the
closest real interior shot, with alt text rewritten to match what's shown:

| Slot | Real photo used |
|---|---|
| index (areas section — storefront) | `photo-storefront.webp` |
| services/laundry-pickup-delivery (availability — front of store) | `photo-storefront.webp` |
| areas/pharr (intro) | `photo-seating-tvs.jpg` |
| areas/hidalgo (intro) | `photo-dryers-carts.webp` |
| services/wash-and-fold (how it works — was "drop-off counter") | `photo-washers-row.webp` |

Still wanted from the client: a high-res storefront original and a drop-off counter photo.
