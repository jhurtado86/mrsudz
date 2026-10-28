# Mr. Sudz Laundromat — Build Report

**Branch:** `build` (not pushed) · **Built:** Oct 27, 2026 · **Authority:** `CLAUDE.md` + `SEO-CONTENT-PROMPT.md`

Every page is self-contained HTML (Tailwind CDN, `/brand.css` tokens) and inherits the approved homepage's
visual system: same nav, footer, final CTA, Visit panel, and service cards.
Screenshots are in `./temporary screenshots/` (git-ignored, local only). Serve with `PORT=3300 node serve.mjs`.
Ports 3000 and 3100 on this machine belong to other projects.

---

## 1. What was built

| Page | File | Photo slots | JSON-LD | Final screenshot(s) |
|---|---|---|---|---|
| Homepage | `index.html` | 3 body + hero | DryCleaningOrLaundry (full entity) | `screenshot-1-homepage-final.png`, `screenshot-2-homepage-mobile.png` |
| Wash, Dry & Fold (flagship / service template) | `services/wash-and-fold.html` | 5 + hero | Service + FAQPage (7) + Breadcrumb | `screenshot-2-wash-and-fold.png`, `screenshot-2-wash-and-fold-mobile.png` |
| Laundry Pickup & Delivery (secondary push) | `services/laundry-pickup-delivery.html` | 3 + hero | Service + FAQPage (6) + Breadcrumb | `screenshot-1-laundry-pickup-delivery.png`, `-mobile.png` |
| Self-Service Laundry | `services/self-service-laundry.html` | 2 + hero | Service + FAQPage (6) + Breadcrumb | `screenshot-1-self-service-laundry.png` |
| Ironing & Steaming | `services/ironing-steaming.html` | 2 + hero | Service + FAQPage (6) + Breadcrumb | `screenshot-2-ironing-steaming.png` |
| Comforter & Bedding Cleaning | `services/comforter-cleaning.html` | 2 + hero | Service + FAQPage (7) + Breadcrumb | `screenshot-1-comforter-cleaning.png` |
| Dry Cleaning | `services/dry-cleaning.html` | 2 + hero | Service + FAQPage (6) + Breadcrumb | `screenshot-2-dry-cleaning.png` |
| McAllen (deepest / city template) | `areas/mcallen.html` | 1 + hero | LocalBusiness `@id` ref + FAQPage (5) + Breadcrumb | `screenshot-3-mcallen.png`, `screenshot-1-mcallen-mobile.png` |
| Pharr (home city) | `areas/pharr.html` | 1 + hero | same pattern | `screenshot-2-pharr.png` |
| San Juan | `areas/san-juan.html` | 1 + hero | same pattern | `screenshot-2-san-juan.png` |
| Edinburg | `areas/edinburg.html` | 1 + hero | same pattern | `screenshot-2-edinburg.png` |
| Alamo | `areas/alamo.html` | 1 + hero | same pattern | `screenshot-2-alamo.png` |
| Hidalgo | `areas/hidalgo.html` | 1 + hero | same pattern | `screenshot-2-hidalgo.png` |
| About | `about.html` | 2 + hero | Business `@id` ref + Breadcrumb | `screenshot-1-about.png`, `screenshot-1-about-mobile.png` |
| Thank-you | `thank-you.html` | hero only | none (noindex) | `screenshot-1-thank-you.png` |

**Screenshot rounds:**
- **Gated pages** (homepage, flagship, McAllen): 2+ correction rounds each, plus a strict-reviewer round.
- **Clones:** 1 round, plus a click-through link check.

The Phase 7 footer tweak (dead links replaced with "Open daily, 7am–10pm") landed after most inner-page screenshots. Only that one bottom-right line differs from what the screenshots show.

**Commits on `build` (oldest → newest):** `727ebe9` CLAUDE.md lock · `8eb8b0b` logo · `3c91098` palette hexes ·
`f7e2f61` slug renames · `bcce16f` assets README · `1e1fdda` package name · `0b43c88` canonical host · `3269e66` email ·
`e2cb565` screenshot tool · `145620b` brand.css palette · `16a4996` homepage · `5c8b5d7` hero type ·
`c428d1f` Phase 2 · `6edcd4e` Phase 3 · `d8d895e` Phase 4 · `cdcd3cd` Phase 5 · `de8a7c2` Phase 6 · `fb6037c` Phase 7 ·
`81364e1` [VERIFY] comments · this report.

---

## 2. Audit results

### Passing (verified by script)
- **Canonical vs sitemap vs og:url:** canonical == sitemap `<loc>` == `og:url` on all 14 indexable pages. The diff is empty, and every URL is on `https://www.mrsudzrgv.com`.
- **Thank-you trio:** `noindex, nofollow` meta ✓, excluded from `sitemap.xml` ✓, `Disallow: /thank-you.html` in `robots.txt` ✓.
- **Metadata:**
  - Every page has a unique `<title>` (all ≤ 57 characters) and a unique description (all ≤ 152).
  - Every page also has keywords, robots, viewport, `lang="en"`, and the full Open Graph and Twitter tag set.
- **Headings:** exactly one `<h1>` per page and no skipped levels.
- **JSON-LD:**
  - **Homepage:** `DryCleaningOrLaundry` with PostalAddress, daily 07:00–22:00 hours, 6-city `areaServed`, `priceRange "$"`, and `sameAs`. Its offer catalog lists 6 services, matching the 6 live service pages. There's no `aggregateRating`.
  - **Service pages:** 3 blocks each, with 6 or more FAQPage Q&As.
  - **City pages:** 3 blocks each. The business block references the homepage `@id`, `areaServed` is that city only, and each has 5 or more FAQPage Q&As.
  - No prices appear anywhere in JSON-LD.
- **Internal links:** every root-relative link and every `/#anchor` target resolves. All `href="#book"` CTAs carry the `CLEANCLOUD BOOKING EMBED` comment.
- **Zero hits** for `yourbusiness`, `service-one…six`, `city-one…six`, "Your Business Name", template color hexes, red, `transition-all`, Barlow, and the current public number (956) 232-9274.
- **Copy:**
  - The banned-word list (SEO-CONTENT-PROMPT.md) and the forbidden-claims list (quote/estimate, same-day, free, insured, guarantee, eco, turnaround, coin, reviews/stars, etc.) both come back clean in visible text on every page.
  - Prices appear only on `wash-and-fold.html` and `comforter-cleaning.html`.
- **City pages:**
  - The shared zones are byte-identical across all 6 city pages.
  - Unique content against each page's closest sibling page is 37–46%.

### Fixed during the build/audit
- **Sitemap dates:** `<lastmod>` was still the template's `2026-06-10`; now `2026-10-27`.
- **Footer Privacy Policy / Terms:** briefly removed as dead links, then restored (Oct 28) on all 15 pages as `href="#"` with `<!-- GHL PRIVACY POLICY URL -->` / `<!-- GHL TERMS URL -->` TODO comments. The policies are hosted in GHL, and these swap in one pass with the other GHL codes (§6).
- **Low-contrast body text on dark:** the template used `muted-light` for body text on navy (3.62:1). It now uses the new `--color-silver` token (6.88:1).
- **Prices in FAQPage schema:** the FAQPage blocks were mirroring price answers. Priced Q&As now stay in the visible FAQ only.
- **Hours wrapping:** the hours readout wrapped; the hero was misaligned with the nav; the hero overlay was too light. All fixed in homepage round 1.
- **Highway names breaking:** "I-69C" broke at its hyphen in the Edinburg hero. Highway names in visible copy are now no-wrap.
- **Copy overclaims removed:**
  - "Large-capacity washers" (machine size isn't confirmed).
  - "Notes on delicate items" (implies special delicate handling).
  - "Under one roof" (could imply in-house dry cleaning).
  - City headings implying customer behavior, such as "Why Alamo families make the drive."
  - "Catch the game" (implies sports on the TVs).
  - A pickup band on the dry cleaning and ironing pages that implied those garments can go through pickup.
- **Wrong fact caught before writing:** I nearly called McAllen "the biggest city in the Valley." Brownsville is larger, so it never went into the copy.

### Still open (not fixable without inventing facts)
- **`[NEEDS INPUT]` comment markers on 15 files:**
  - Every phone placeholder: `(555) 000-0000` / `+15550000000`, including the homepage schema `telephone`.

  These are deliberate open-item flags, not template residue. The phone placeholder is a hard launch gate (below).
- **Placeholder images:** `og:image` / `twitter:image` and every photo, hero and CTA background use placehold.co at final dimensions (see §6).
- **Rich Results Test:** not run. It needs the site at a public URL. Validate at `search.google.com/test/rich-results` after deploy.
- **Owner's-first-name gate:** ✓ passed Oct 28: 0 case-insensitive hits across all 15 pages and every other source file. The name was supplied for the check only and isn't recorded in this report or any page.
- **Redirects:** no `vercel.json` yet. The 4 locked 301s (`/pricing`, `/promotions`, `/contact`, `/book`) go in at cutover, as planned.

### LAUNCH GATE — must all be zero before DNS cutover
Run from the repo root. Each command must print `0`:

```sh
grep -rEo '\(555\) ?000-0000' --include='*.html' . | wc -l        # placeholder phone (display)    — currently 79
grep -rEo '\+?1?5550000000' --include='*.html' . | wc -l           # placeholder phone (tel:/schema) — currently 41
grep -rio '<owner first name>' --include='*.html' . | wc -l         # owner's first name, case-insensitive — currently 0
grep -rc 'href="#book"' --include='*.html' . | grep -v ':0' | wc -l # pages with unswapped CleanCloud links
grep -rc 'href="#"' --include='*.html' . | grep -v ':0' | wc -l     # pages with unswapped GHL Privacy/Terms links
```

The phone gate is expected to fail until the GHL tracking number arrives; it's listed so launch can't happen with the placeholder.

---

## 3. `[VERIFY]` local anchors

Only verified anchors are visible on the pages. Unconfirmed candidates are left as HTML comments:

| File:line | Flag |
|---|---|
| `areas/pharr.html:808` | Is the store near the W. Sam Houston Blvd. / Cage Blvd. intersection? (The TDLR records hint at "Sam Houston Blvd. (Cage Blvd., Bus. US…)" but don't confirm it.) |
| `areas/hidalgo.html:808` | Best road from Hidalgo north to W. Sam Houston Blvd. (S. Cage Blvd. / US 281 / Spur 115?). Not named on the page. The visible copy says only "head north" plus Get Directions. |

**Anchors used visibly, with their sources:**

| Anchor | Pages | Source |
|---|---|---|
| I-2 / US 83 through McAllen, Pharr and San Juan | McAllen, San Juan, Alamo | Wikipedia / AARoads Interstate 2 |
| Business 83 as McAllen's main east–west road, continuing into Pharr and passing through Alamo and San Juan | McAllen, San Juan, Alamo | Wikipedia, US 83 Business (McAllen) |
| I-69C / US 281 from Edinburg to I-2 in Pharr | Edinburg, Pharr | Wikipedia / AARoads I-69C |
| UTRGV Edinburg campus, 1201 W. University Dr.; Edinburg as county seat | Edinburg | UTRGV listings; San Juan, TX Wikipedia |
| San Juan bordered by Pharr (west) and Alamo (east); Basilica of Our Lady of San Juan del Valle | San Juan | Wikipedia; TX House resolution |
| FM 907 (Alamo Road) | Alamo | Business 83 article |
| McAllen–Hidalgo–Reynosa International Bridge | Hidalgo | Wikipedia |
| PSJA ISD shared by Pharr, San Juan and Alamo | San Juan, Alamo | PSJA ISD listings |

No drive times or mileages are stated anywhere.

---

## 4. Judgment calls where CLAUDE.md was silent

**Design system**
1. **Typography:** Archivo (headings; wide only on small labels and the hours readout), Nunito (body), and IBM Plex Mono (hours and status data only) replaced the template's Barlow. You approved this on the homepage, and the hero was lightened to weight 700 at your request.
2. **Logo chip:** `logo.png` is RGB on solid white with no transparency, so it sits in a white rounded chip in the nav and footer rather than directly on navy.
3. **Two new color tokens:**
   - `--color-silver` (#C3CED9) for secondary text on dark.
   - `--color-accent-bright` (#6CC0EA) for small accent text on navy.
4. **Contrast rules:** text on sky-blue buttons is always ink (white fails at 2.63:1), and small accent text on white uses `accent-deep`.
5. **Signature element:** a Visit panel with a live "Open now · until 10 PM" status, computed in America/Chicago time from the confirmed hours. It's the homepage's signature and is reused on the city and About pages.

**SEO and schema**
6. **Prices kept out of FAQPage schema:** CLAUDE.md allows no prices in JSON-LD, so priced Q&As show on the page but aren't in FAQPage. Google allows the schema to cover a subset of the visible FAQ.
7. **Service schema `areaServed`:** lists all 6 cities as the market area. It makes no delivery claim; the delivery copy everywhere is "book online to check pickup availability at your address."
8. **No FAQPage on the homepage:** CLAUDE.md only calls for FAQPage on service and city pages.
9. **Service page titles:**
   - The flagship leads with "Wash & Fold Laundry Service" (collision rule).
   - Comforter uses the shorter "Comforter Cleaning in Pharr, TX" in its title.
   - Dry Cleaning is "Dry Cleaning **Drop-Off**", so it never implies in-house cleaning.
10. **Pharr city page** targets "Pharr Laundry Services, Close to Home" with storefront framing, so it doesn't compete with the homepage's "Laundromat in Pharr, TX."
11. **Other city titles** use "Laundromat & Laundry Service Near [City], TX", the walk-in angle, since the delivery zone is unknown. CLAUDE.md's "Laundry Service & Delivery in [City]" pattern waits for the zone answer.
12. **Why-city headings** are written as "Why It's Worth the Drive from…" or "Why Mr. Sudz Works for…" rather than claiming that city's residents choose us.
13. **City hero and metadata** differ per city outside the four CITY-SWAP zones. That's unavoidable; everything else outside the zones is byte-identical.

**CTAs and copy**
14. **Self-Service hero CTAs:** primary is Get Directions (it's a walk-in service) and Book a Pickup is secondary. The Pickup & Delivery hero pairs Book a Pickup with Call, since directions don't fit that service.
15. **"Newest service":** the Pickup & Delivery page calls it the newest service at Mr. Sudz, based on the current site's "now available / new" wording.
16. **Thank-you copy** says "Someone from Mr. Sudz will get back to you," with no response time.
17. **Contact email:** swapped `hello@yourbusiness.com` → `info@mrsudzrgv.com` (confirmed in CLAUDE.md).

**Process and tooling**
18. **How the inner pages were built:** a generator in my scratchpad, not committed, pulled the shared partials verbatim from `index.html`. Edit the HTML files directly from now on; they're the source of truth.
19. **Screenshot tool:** `screenshot.mjs` now launches `headless: 'shell'`, because Chrome's new headless mode timed out on every capture on this Mac.

---

## 5. QUESTIONS FOR JUAN (most important first)

1. **Delivery zone.** Which of Pharr, McAllen, San Juan, Edinburg, Alamo and Hidalgo get pickup & delivery? This is the one open strategy input. Once it's answered, the in-zone city pages switch to delivery-led titles, heroes and FAQs.
2. **CleanCloud booking link or embed code.** Every "Book a Pickup" button (`href="#book"`, 4–7 per page) swaps in one pass. The current `/book` stops working at DNS cutover.
3. **GHL tracking number.** It replaces `(555) 000-0000` / `+15550000000` on every page and in the homepage schema.
4. ~~Owner's first name for the pre-deploy grep~~ — **answered Oct 28.** The check passed with 0 hits; the name isn't recorded here.
5. ~~Privacy Policy and Terms~~ — **answered Oct 28.** They're hosted in GHL. The footer links are restored with TODO comments, and the URLs are listed in §6.
6. **GHL contact form, chat widget and tracking script.** The slots are in place.
7. **Pickup & delivery details.** Is any of this confirmed for publishing: fees, minimums, turnaround, pickup windows? Right now every page says only "book online to check pickup availability / pickup times."
8. **What pickup accepts.** Can ironing, comforters and dry cleaning go through pickup, or only wash & fold?
9. **Turnaround for wash & fold and dry cleaning.** Current copy says "ask our attendant when you drop off."
10. **How customers pay at the machines.** It's unconfirmed, so it's not mentioned anywhere.
11. **Machine sizes and counts.** Is there a large-capacity washer for self-serve comforters? Not claimed.
12. **Store location detail.** Is it near a landmark or cross street (Cage Blvd.?), and is there parking? See the [VERIFY] flags.
13. **Attendant hours.** Copy says "friendly on-site attendants" without claiming every hour.
14. **GBP categories.** Confirm the working set: Laundromat (primary), Laundry Service, Dry Cleaner.
15. **Photos.** Do we have consent and originals for the current-site CleanCloud photos, if any get reused?

---

## 6. ASSETS STILL NEEDED

| Asset | Where it goes | Spec |
|---|---|---|
| `brand_assets/hero-background.jpg` | Hero on every page (OFF-LIMITS slot) | 1920×1080, purpose-made — never a content photo |
| `brand_assets/cta-background.jpg` | Final CTA on every page except thank-you (OFF-LIMITS slot) | 1920×1080, purpose-made |
| `brand_assets/og-image.jpg` | `og:image` / `twitter:image` on every page | 1200×630 |
| Original logo, ideally transparent PNG or SVG | Nav and footer chip; re-derive palette hexes | Current file is the 300×151 site logo on white |
| Content photos, 4:3 at 1200×900 (27 slots total) | **12 placed** (Oct 28 batch 1, see `brand_assets/README.md`). **8 more** are ready once the approved batch-2 files (storefront, carts by the window, front counter) are saved into the repo. **7 still have no matching photo:** a laundry bag (Wash & Fold, Pickup & Delivery), ironing ×2, comforters/blankets ×2, dry cleaning on hangers ×1 | Also needed: full-size originals of the three 680×510 photos. Exclusions: no customer faces, no recognizable garments, no plates |
| CleanCloud booking URL or embed | Every `href="#book"` | Launch-blocking |
| GHL tracking number | Every phone link + homepage schema | Launch-blocking |
| GHL contact form embed | `index.html` `#contact` | Launch-blocking |
| GHL chat widget + external tracking scripts | Before `</body>` / in `<head>` on every page | Launch-blocking |
| GHL review widget (128 reviews confirmed) | Commented slot on `index.html`. When live: un-comment it, re-enable the nav/footer Reviews links, and add `aggregateRating` in the same commit | Backfill |
| GHL Privacy Policy URL | Footer `<!-- GHL PRIVACY POLICY URL -->` on every page (`href="#"`) | Swap with the other GHL codes |
| GHL Terms URL | Footer `<!-- GHL TERMS URL -->` on every page (`href="#"`) | Swap with the other GHL codes |
| `vercel.json` with the 4 locked 301s + www as Primary domain | Repo root | At cutover |
