# Packman site — v4

Static HTML, deploy-ready for Vercel. Complete redesign matching the cream/lime brand reference.

## What changed

This is a full visual redesign. Old edgy/dark aesthetic is gone — now soft cream wash background, floating pill navigation, two-color headlines, and rounded everything.

## Routes

### Country landing pages (homepage variants)
| URL      | Country | Currency |
|----------|---------|----------|
| `/`      | Generic | (none)   |
| `/uae`   | UAE 🇦🇪  | AED      |
| `/ksa`   | KSA 🇸🇦  | SAR      |
| `/oman`  | Oman 🇴🇲 | OMR      |

Each country page is identical to home, but:
- Its country pill in the footer is highlighted (dark navy)
- A small country badge under the hero shows "Showing prices for [country]" with a "change country" link

### Pricing pages (per-country plans)
| URL                | Currency           |
|--------------------|--------------------|
| `/pricing`         | AED (UAE default)  |
| `/pricing-uae`     | AED                |
| `/pricing-ksa`     | SAR                |
| `/pricing-oman`    | OMR                |

Currency in the plan tiers is baked in per URL — no JS toggle needed.

### Auxiliary pages
| URL          | Purpose                                  |
|--------------|------------------------------------------|
| `/partners`  | Logistics, payments, platforms partners  |
| `/faqs`      | 8 expandable FAQ items                   |
| `/contact`   | Email, WhatsApp, partnerships channels   |

## Design tokens

| Token       | Value     | Usage                              |
|-------------|-----------|------------------------------------|
| `--ink`     | `#0E1820` | Body text, dark buttons, logo bg   |
| `--olive`   | `#788938` | Highlighted headline phrase, links |
| `--volt`    | `#D2F801` | Lime green primary CTA buttons     |
| `--paper`   | `#FFFFFF` | Pill nav, cards, cookie banner     |
| `--soft`    | `#F0F2E3` | Light pill buttons (Login, Reject) |
| `--bg-base` | gradient  | Cream-yellow page wash             |

Typography: **Inter** (400/500/600/700/800) for everything; **IBM Plex Mono** (500/600) for tag pills and column titles.

## Components

- **Pill nav** — floating, white, full-rounded, subtle shadow. Logo lockup + nav links + Login (light pill, with chevron) + Launch your store (lime pill) + EN/AR toggle (dark/light pill).
- **Tag pill** — `● NEW · AI-POWERED SETUP` style indicator with green dot.
- **Two-color headline** — navy first half, olive second half. Wraps cleanly across two lines.
- **Hero input** — large white pill with camera icon + placeholder + lime "Start free →" button. Pressing Enter or clicking submits to `/pricing`.
- **Cookie banner** — fixed-position card at bottom with Reject (light pill) and Accept (lime pill). Dismissable via JS.
- **Country pills (footer)** — three pills with flag + name. Active country becomes dark navy.
- **Pricing cards** — 4-column grid with featured plan in dark navy + lime accents. Each card has a "Save X%" badge.
- **FAQ accordion** — `<details>`/`<summary>` rounded cards with rotating + indicator.

## Mobile

Below 768px:
- Nav links and Login button hide; only logo + Launch + EN/AR remain in the pill
- Logo tagline hides; logo mark/text shrink
- Hero text scales down; input button compacts to "Start free" without arrow icon
- Pricing grid collapses to single column
- Cookie banner stacks vertically with stretched buttons
- Footer columns collapse to single column

## Deploy

Drag the `packman/` folder onto https://vercel.com/new — that's it. `vercel.json` enables `cleanUrls`.

## Local preview

```bash
cd packman
python3 -m http.server 8000
# open http://localhost:8000
```

## Source

Build script: `build_v4.py` in the project root.
Run `python3 build_v4.py` to regenerate the entire `packman/` folder.

The script holds:
- A single CSS block (design tokens + components + mobile media query)
- A reusable shell with nav + footer + cookie banner
- Per-page body templates: `home_body`, `pricing_body`, `partners_body`, `faqs_body`, `contact_body`
- Country variants generated from a single dictionary (`COUNTRIES`)
