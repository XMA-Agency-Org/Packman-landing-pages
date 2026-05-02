# Packman site — v6

Static HTML, deploy-ready for Vercel. Conversion-focused landing pages with VSLs, problem/solution narrative, math reveals, before/after comparisons, and testimonials — built in the cream/lime brand design.

## What changed in v6

- ✅ **Real landing pages, not a website clone** — every page has VSL placeholders, pain statements, math/numbers, comparisons, social proof, and urgency CTAs
- ✅ **Two new audience-specific landing pages** — `/for-brands` (200+ orders/mo) and `/for-startups` (first-time sellers) — each with their own VSL, math, before/after, and testimonial
- ✅ **VSL components** — dark navy 16:9 cards with lime play buttons, eyebrow tags, timestamp badges, and money-quote captions
- ✅ **Math reveal cards** — equations in mono font (`200 × AED 199 AOV = AED 39,800`) plus coral RTO-loss callouts
- ✅ **Before/After comparisons** — side-by-side cards (paper vs ink) with itemized lists and totals
- ✅ **Dashboard mocks** — stylised previews with browser-chrome dots, real orders, SKUs, status badges, AED totals
- ✅ **Testimonials** — 3 sellers across UAE, KSA, Oman with avatars, names, and roles
- ✅ **Pain section** — 4 friction stat cards (9 tools, 3h lost, 20% RTO, 5 tabs) in coral red
- ✅ **48-hour timeline** — vertical timeline with lime dots and mono time labels (`/for-startups`)
- ✅ **Old-way-vs-new-way cost comparison** — `AED 148,800` to launch the old way vs `AED 400/month` with Packman
- ✅ Pricing structure preserved — Monthly / Yearly toggle per country
- ✅ Real packman.ai content preserved — partners, FAQs, contact channels, offices
- ✅ EN/AR toggle still works site-wide with proper RTL

## Routes

### Country home pages (with full landing-page flow)
| URL      | Country  | Currency |
|----------|----------|----------|
| `/`      | Generic  | AED      |
| `/uae`   | UAE 🇦🇪   | AED      |
| `/ksa`   | KSA 🇸🇦   | SAR      |
| `/oman`  | Oman 🇴🇲  | OMR      |

### Audience landing pages (NEW)
| URL              | For                                | Hook                          |
|------------------|------------------------------------|-------------------------------|
| `/for-brands`    | Brands doing 200+ orders/month     | "Let's talk math."            |
| `/for-startups`  | First-time sellers                 | "Live in 48 hours."           |

### Pricing
| URL                | Monthly | Yearly  | Save |
|--------------------|---------|---------|------|
| `/pricing-uae`     | AED 400 | AED 3,600 | 25% |
| `/pricing-ksa`     | SAR 400 | SAR 3,600 | 25% |
| `/pricing-oman`    | OMR 40  | OMR 360   | 25% |

### Auxiliary
| URL          | Content                                             |
|--------------|-----------------------------------------------------|
| `/partners`  | 8 ecosystem partners + 3 payment gateways           |
| `/faqs`      | 15 grouped FAQs                                     |
| `/contact`   | Form + 4 channels + 3 office cards                  |

## Home page flow

1. **Hero** — `Sell anything, anywhere. Packman builds your store from one photo.` + camera input + Start free CTA
2. **VSL #8 · The 90-sec hook** — dark video card with lime play button + money-quote underneath
3. **The mess behind the scenes** — `What kills most brands isn't competition. It's the chaos.` + 4 coral pain stats
4. **The platform · 4 modules** — alternating layout with dashboard mocks (Orders, AI Content, Inventory, Shipping)
5. **The AI team** — 8 AI manager cards (hover invert to dark)
6. **What sellers say** — 3 testimonials (Layla H. Dubai, Faisal A. Riyadh, Maitha S. Muscat)
7. **Pick your path** — 2 path cards linking to `/for-brands` and `/for-startups`
8. **Pricing teaser** — `One plan. Three countries.` + See pricing CTA
9. **Final CTA** — dark navy block: `Your first order ships in 48 hours.`

## /for-brands flow

1. Hero — `Doing 200+ orders a month? Let's talk math.`
2. VSL #1 — `9 tools to 1` with Maitha S. quote
3. **The math** — green math card (`200 × AED 199 = AED 39,800`) + coral RTO-loss card (`AED 7,960 gone`)
4. **The switch** — `9 tools. One Packman.` before/after with itemized monthly costs (`AED 1,865 vs AED 400`)
5. Long-form testimonial from Maitha S.
6. Final CTA — `Stop bleeding revenue.`

## /for-startups flow

1. Hero — `Your first store, your first sale — live in 48 hours.`
2. VSL #4 — `48-hour launch` with Faisal A. quote
3. **The 48-hour timeline** — 6 steps (0min sign up → 48hr first order → next day ship)
4. **Old way vs new way** — `AED 148,800` to launch (warehouse, dev team, courier accounts, etc.) vs `AED 400/month`
5. Long-form testimonial from Faisal A.
6. Final CTA — `Your first sale, this week.`

## Design tokens

| Token        | Value     | Usage                                        |
|--------------|-----------|----------------------------------------------|
| `--ink`      | `#0E1820` | Body text, dark cards, VSL background        |
| `--olive`    | `#788938` | Highlighted text, eyebrows, links            |
| `--volt`     | `#D2F801` | Primary CTAs, play buttons, math results     |
| `--coral`    | `#E85D45` | Pain numbers, before-side X marks, RTO card  |
| `--paper`    | `#FFFFFF` | Pill nav, cards, dashboard mocks             |
| `--soft`     | `#F0F2E3` | Light pill buttons (Reject, Login, Toggles)  |
| `--olive-bg` | `#ECF1CB` | Country tags, AI icon backgrounds, bonus card|

## Bilingual

Every text element has `data-en="..." data-ar="..."` attributes. The EN/AR toggle in the nav swaps text site-wide, sets `dir="rtl"`, loads IBM Plex Sans Arabic, and persists choice in localStorage. The pricing toggle, billing translations, and dashboard mock labels all flip correctly.

## Mobile

- Nav collapses to logo + Launch your store + EN/AR
- 4-column grids → 2 columns
- 3-column grids → 1 column
- Compare grid stacks vertically
- VSL play button shrinks
- Math card padding shrinks
- Cookie banner stacks

## Deploy

Drag the `packman/` folder onto https://vercel.com/new — that's it. `vercel.json` enables `cleanUrls`.

## Local preview

```bash
cd packman
python3 -m http.server 8000
# open http://localhost:8000
```

## Source

Build script: `build_v6.py` in the project root. Run `python3 build_v6.py` to regenerate.

```
packman/
├── README.md
├── vercel.json
├── index.html              ← home (full landing page)
├── uae/index.html
├── ksa/index.html
├── oman/index.html
├── for-brands/index.html   ← NEW: brands landing page with VSL #1
├── for-startups/index.html ← NEW: startups landing page with VSL #4
├── pricing/index.html
├── pricing-uae/index.html
├── pricing-ksa/index.html
├── pricing-oman/index.html
├── partners/index.html
├── faqs/index.html
├── contact/index.html
└── assets/
    ├── logo-mark-navy.png
    ├── logo-mark-volt.png
    ├── logo-full-navy.png
    └── logo-full-volt.png
```
