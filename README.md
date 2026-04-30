# Packman site

Static HTML, deploy-ready for Vercel. Drag the folder onto vercel.com/new — done.

## What's new in this build

**1. Real logo installed.** The navy mark sits in the nav next to "packman" wordmark.
Volt mark in dark footers. All four logo files are in `/assets/` (with transparent backgrounds).

**2. Rounded edges.** Buttons radiused at 12px (was sharp 2px). Cards and dashboard
mocks at 16px. Visual containers across the site feel softer without going
pill-shaped.

**3. Currency switching by region.** The footer has three buttons — UAE, KSA, Oman.
Click any of them and every price on the page swaps:
- UAE → AED (e.g. AED 3,900/yr)
- KSA → SAR 4,000/yr
- Oman → OMR 400/yr
Choice persists across pages via localStorage.

Numbers rounded to the nearest 10 in each currency. Yearly anchor: AED 3,900 →
SAR 4,000 → OMR 400 (per your spec).

## Folder structure

```
packman/
├── index.html               → /
├── pricing/index.html       → /pricing
├── for-brands/index.html    → /for-brands
├── for-startups/index.html  → /for-startups
├── ar/index.html            → /ar
├── uae-oman/index.html      → /uae-oman
├── assets/                  ← logos already here, drop fonts in
└── vercel.json
```

## Optional — Arabic font

Drop these into `/assets/` for the Avenir Arabic brand font:
- `avenir-arabic-book.otf`
- `avenir-arabic-black.otf`

Without them, Arabic text falls back to IBM Plex Sans Arabic (loaded via Google
Fonts). Still readable, just not the brand font.

## Deploy

**Easiest:** drag the `packman/` folder onto https://vercel.com/new

**CLI:** `cd packman && vercel deploy --prod`

**Local preview:** `python3 -m http.server 8000` then open http://localhost:8000
