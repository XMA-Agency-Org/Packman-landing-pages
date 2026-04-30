# Packman site

Static HTML, deploy-ready for Vercel.

## Routes

| URL                | File                       |
|--------------------|----------------------------|
| `/`                | `index.html`               |
| `/pricing`         | `pricing/index.html`       |
| `/for-brands`      | `for-brands/index.html`    |
| `/for-startups`    | `for-startups/index.html`  |
| `/ar`              | `ar/index.html`            |
| `/uae-oman`        | `uae-oman/index.html`      |

## v3 changes

### 1. Edgy non-rectangular shapes (everywhere)
Every visual container uses CSS `clip-path` polygons — no rounded rectangles.

| Element                          | Shape                                   |
|----------------------------------|-----------------------------------------|
| Buttons (`.btn-primary/ghost`)   | Forward-chevron arrow (cut right edge)  |
| All cards (`bg-paper.border` etc.) | Cut top-right corner (24px)           |
| VSL hero containers              | Big cut bottom-right (48px) + grape drop-shadow |
| Dashboard mocks (`.mock-dashboard`) | Cut bottom-right (36px) + ink drop-shadow |
| Featured pricing card            | Diagonal cuts (TR + BL) when `.edge-diag` |
| "MOST POPULAR" tag               | Rotated -3deg                           |

Box-shadows that wouldn't survive `clip-path` were swapped to `filter: drop-shadow()` so the offset shadow follows the cut shape.

### 2. Universal currency switching
Every money number on every page (94 references) updates instantly when the user clicks **UAE / KSA / Oman** in the footer. Choice persists across pages via `localStorage`.

| Region | Currency | Anchor              |
|--------|----------|---------------------|
| UAE    | AED      | base                |
| KSA    | SAR      | AED 3,900 → SAR 4,000 |
| Oman   | OMR      | AED 3,900 → OMR 400   |

Conversion: `1 AED = 1.0256 SAR = 0.1026 OMR`.

Rounding tiers:
- ≥ 100 → nearest 10 (clean headline numbers like AED 1,100 / SAR 1,130 / OMR 110)
- 10–99 → nearest 5 (preserves visual differentiation between effective rates)
- < 10 → nearest 1 (small fees like shipping)
- Source amounts with decimals (dashboard mock orders like AED 239.65) preserve 2-decimal precision

What switches:
- Plan tiers, effective rates, savings (across all 6 pages)
- Account-management add-ons, storage tiers (pricing page)
- Revenue / cost-comparison numbers (for-brands math: AED 199 AOV, AED 39,800/mo, AED 7,960 lost; for-startups old-way breakdown: AED 60,000 + 15,000 + 40,000 + 8,000 + 4,800 + 15,000 + 6,000 = AED 148,800)
- Dashboard mock orders, including OMR-priced Oman side on the bilingual UAE-Oman page (OMR 22.40 / 17.90 / 38.75 → switch with toggle)
- Arabic-numeric mention "٧,٩٦٠ درهم" on the AR page (normalized to AED 7,960 then wired)
- VAT threshold (AED 375,000), shipping fees (AED 9, AED 25), and all other money references
- Column headers on the bilingual dashboard mock (`UAE · AED` / `OMAN · OMR` → both swap to current currency)

### 3. Logos installed
Real logo PNGs replace the previous wordmark placeholders.
- Nav: navy mark + "packman" wordmark (or "باكمان" on `/ar`)
- Dark footer: volt mark + cream wordmark
- Light footer (uae-oman page): navy mark + ink wordmark

### 4. Folder routing
Each page lives in its own folder so URLs are clean (`/pricing` → `pricing/index.html`). `vercel.json` enables `cleanUrls`.

## Deploy

Drag the `packman/` folder onto https://vercel.com/new — that's it.

## Local preview

```bash
cd packman
python3 -m http.server 8000
# open http://localhost:8000
```

## Source

Build script: `build_v3.py` (in the project root, not in this folder).
Source HTML: `source/01-home.html` through `06-uae-oman.html`.
Re-run `python3 build_v3.py` to regenerate.
