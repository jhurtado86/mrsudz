# CLAUDE.md — Mr. Sudz Laundromat (LOCKED — one open input)

> **Status:** LOCKED Oct 22, 2026 (strategy lock with Juan). All decisions resolved — see
> **DECISIONS (resolved)** at the bottom. The ONLY open client input is the **delivery
> zone**, which sets each city page's angle (it does not block Prompts 0–3).
> Any remaining `[NEEDS INPUT]` is backfill: build without the claim, never invent it.

---

## What This Is

This is the **Mr. Sudz Laundromat** website, built on the Nexor AI template.
The generic template placeholders are resolved to this client's real identity below;
anything not yet confirmed is left `[NEEDS INPUT]` and must NOT be invented. Keep the
template's structure, section rhythm, nav pattern, dark sections, footer layout, and
design system intact — only content, brand, service area, colors, logo, photos, and copy
are client-specific.

Trade: **Laundromat + laundry services** (self-service laundromat, wash/dry/fold drop-off,
ironing & steaming/pressing, and pickup & delivery). Several template modules are
home-services artifacts that do not apply to this trade — see "Template Sections to DELETE."

Treat any remaining `[NEEDS INPUT]` field as fill-in-the-blank. Do not invent client
facts; confirm with the client / Juan before filling.

**Source of current facts:** the client's existing CleanCloud-built site (mrsudzrgv.com:
Home, Pricing, Promotions, Contact, Book). Anything below marked *(from current site)* is
the client's own published copy — still confirm with the client before treating as locked.

---

## Resolved token reference

| Token | Resolved value |
|---|---|
| Business name | Mr. Sudz Laundromat (short brand: Mr. Sudz) |
| Service One … Six | 1. Wash, Dry & Fold · 2. Laundry Pickup & Delivery · 3. Self-Service Laundry · 4. Ironing & Steaming · 5. Comforter & Bedding Cleaning · 6. Dry Cleaning |
| service slugs | `wash-and-fold` · `laundry-pickup-delivery` · `self-service-laundry` · `ironing-steaming` · `comforter-cleaning` · `dry-cleaning` |
| Primary city | Pharr, TX (physical location; anchors NAP + homepage) |
| City 2 … City 6 | McAllen · San Juan · Edinburg · Alamo · Hidalgo (delivery coverage per city = [NEEDS INPUT]) |
| city slugs | `pharr` · `mcallen` · `san-juan` · `edinburg` · `alamo` · `hidalgo` |
| Region | Rio Grande Valley (RGV), Hidalgo County, TX |
| Phone (site) | [NEEDS INPUT — GHL tracking number ONLY]. Current public number *(from current site)*: (956) 232-9274 — used in the client's own marketing posts, so very likely the business line (not a personal number). Stays on GBP as-is (DECISION #6). |
| Email | info@mrsudzrgv.com *(from current site)* |
| Domain | mrsudzrgv.com — canonical host **https://www.mrsudzrgv.com** (set as Vercel Primary day one; non-www 301 → www) |

> ⚠️ **Email domain may differ from website domain.** If so, both can be correct — do NOT
> "fix" one to match the other, and never build a URL off the email domain. Confirm.
> (Currently both are mrsudzrgv.com.)

> ⚠️ **Domain migration risk:** mrsudzrgv.com currently runs on CleanCloud's website
> builder, which also hosts the live `/book` flow. Repointing DNS to Vercel removes that
> page. Before cutover, get the CleanCloud booking widget/hosted booking link and wire it
> into the new site. [NEEDS INPUT — CleanCloud booking URL or embed code]

---

## Brand color system — FROZEN methodology, FILL the values

Palette is **derived from the client logo every build** — extract the hexes from
`brand_assets/logo.png`; never assume the template's colors. Define once via CSS custom
properties + Tailwind `theme.extend.colors`; reuse everywhere; never hardcode hexes per
page.

Logo source *(from current site)*:
`https://dafgr1y3h3vlw.cloudfront.net/images/logos/361751741098512.png` — download into
`brand_assets/logo.png` (or get the original high-res file from the client). Current site copy
leans blue (💙 used throughout) — confirm against the actual logo hexes.

**Derived Oct 27 2026** from the current-site logo (300×151 PNG, now `brand_assets/logo.png`).
The logo is two flat colors on white: navy `#153E66` (~34% of pixels — wordmark, washer,
mustache) and sky blue `#43A9DF` (~5% — "LAUNDROMAT," suds). Every other token is derived
from those two. Re-check the hexes when the client's original logo file replaces this one.

| Token | Hex | Role |
|---|---|---|
| `--color-primary` | `#153E66` | Primary brand (logo navy) — dark hero/sections, footer, nav, primary buttons |
| `--color-primary-mid` | `#1D4C7A` | Mid-tone — first dark-elevation step, primary hover, borders/dividers on dark |
| `--color-accent` | `#43A9DF` | Accent (logo sky blue) — icons, fills, highlights. **Text ON an accent fill must be `--color-ink`/`--color-primary`, never white** (white 2.63:1 ✗ · ink 6.41:1 ✓) |
| `--color-accent-deep` | `#1D6FA0` | On-light fallback for the accent — small text/links/dividers on white (5.48:1) and bg-2 (5.04:1) |
| `--color-accent-bright` | `#6CC0EA` | On-dark accent — accent text/eyebrows on `--color-dark` (5.42:1). The raw logo sky is only 4.17:1 on navy, so it's not used for small text on dark |
| `--color-silver` / neutral | `#C3CED9` | Muted borders, secondary text on dark (6.88:1 on dark), chrome |
| `--color-dark` (canonical) | `#153E66` (= primary) | THE single dark-section background token |
| `--color-dark-3` | `#255783` | Deepest dark-elevation surface (cards on dark) |
| `--color-ink` | `#0F1E2E` | Near-black navy for headings/body (16.86:1 on white) |
| `--color-bg` | `#FFFFFF` | Body/content backgrounds |
| `--color-bg-2` | `#F2F6FA` | Light section tint (navy-tinted off-white) |
| `--color-muted` | `#576B80` | Muted/secondary text — 5.50:1 on bg, 5.06:1 on bg-2 |
| `--color-muted-light` | `#8496A9` | Lighter muted text — large/meta text only (3.04:1 on white) |
| `--color-line` | `#D9E2EB` | Hairlines/borders on light |

*Rows `accent-bright`, `dark-3`, `bg-2`, `muted-light`, and `line` are tokens `brand.css`
already defines, added here so every token has a value. The values aren't in `brand.css`
yet — they get applied there in Prompt 1. `--color-rating` stays unused (no stars until
the review widget is live).*

**FROZEN rules:**
- **Accent-on-light fallback:** a bright accent is fine as fill / text-on-dark; as small
  text or dividers on white it goes low-contrast — fall back to `--color-accent-deep`.
- **One canonical dark token:** `--color-dark` is the only dark-section background. Never
  let a second near-identical dark hex drift in.
- **Strip the template's red.** The template ships red as de-facto primary — remove it.
  Red is semantic (emergency/urgency) only, and only if the brand actually uses it.
  **Decided: no red in this palette.**
- **Never use default Tailwind blue/indigo/sky/cyan.** Drive every color from the brand
  tokens and derive shades from them. (Especially relevant here — if the brand is blue,
  the blues come from the logo hexes, never Tailwind's `blue-*`/`sky-*`.)

---

## Integration placeholders — FROZEN insertion points, DECIDE per client

- `<!-- GHL CONTACT FORM EMBED -->` — [NEEDS INPUT — form name]. Use the GHL embed; never a custom form.
  (Current site uses a CleanCloud contact form: Name*, Email*, Phone, Message*.)
- `<!-- CLEANCLOUD BOOKING EMBED -->` — **client-specific addition.** Pickup & delivery
  orders run through CleanCloud (web booking + CleanCloud app). [NEEDS INPUT — booking
  widget code or hosted link]. All "Book Now / Schedule a Pickup" CTAs point here.
- `<!-- GHL CHAT WIDGET SCRIPT -->` — [NEEDS INPUT] (insert before `</body>`).
- `<!-- GHL EXTERNAL TRACKING SCRIPT -->` — [NEEDS INPUT] (insert in `<head>`).
- `<!-- GHL REVIEW WIDGET EMBED -->` — **KEEP THE SLOT, wire later.** 128 Google reviews
  confirmed; widget code is backfill. Until it's live: no review count, stars, or rating
  in copy or schema. When it's wired and displayed, add `aggregateRating` to the homepage
  JSON-LD in the same commit — never before.
- `<!-- GOOGLE MAPS EMBED -->` — **WIRE.** Public storefront address confirmed on current
  site: 1032 W. Sam Houston Blvd., Ste. 6, Pharr, TX 78577.
- `<!-- INSURANCE CARRIER LOGO ROW -->` — **DELETE.** Not applicable to a laundromat.
- `<!-- FINANCING SECTION -->` — **DELETE.** Not applicable.
- Social share image: `brand_assets/og-image.jpg` (1200×630) — [NEEDS INPUT — create before launch].

---

## Template Sections to DELETE for this client

- Financing block / CTA — **DELETE**
- Insurance carrier-logo row + any insurance copy — **DELETE** (no insurance angle in this trade)
- Review widget / star rating / review-count blocks — **DELETE until confirmed**
- Inventory / gallery page — **NOT in v1** (revisit when Juan's photos arrive)
- Trust-badge pill row in the hero — delete by default (redundant with the eyebrow)
- Home-services artifacts to remove: "emergency service," "free estimate / free quote,"
  "licensed & insured," "same-day technician dispatch," any repair/replacement framing.
  Replace quote-CTA language with **Book a Pickup / Visit Us / Call** framing.

## Trade Adaptation — contractor template → laundromat (client-specific)

The Nexor template was built for contractors. This build CLONES it (keep structure,
nav, footer, dark sections, design system, schema patterns, serve/screenshot tooling)
but adapts these pieces. Prompt 0 must report which of these exist in the template.

**Swap:**
- Every "Get a Free Quote / Free Estimate" CTA → primary **Book a Pickup** (CleanCloud),
  secondary **Get Directions** or **Call**. Final-CTA section uses the same pair.
- Estimate/quote form sections → GHL contact form (questions, commercial inquiries) +
  CleanCloud booking for orders. No quote-request framing anywhere.
- "Our Process" / project-steps section → **How Pickup & Delivery Works**
  (Book → Pickup → Wash → Delivery — the 4 steps on the current site).
- Service-area / "we come to you" copy → storefront-first: hours + address + map, with
  delivery as the add-on.

**Add (sections a contractor template won't have):**
- **Hours + Visit block** (open daily 7am–10pm, address, map, parking) — homepage, near top.
- **Amenities block** (free Wi-Fi, charging stations, etc. — confirmed items only).
- **Pricing block** — on the Wash & Fold and Comforter pages only (see Price list; DECISION #1).
- ~~Promotions band~~ — **decided: no promotions anywhere on the site.**

**Delete (contractor-only):** before/after galleries, project portfolio, emergency
service banners, "licensed & insured" badges, financing, insurance carrier rows,
warranty sections, crew/technician bios.

---

## Business Identity

- Business name / short brand: Mr. Sudz Laundromat / Mr. Sudz
- Industry / trade: Laundromat & laundry services (drop-off, pickup & delivery, pressing)
- Owner: **LOCKED — the owner's name is NEVER published anywhere on this site** (no About
  the Owner section, no body copy, headings, meta/OG, schema, alt text, or CTAs). The
  About page is about the business and the laundromat, not a person. Zero grep hits for
  the owner's first name before deploy.
- Staff / team: never named. Use only "friendly on-site attendants" and "our driver." **Never infer staff or roles from social posts. Confirm
  directly with the client.**
- Relationship claims: **FROZEN** — no "family owned," "husband and wife," "couple," or
  any relationship structure without explicit written confirmation. "Family-run" is a
  tone signal (safe); a relationship *claim* is a fact (needs confirmation).
  → **Confirmed (Juan, Oct 22 2026):** publish "family-owned and operated" — the client's own
  written description. Nothing beyond that phrase (no who, no relationships).
- Differentiator / ownership signal: family-owned and operated + the amenities (TVs, A/C, snack bar, attendants)
- Client's own positioning *(business description, pasted by Juan Oct 22 2026)*: family-owned
  Pharr laundromat offering self-service and wash, dry & fold, with "an array of added
  amenities," aiming to be the premier laundromat in the Rio Grande Valley.
  → Use as the **positioning direction**, not as copy. "Premier laundromat in the RGV" is
  an aspiration — never state it as a fact or ranking. Amenities are the proof point.
  ("Top-notch" is on the SEO-CONTENT-PROMPT banned list — don't reuse his wording.)
- About page content: the business — family-owned and operated, Pharr storefront, services,
  amenities, "Laundry Day Made Easy." No owner name, no founding year, no history claims.
- **FROZEN framing rule:** an experience figure is a PERSONAL claim, not a business-age
  claim. Write "[N] years in the [trade]" — never "[N] years serving [City]" (implies
  business age). Founding year is separate and [NEEDS INPUT] until confirmed.
- Supplier / franchise / dealer relationship: Independent (no franchise indicated)
  Make no franchise or affiliation claim either way. Software: CleanCloud (booking/POS) — not a public claim.
- Physical address: **1032 W. Sam Houston Blvd., Ste. 6, Pharr, TX 78577** *(from current site)*
  → PostalAddress INCLUDED in schema.
- Phone (site): [NEEDS INPUT — GHL tracking number]
- Phone (owner personal — NOT FOR PUBLICATION): none provided. Only the GHL number (and
  the business line above, if ever needed) may appear.
- Email: info@mrsudzrgv.com
- Domain + canonical host: **https://www.mrsudzrgv.com**
- Founded year: unknown — never state or compute it.
- Licenses / certifications: N/A for trade — publish none.
- Official tagline: **"Laundry Day Made Easy"** (client's own phrase from current site).
- Review / reputation status: **128 Google reviews (confirmed by Juan, Oct 2026).**
  Star rating arrives with the widget. Review widget will be wired LATER (backfill). Until the
  widget is live on the page: no stars, no `aggregateRating`, no testimonials. Leave the
  `<!-- GHL REVIEW WIDGET EMBED -->` slot in place on the homepage so it drops in without
  layout work. **Decided: no review count in copy until the widget is live.**
  Do NOT carry over "100% Customer Satisfaction (based on reviews)." Unattributed
  testimonials are never published.
- Price range: **`$`** (JSON-LD `priceRange`)
- Social: Facebook https://www.facebook.com/MrSudzLaundromat ·
  Instagram https://www.instagram.com/mrsudzlaundromat/

### Key operational facts (must be accurate everywhere once filled)
- Service model: **both** — walk-in self-service + drop-off at the store, AND pickup &
  delivery (described on current site as "now available" / "new").
- Delivery area / radius / zip codes: [NEEDS INPUT — the ONE open client question; sets city-page angles]
- Delivery minimums, fees, turnaround time: **not stated on the site** — route to "book online to see pickup times."
- Intake method / primary CTA framing: **Book a pickup online (CleanCloud)** for
  delivery; **"Visit us — open daily 7am–10pm"** for self-service; phone as secondary.
  Booking also available via the **CleanCloud app**.
- Payment at machines: **not stated on the site** (unconfirmed — do not say coin, card, or app).
- Machines: describe only as modern, high-efficiency, fast (client's own words). No counts,
  sizes, or brand names.
- Amenities *(from current site FAQ)*: 75" big-screen TVs, free Wi-Fi, charging stations,
  cold A/C, snack bar (drinks and treats for purchase), clean modern facility, friendly
  on-site attendants. Do NOT claim attendants are on duty every open hour; no seating counts,
  detergent sales, or parking claims.
- Wash, Dry & Fold drop-off flow *(from current site FAQ)*: drop off with the attendant →
  state preferences (detergent, drying, special instructions) → washed, dried, folded →
  ready for pickup. No turnaround time on the site — never "same-day."
- Retail *(from current site)*: hangers, Mr. Sudz laundry bag.
- Language: **English only for v1.** No Spanish sections, no hreflang.

### Price list *(from current site, confirmed matches Juan's paste Oct 22 2026)*
> **DECISION #1 (locked):** publish ONLY the Wash, Dry & Fold group below — the $1.50/lb
> rate plus comforter and coverlet/blanket prices — on the Wash & Fold and Comforter pages
> (copy + FAQ OK). Everything else (ironing, starch, dry cleaning, retail) is reference
> only: never published; route that pricing intent to "call or book online."
> JSON-LD: `priceRange: "$"` only — no price values in Offer blocks.

| Group | Item | Price |
|---|---|---|
| Wash, Dry & Fold | Wash & Fold, per lb | $1.50 |
| | Comforter — Twin / Full / Queen / King | $15 / $18 / $22 / $22 |
| | Down/Feather Comforter | $28 |
| | Coverlet/Blanket — Twin / Full / Queen / King | $11 / $14 / $17 / $17 |
| Ironing (listed under Delivery) | Pants, Shirts, Shorts, Skirts | $2.75 each |
| | Starch — Regular / Heavy (per item) | $0.25 / $0.50 |
| In-Store | Shirt/Blouse — Short / Long Sleeve | $5.50 / $6.00 |
| | Slacks | $5.50 |
| | Sweater — Short / Long Sleeve | $6.50 / $7.50 |
| | Dress — Short / Long | $9.00 / $11.00 |
| | Blazer/Coat | $10.00 |
| | School Band Uniform | $15.00 |
| Retail | Hangers (5-pack) | $1.00 |
| | Mr. Sudz Laundry Bag | $10.00 |

"In-Store" = **Dry Cleaning** (confirmed Oct 22 2026 via the client's dry cleaning post).

### Promotions — **decided: none on the site.** Do not mention any discount, promo, or
first-order offer anywhere (they change too often to keep accurate).

### Hours (for `openingHoursSpecification`)
- Open daily 7:00am–10:00pm *(from current site)* → `Mo-Su 07:00-22:00`
- No last-wash or drop-off cutoff claims.

---

## Services — FROZEN methodology, FILL the six

**FROZEN:** select service pages for search volume + lead intent (broad high-intent
categories over narrow component terms). Minor/related services fold in as on-page
sections or FAQ, not their own pages. Default is six pages; flex only if the client
genuinely needs more/fewer.

- **Homepage target:** "laundromat Pharr" / "laundromat near me" (the broad category term
  lives on the homepage, NOT a service page)
- **Flagship (highest volume + lead value):** Wash, Dry & Fold — `/services/wash-and-fold.html`
  ("wash and fold near me," "drop off laundry service"). Current listed rate $1.50/lb.
- **Secondary push (differentiator / highest ticket):** Laundry Pickup & Delivery —
  `/services/laundry-pickup-delivery.html` (new service, recurring revenue, CleanCloud booking)
- **Standard:**
  - Self-Service Laundry — `/services/self-service-laundry.html` (machines,
    amenities; must lead with "self-service" phrasing, not "laundromat," to avoid
    colliding with the homepage)
  - Ironing & Steaming — `/services/ironing-steaming.html` (pressing; workwear, uniforms,
    dresses, school band uniforms; starch options)
  - Comforter & Bedding Cleaning — `/services/comforter-cleaning.html` (comforters, down/
    feather, coverlets, blankets — all sizes)
  - Dry Cleaning — `/services/dry-cleaning.html` (**confirmed** — client's own post, pasted
    by Juan Oct 22 2026: suits & dress shirts, dresses & skirts, jackets/blazers/coats,
    pants, sweaters; workwear + special-occasion angle). This is the "In-Store" price
    group. Copy never says "on-site" / "in-house" or states a turnaround (unconfirmed) —
    frame as "drop off your dry cleaning at Mr. Sudz."
- **Folded-in sub-services (sections/FAQ, not pages):** starch options (regular/heavy),
  school & band uniform pressing, retail laundry bags & hangers.

> ⚠️ **FROZEN anti-cannibalization:** keep distinct search intents on distinct pages
> (e.g. repair vs replacement). Never introduce a broad umbrella page that cannibalizes
> two narrower ones.
> Client-specific: **Wash & Fold** (the service — drop-off or delivered) vs **Pickup &
> Delivery** (the convenience — "laundry delivery service near me") stay separate. Wash &
> Fold page links to Pickup & Delivery for the delivery option; it does not re-explain it.

---

## Site Architecture — FROZEN structure, FILL the slugs

> ⚠️ **FROZEN — VERIFY BEFORE WRITING PATHS.** After cloning the template and before
> finalizing any path here, run `find . -name "*.html"` and confirm the real tree matches.
> Prior builds shipped `CLAUDE.md` paths that didn't match the repo and paid for it every
> session. **Disk is the source of truth.**

- Homepage `index.html`
- About `about.html`
- Contact / Thank-You `thank-you.html` (noindex, nofollow)
- Service pages under `/services/`: `wash-and-fold.html`, `laundry-pickup-delivery.html`,
  `self-service-laundry.html`, `ironing-steaming.html`, `comforter-cleaning.html`, `dry-cleaning.html`
- City pages under `/areas/`: `pharr.html`, `mcallen.html`, `san-juan.html`, `edinburg.html`, `alamo.html`, `hidalgo.html`
- Inventory/gallery page: **none in v1**
- No pricing page, no promotions page, no contact page (contact = homepage section + GHL form)

> **Redirects (locked) — 301 in `vercel.json` at cutover:**
> `/pricing` → `/services/wash-and-fold.html` · `/promotions` → `/` · `/contact` → `/` ·
> `/book` → `/services/laundry-pickup-delivery.html`

### City priority — FROZEN methodology, FILL the order
Home city anchors the homepage + NAP. Deepest city page = highest-volume target and
becomes the CITY-PAGE TEMPLATE. Order drives GSC indexing sequence.

**SEO goal (Juan, locked):** win Pharr (homepage + map pack) AND rank in the neighboring
cities. City pages are built for every neighbor regardless of delivery coverage. Each
city page's angle is set by what's TRUE for that city:
- **In the delivery zone** → lead with pickup & delivery to that city, plus the walk-in option.
- **Outside the zone** → lead with the drive-in angle (real route/drive from that city to
  W. Sam Houston Blvd.) and wash & fold drop-off. Never imply delivery there.
- Never claim a location in a neighbor city — one storefront, in Pharr.

- Order (locked; zone status per city = [NEEDS INPUT]):
  1. **Pharr** — home city; storefront on W. Sam Houston Blvd.
  2. **McAllen** — largest adjacent market, highest volume → **DEEPEST city page / city
     template** (Prompt 4). If McAllen turns out to be outside the zone, it still leads —
     with the drive-in angle.
  3. **San Juan** — immediately east of Pharr
  4. **Edinburg** — large market north (UTRGV students/renters = wash & fold demand)
  5. **Alamo** — east along the same corridor
  6. **Hidalgo** — south of Pharr
- Delivery zone answer only changes each page's angle, never the list.

---

## Always Do First — FROZEN
Invoke the frontend-design skill before writing frontend code **if available** in the
environment (it may not be installed in Claude Code — proceed without it if not).

## Content Writing Methodology — FROZEN
For all page copy, read and follow `SEO-CONTENT-PROMPT.md` in full as the PRIMARY writing
methodology before writing any content. If wording ever conflicts with the technical rules
below, `SEO-CONTENT-PROMPT.md` wins on wording; the rules below govern technical
implementation.

GBP categories for the prompt (working set — Juan will correct if the profile differs):
primary **Laundromat**; secondaries **Laundry Service**, **Dry Cleaner**. GBP services = the
six service pages.

---

## Local SEO Requirements — FROZEN (fill only the title/description tokens)

**Per-page metadata (every page):** unique `<title>` <60 chars; unique
`<meta description>` <160 with a service + city + CTA; local `keywords`;
`robots` index/follow with max-image/snippet/video-preview; self-referential `canonical`;
`<html lang="en">` + viewport.

**Open Graph + Twitter (every page):** og:title/description/url/type/image/locale/site_name;
twitter summary_large_image + title/description/image; images → 1200×630 (flag if not created).

**Structured Data (JSON-LD) — FROZEN patterns:**
- Homepage: `@type` = **`DryCleaningOrLaundry`** (schema.org's specific LocalBusiness
  subtype for laundromats/laundry services — never bare LocalBusiness).
  Include name, telephone (GHL), email, priceRange (pending), `openingHoursSpecification`,
  `areaServed` (full city list), `hasOfferCatalog` (the service pages), `sameAs`
  (Facebook + Instagram).
- **PostalAddress:** **INCLUDE** — public storefront: 1032 W. Sam Houston Blvd., Ste. 6,
  Pharr, TX 78577, US.
- **`aggregateRating`:** include ONLY when real reviews are confirmed AND displayed.
- License numbers → `additionalProperty`. (N/A here.)
- **Service pages:** 3 blocks — `Service` + `FAQPage` (min 6 Q&As) + `BreadcrumbList`.
- **City pages:** 3 blocks — `LocalBusiness` ref (same `@id` as homepage, not a
  re-declaration) + `FAQPage` (min 4 city-scoped Q&As) + `BreadcrumbList`.
  `areaServed` = that city only, never the full list.
- **Inventory/gallery pages:** `ImageGallery` or `CollectionPage` only — never `Service`.
- **Thank-you trio (one atomic unit):** noindex/nofollow meta + excluded from `sitemap.xml`
  + Disallow in `robots.txt`.
- **Per-page title collision:** the flagship service title must lead with a different
  phrase than the homepage title even when they share a keyword.
- **Offer-catalog count == live service-page count.**
- Validate at `search.google.com/test/rich-results` before launch.

**Visible on-page SEO — FROZEN:** exactly one `<h1>`/page; H2/H3 hierarchy, no skipped
levels; city names in human-readable body text; service+city combos appear naturally;
descriptive alt text with service/location context.

**City pages — anti-duplicate — FROZEN:** each city page ≥30–40% unique content; never
just swap the city name (doorway-page penalty); reference real, VERIFIED local anchors
(highways/neighborhoods/landmarks/districts) — flag `[VERIFY]` rather than invent; unique
intro + unique "why [City] chooses us" per page.

**Technical SEO files — FROZEN:** `sitemap.xml` (all indexable pages; exclude thank-you);
`robots.txt` (allow crawl, disallow thank-you, point to sitemap).

**Title/description patterns:**
- Homepage: `Laundromat in Pharr, TX | Mr. Sudz Laundromat` —
  "Clean laundromat in Pharr, TX with self-service machines, wash & fold, ironing, and
  pickup & delivery. Open daily 7am–10pm. Book a pickup today."
- Service page: `[Service] in Pharr, TX | Mr. Sudz` — flagship leads with
  "Wash & Fold Laundry Service" (not "Laundromat") per the collision rule.
- City page: `Laundry Service & Delivery in [City], TX | Mr. Sudz` (adjust per final
  zone; non-delivery cities lead with the walk-in angle instead).

---

## Hero & Asset Patterns — FROZEN

### Hero + Final-CTA backgrounds — dedicated named slots ONLY
- The hero background and the final-CTA background are **their own asset slots.** They are
  filled **only** by a purpose-made image named exactly `hero-background.*` and
  `cta-background.*` in `brand_assets/`.
- **They NEVER use a client content/job photo.** A client's section/gallery photos are
  never promoted into either background. Ever.
- Until the dedicated file exists, both stay on `https://placehold.co/1920x1080` at exact
  final dimensions. Flag as pending — never substitute another image to "fill" it.
- **Off-limits on every content-photo and layout pass** (also enforced in WORKFLOW.md).
  A photo/layout prompt must not touch these two backgrounds unless it is explicitly about
  them.
- Static full-bleed image is the default hero on every page including the homepage
  (`min-h-screen`, left-anchored text block, image + dark overlay ~0.7 + edge vignette +
  text-shadows).

### Hero video — enhancement, homepage only
Only when the client provides a usable clip. Replaces the static homepage hero; the
`hero-background` image becomes the poster/fallback. **FROZEN sequence, never skipped:**
trim only → save preview → client approves in/out → compress separately (H.264, strip
audio, ~2–3MB) → wire in last. `.gitignore` the raw source + trim preview; commit only the
final compressed clip.

### Uniform photo sizing — every section, every page
- **Every content photo uses the same-size aspect-ratio container** (`aspect-ratio` +
  `object-fit: cover`), never a fixed `h-[Npx]`. One ratio applied site-wide so no photo
  is a different size than another within or across sections.
- This is independent of the photo *tier* (which sets how MANY photos a page gets, below).
  Tiers govern count; this rule governs that every container is the same dimensions.

### Gallery / inventory section — uniform grid, no dead space
If the client has a dedicated gallery or inventory section:
- **Uniform grid:** equal cells, consistent gutters, every image the same size.
- **No dead space and no ragged last row** — size the grid so the final row fills or is
  balanced; never leave an orphaned single image floating in an empty row.
- Inventory/gallery page is **blocked until real photos exist** — do not ship it against
  placeholders.
- Excluded photo types apply here too (see below).

### Photo Tier Allocation — FROZEN default (override per client at strategy lock)
| Page type | Body photos | Hero |
|---|---|---|
| Flagship service | 5 | ✓ |
| Secondary push service | 3 | ✓ |
| Standard service | 2 | ✓ |
| City page | 1 | ✓ |
| About | 2 | ✓ |
| Inventory / gallery | No limit (reuse accepted) | ✓ |

**FROZEN rules:** one-photo-one-slot on all non-inventory pages (no photo twice on a
page); cross-page reuse minimized except on inventory; excluded types everywhere —
readable license plates, strong tilt/rotation, stained/damaged subjects, anything
privacy-sensitive; owner/people slots use `aspect-[3/4]` + `object-position: center top`
(portrait is the norm for headshots); document EXACT asset filenames confirmed by
`ls brand_assets/` — never assume naming.

**Client-specific exclusions (laundromat):** no identifiable customers without consent,
no customers' personal garments/undergarments recognizable, no visible customer faces in
the background of facility shots, no delivery-vehicle plates.

**Known existing photos *(from current site, CleanCloud CDN)* — get the client's OK + originals:**
- Hero/washer image: `.../website-builder/websites/1105/98d88fb6-cafb-4b8f-9f6a-8b44f2b58888.webp`
- Pricing image: `.../1105/13a35c8d-2fd6-4e76-8bc2-18babc048570.jpg`
- Facility tour (contact page): `976b0a60…jpg`, `3e2ccb90…jpg`, `46e2d2eb…jpg`,
  `cc643689…jpg`, `d968d977…jpg`, `f54fa5cc…png`
- Promo graphics: `e58aa77d…webp`, `cb39484a…png` (promo art — not content photos)
- Base: `https://dafgr1y3h3vlw.cloudfront.net/website-builder/websites/1105/`
- **Juan will supply photos later.** Build every slot on placehold.co at final
  dimensions with final alt text; default tiers stand. Swap in Prompt 8.

### City-page clone zones — FROZEN
Four unique zones per city, everything else shared:
`<!-- CITY-SWAP: intro -->` · `<!-- CITY-SWAP: local-anchors -->` ·
`<!-- CITY-SWAP: why-city -->` · `<!-- CITY-SWAP: faq -->`
The Areas We Serve dropdown (desktop + mobile) is a protected shared zone — mark it and
never modify it during a city clone pass:
`<!-- SHARED ZONE: Areas We Serve dropdown — do NOT modify during city clone pass -->`

---

## Screenshot discipline — FROZEN (tiered)

Code MUST save real PNG files to `./temporary screenshots/` and report the exact path — a
prose description is never a substitute. **Number of rounds is tiered by page type:**

- **Gated template pages — homepage, flagship service, deepest city: 2 comparison rounds.**
  These set the pattern everything inherits; iterate until right.
- **Clones and structural pages — remaining services/cities, about, thank-you: 1 round +
  a click-through.** They inherit an approved parent, so verify, don't re-iterate.
- More rounds only if the 1-round check surfaces a real problem.

(Serve on localhost first — never screenshot a `file:///` path.)

---

## Reference Images — FROZEN
Default: build ORIGINAL pages from this file with high craft — do NOT match a provided
reference. The match-exactly rules apply ONLY when a reference image is explicitly
provided (then: match layout/spacing/type/color, swap placeholder content, don't improve
the design, 2 comparison rounds).

## Local Server / Screenshot Workflow — FROZEN
`node serve.mjs` (root at `http://localhost:3000`, background, don't double-start).
`node screenshot.mjs http://localhost:3000 [label]` → `./temporary screenshots/screenshot-N[-label].png`
(auto-incremented). Read the PNG back and analyze specifics (px sizes, exact hexes,
spacing, alignment, radii, shadows).

## Output Defaults — FROZEN
Self-contained HTML; Tailwind via CDN; `https://placehold.co/WIDTHxHEIGHT` placeholders;
mobile-first responsive.

## Anti-Generic Guardrails — FROZEN
Brand tokens only (never default Tailwind palette). Layered color-tinted shadows (never
flat `shadow-md`). Distinct display + body fonts; tight tracking on large headings,
generous body line-height. Layered radial gradients + SVG-noise grain for depth. Animate
only `transform`/`opacity` (never `transition-all`), spring easing. Every clickable
element has hover + focus-visible + active states. Image overlays + a color-treatment
layer. Intentional spacing tokens. A base→elevated→floating depth system.

---

## Locked Language — FILL per client
- Insurance framing: **N/A — no insurance language anywhere.**
- Warranty / guarantee: no satisfaction guarantee, "100% satisfaction," or damage/loss
  policy anywhere.
- Certification/quality claims: none. No "eco-friendly," "hypoallergenic," "professional
  dry cleaning" as a quality claim, "on-site/in-house dry cleaning," or "same-day" unless
  confirmed. (The dry cleaning SERVICE itself is confirmed — name it freely.)
- Ownership signal: **"family-owned and operated," local Pharr business** (confirmed).
- Experience framing: **none** — no years-in-business or experience figures (unconfirmed).
- Testimonials/reviews: none, and no review count, until the widget is live. Do NOT carry over
  "100% Customer Satisfaction (based on reviews)."
- Delivery claims: no "free delivery," "same-day," or delivery-zone claims until the
  zone, fee, and turnaround are confirmed.
- Pricing: only the Wash, Dry & Fold group (per-lb + comforters/blankets). See Price list.

## Hard Rules — FROZEN
- No invented facts; confirm before filling any `[NEEDS INPUT]`.
- No price / range / "starting at" unless explicitly confirmed here — route pricing intent
  to the quote CTA (applies to copy, FAQ, AND JSON-LD Offer blocks).
  *(Client-specific: the Wash, Dry & Fold prices in the Price list ARE confirmed for
  copy/FAQ on the Wash & Fold and Comforter pages. All other prices: route to "call or
  book online." No prices in JSON-LD beyond `priceRange: "$"`.)*
- No insurance coverage-outcome claims.
- No relationship claim without written confirmation.
- No review widgets/stars/counts/`aggregateRating` until reputation is confirmed.
- Never infer ownership/roles/relationships from social posts.
- Never publish the owner's personal number — GHL tracking number only; grep returns zero
  hits for the personal number before deploy.
- Never promote a client photo into the `hero-background` / `cta-background` slots.
- No readable license plates or privacy-sensitive photos.
- Strip the template's red; no default Tailwind blue/indigo as primary.
- No `transition-all`.
- Follow the tiered screenshot rule above — don't stop after one pass on a *gated template
  page*; a single round + click-through is correct for clones.

## Git Discipline — FROZEN
- Commit/push only when asked; branch first if on the default branch.
- Rename a service/city → update its filename, all hrefs, nav/footer labels, schema,
  title/meta, and breadcrumb together.
- Three-command pre-commit check, no exceptions: `git status`, `git branch`,
  `git remote -v` (the client repo, NOT nexor-template).
- Logical commit separation: CLAUDE.md → own commit; brand_assets → own commit; page
  builds grouped by phase. Never mix client-layer decisions with build work.
- Commit assets immediately on placement (their own commit).
- Set the canonical host as Vercel **Primary on day one**, not at launch.
- Submit the sitemap to GSC as the full canonical URL. Indexing order: services → primary
  city → remaining cities → about. ~10–12 URL inspections/day; spread across days. Re-check
  the homepage canonical in GSC 3–5 days post-launch.

---

## Active Blockers

**Open client input (does NOT block Prompts 0–3):**
- Delivery zone — which of Pharr, McAllen, San Juan, Edinburg, Alamo, Hidalgo get pickup &
  delivery. Needed before Prompt 4 (city pages).

**Launch-blocking (needed before DNS cutover, not before build):**
- CleanCloud booking widget/hosted link (the current `/book` dies when DNS moves)
- GHL tracking number; GHL contact form embed; GHL chat + tracking scripts
- Logo original → palette derivation (or derive from the current-site logo URL above)
- og-image.jpg (1200×630)

**Backfillable (build against placeholders, swap in one pass — Prompt 8):**
- All photos (Juan supplying later), hero/cta backgrounds
- Review widget code (128 reviews confirmed) → then `aggregateRating`

---

## DECISIONS (resolved at strategy lock, Oct 22 2026)

1. Pricing → publish ONLY Wash, Dry & Fold prices ($1.50/lb + comforters/blankets) on the
   Wash & Fold and Comforter pages; nothing else; `priceRange: "$"`.
2. 6th service → Dry Cleaning.
3. Cities → Pharr, McAllen (deepest/template), San Juan, Edinburg, Alamo, Hidalgo. Delivery
   zone pending — sets angle per page only.
4. Booking → CleanCloud for orders/pickups; GHL for contact form, chat, tracking.
5. Domain → https://www.mrsudzrgv.com canonical; old URLs 301'd (see Site Architecture).
6. Phone → GHL tracking number on the site per frozen rule; GBP number left as-is.
7. Promotions → none on the site.
8. Family-owned → publish "family-owned and operated."
9. Language → English only.
10. Gallery → none in v1.
11. Photos → Juan supplies later; default tiers; placeholders until then.
12. Blocker split → as listed above.
13. Reviews → no count/stars/testimonials until the widget is live.
14. FAQ → write fresh per SEO-CONTENT-PROMPT.md from confirmed facts.

Anything not confirmed defaults to Claude's recommendation already written above; Juan will
call out changes later as `CLAUDE.md` edits.
