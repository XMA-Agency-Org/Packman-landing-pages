# Packman site — v5

Static HTML, deploy-ready for Vercel. Content sourced from packman.ai, redesigned in the cream/lime brand.

## What changed in v5

- ✅ **EN/AR toggle now works** — clicking AR switches the entire site to Arabic with proper RTL layout. Choice persists across pages via localStorage.
- ✅ **Pricing simplified to 2 options** (Monthly / Yearly), per-country:
  - 🇦🇪 UAE: AED 400 / month or AED 3,600 / year (save 25%)
  - 🇸🇦 KSA: SAR 400 / month or SAR 3,600 / year (save 25%)
  - 🇴🇲 Oman: OMR 40 / month or OMR 360 / year (save 25%)
- ✅ **Real content from packman.ai** — hero, "Packman is simple" (4 steps), "Run ads without becoming a marketer", "Launch content without a content team", "Your warehouse, without owning one" (warehouses + 160+ countries), "Hire your AI managers" (8 specialists)
- ✅ **Partners restructured** — government & ecosystem partnerships preserved as informational cards (Dubai Economy, RAKDED, Abu Dhabi Chamber, Ministry of Education Kidspreneur, World Government Summit, Harvard, etc.), plus a separate **Payment Gateways** section showing only Tabby, Tamara, and Apple Pay
- ✅ **Real contact info** — Sales / Support / Partnerships / Careers channels with proper packman.ai email addresses, working contact form, three-office grid (Dubai · Riyadh · Muscat)
- ✅ **Real FAQs** — 5 grouped sections (Getting started, Pricing & billing, Fulfillment & shipping, Payments, Support & account) with content rewritten from packman.ai

## Routes

### Country home pages
| URL      | Country  | Currency |
|----------|----------|----------|
| `/`      | Generic  | (none)   |
| `/uae`   | UAE 🇦🇪   | AED      |
| `/ksa`   | KSA 🇸🇦   | SAR      |
| `/oman`  | Oman 🇴🇲  | OMR      |

### Pricing pages
| URL                | Currency | Monthly | Yearly  |
|--------------------|----------|---------|---------|
| `/pricing`         | AED      | 400     | 3,600   |
| `/pricing-uae`     | AED      | 400     | 3,600   |
| `/pricing-ksa`     | SAR      | 400     | 3,600   |
| `/pricing-oman`    | OMR      | 40      | 360     |

Each pricing page has a country switcher pill (UAE/KSA/Oman) and a Monthly/Yearly toggle. The big number updates live when the toggle is clicked.

### Auxiliary pages
| URL          | Content                                                  |
|--------------|----------------------------------------------------------|
| `/partners`  | 8 ecosystem partners + 3 payment gateways                |
| `/faqs`      | 13 grouped FAQs (Getting started, Pricing, etc.)         |
| `/contact`   | Contact form + 4 channel cards + 3 office cards          |

## Bilingual implementation

Every text element carries `data-en="..." data-ar="..."` attributes. Clicking the AR button:

1. Sets `<html dir="rtl" lang="ar">`
2. Switches all text to the Arabic translation via the data attributes
3. Loads the Arabic font (`IBM Plex Sans Arabic`)
4. Highlights AR in the toggle, persists choice in localStorage

Re-visiting any page reads the saved choice and applies it automatically.

## Sections on the home page

1. **Hero** — `Sell anything, anywhere. Packman builds your store from one photo.` + camera-icon input + Start free CTA
2. **Who it's for** — three video tiles (Handmade / Retail / Niche)
3. **Packman is simple** — 4-step process (Drop a photo → AI builds → Get orders → We ship)
4. **Run ads without becoming a marketer** — image grid + ad campaign preview card
5. **Launch content without a content team** — tile mosaic + content explanation
6. **Your warehouse, without owning one** — 4 region cards (UAE / KSA / Oman / 160+ countries)
7. **Hire your AI managers** — 8 cards (Marketing, Content, Storefront, Fulfillment, Support, Analyst, Accountant, Technical)
8. **Pricing teaser** — link to /pricing

## Deploy

Drag the `packman/` folder onto https://vercel.com/new — that's it. `vercel.json` enables `cleanUrls`.

## Local preview

```bash
cd packman
python3 -m http.server 8000
# open http://localhost:8000
```

## Source

Build script: `build_v5.py` in the project root.
Run `python3 build_v5.py` to regenerate the entire `packman/` folder.

## File inventory

```
packman/
├── README.md
├── vercel.json
├── index.html              ← home (generic)
├── uae/index.html          ← UAE home
├── ksa/index.html          ← KSA home
├── oman/index.html         ← Oman home
├── pricing/index.html      ← Pricing (UAE default)
├── pricing-uae/index.html  ← Pricing UAE
├── pricing-ksa/index.html  ← Pricing KSA
├── pricing-oman/index.html ← Pricing Oman
├── partners/index.html     ← Partners (ecosystem + payments)
├── faqs/index.html         ← FAQs
├── contact/index.html      ← Contact
└── assets/
    ├── logo-mark-navy.png
    ├── logo-mark-volt.png
    ├── logo-full-navy.png
    └── logo-full-volt.png
```
