# Packman site — v6.1

Static HTML, deploy-ready for Vercel. Mobile-optimised landing pages with VSLs and conversion mechanics.

## What changed in v6.1 (your mobile feedback)

### English version fixes
- ✅ **Nav layout on mobile fits properly** — packman logo + "e-commerce for entrepreneurs" tagline + Launch your store + EN/AR all fit cleanly on the pill bar at 390px width. No overflow, EN/AR is now compact and well-positioned.
- ✅ **04 Shipping reframed — Packman ships, no third party** — removed all Buraq/Aramex references. New section reads "Your shipping team. On payroll." with copy: "Packman runs the warehouses, packs the orders, and delivers them with our own fleet. No third-party hand-offs, no missing parcels, no finger-pointing." The dashboard mock now shows `Packman Express` and `Packman Standard` as our own courier tiers.
- ✅ **AI managers stack 1-per-row on mobile** — no more 2-column squeeze. Each manager card on its own line for clean scrolling.
- ✅ **Hero CTAs work properly** — under the "I want to sell..." input, you now get two CTAs:
  - `Schedule a demo` (light pill, books a call)
  - `Launch your store` (dark navy, goes to pricing)
  - On mobile they stack vertically full-width. On desktop they sit side-by-side. No more cramped Launch button.

### Arabic version fixes
- ✅ **Logo + tagline + AR/EN all fit decently** — the logo lockup with "التجارة الإلكترونية لرواد الأعمال" tagline, "أطلق متجرك" CTA, and the AR/EN toggle all align cleanly in the pill nav.
- ✅ **Single-column mobile layout** — every card section (AI managers, AI tiles, region grid, partners grid, payment gateways, before/after compare, what's included) now stacks 1-per-row on mobile, no 2-up squeeze.
- ✅ **AR persistence across pages** — when you tap AR, the choice is saved in localStorage and applies INLINE in the `<head>` of every subsequent page **before first paint**. No flash of English. Stays AR if you refresh, navigate, open in a new tab.

## Routes

### Country home pages (with full landing-page flow)
| URL      | Country  | Currency |
|----------|----------|----------|
| `/`      | Generic  | AED      |
| `/uae`   | UAE 🇦🇪   | AED      |
| `/ksa`   | KSA 🇸🇦   | SAR      |
| `/oman`  | Oman 🇴🇲  | OMR      |

### Audience landing pages
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

1. **Hero** — `Sell anything, anywhere. Packman builds your store from one photo.` + camera input + Start free CTA + Schedule a demo / Launch your store dual CTA below
2. **VSL #8 · The 90-sec hook** — dark video card with lime play button + money-quote underneath
3. **The mess behind the scenes** — `What kills most brands isn't competition. It's the chaos.` + 4 coral pain stats
4. **The platform · 4 modules** — alternating layout with dashboard mocks (Orders, AI Content, Inventory, **Shipping with Packman fleet**)
5. **The AI team** — 8 AI manager cards (1-per-row on mobile)
6. **What sellers say** — 3 testimonials (Layla H. Dubai, Faisal A. Riyadh, Maitha S. Muscat)
7. **Pick your path** — 2 path cards linking to `/for-brands` and `/for-startups`
8. **Pricing teaser** — `One plan. Three countries.`
9. **Final CTA** — `Your first order ships in 48 hours.`

## Bilingual

Every text element has `data-en="..." data-ar="..."` attributes. The EN/AR toggle:
- Swaps text site-wide via JS
- Sets `dir="rtl"` on `<html>`
- Loads IBM Plex Sans Arabic font
- **Persists in localStorage**
- **Applies INLINE in `<head>` on every page load** so there's no flash of English when navigating

## Mobile

Below 768px breakpoint:
- Nav: logo (with shrunk tagline) + Launch your store + EN/AR fit on one pill row
- All grids collapse to **single column**
- Hero dual CTAs stack vertically full-width
- Compare cards stack vertically
- Pricing CTA row stacks
- Cookie banner stacks vertically
- VSL play button shrinks
- Math card padding shrinks

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
├── index.html              ← home
├── uae/index.html
├── ksa/index.html
├── oman/index.html
├── for-brands/index.html
├── for-startups/index.html
├── pricing/index.html
├── pricing-uae/index.html
├── pricing-ksa/index.html
├── pricing-oman/index.html
├── partners/index.html
├── faqs/index.html
├── contact/index.html
└── assets/  (logos)
```
