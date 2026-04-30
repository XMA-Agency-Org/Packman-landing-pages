# Packman site — Vercel-ready

Static HTML. No build step. Drop into Vercel and it works.

## Folder structure

```
packman/
├── index.html               ← homepage           (route: /)
├── pricing/index.html       ← pricing page       (route: /pricing)
├── for-brands/index.html    ← for brand owners   (route: /for-brands)
├── for-startups/index.html  ← for first-timers   (route: /for-startups)
├── ar/index.html            ← Arabic / KSA       (route: /ar)
├── uae-oman/index.html      ← UAE + Oman         (route: /uae-oman)
├── assets/                  ← logos + Arabic font files (you add these)
└── vercel.json              ← clean URLs config
```

## Why this fixes the broken pricing link

Vercel serves `pricing/index.html` automatically when someone visits `/pricing`.
Each page now lives in its own folder with an `index.html`, so every internal
link in the nav (`/`, `/pricing`, `/for-brands`, `/for-startups`, `/ar`,
`/uae-oman`) resolves correctly.

The previous setup had standalone HTML files with no routing — so a click on
"Pricing" hit `/pricing` and returned 404 because nothing was there.

## Before deploying — add your assets

Drop these 4 files into `/assets/`:

- `wordmark-navy.png` — your wordmark logo
- `logo-icon-navy.png` — your small icon mark
- `avenir-arabic-book.otf` — Avenir Arabic Book (weight 400)
- `avenir-arabic-black.otf` — Avenir Arabic Black (weight 900)

The site will load without them, but the wordmark will be missing and Arabic
text will fall back to IBM Plex Sans Arabic.

## Deploy options

### Option 1: Drag and drop (easiest)
1. Go to https://vercel.com/new
2. Drag the `packman/` folder onto the upload area
3. Click Deploy

### Option 2: Vercel CLI
```bash
cd packman
vercel deploy --prod
```

### Option 3: Git
```bash
cd packman
git init && git add . && git commit -m "Initial site"
git remote add origin <your-repo-url>
git push -u origin main
```
Then connect the repo to Vercel.

## Local preview before deploying

```bash
cd packman
python3 -m http.server 8000
```
Open http://localhost:8000 — the nav should work across all pages.

## Notes

- Pages use Tailwind via CDN — no build step needed.
- Internal links use absolute paths (`/pricing`, not `./pricing`) so they work
  from any folder depth.
- `vercel.json` enables clean URLs — `/pricing` rather than `/pricing/`.
- The `/ar` page is fully RTL. Language switcher links in the nav take users
  between `/` (EN) and `/ar` (Arabic).
