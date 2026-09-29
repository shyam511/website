# bitlane.in — website

Static marketing site for **Bitlane** and its first product, **ProTerm** (a free,
private SSH terminal for Android, built to run AI coding agents). Plain HTML and
CSS, no JavaScript, no build step. Hosted on GitHub Pages at `https://www.bitlane.in`.

## Layout

```
website/
├── index.html                      # home: hero + one value section + footer
├── privacy.html                    # the privacy policy, served at /privacy
├── 404.html
├── styles.css                      # shared styles (app design tokens)
├── CNAME                           # custom domain for GitHub Pages
├── .nojekyll                       # serve files as-is
├── robots.txt
├── sitemap.xml
└── assets/
    ├── logo.svg                    # Dock mark, indigo tile (site + favicon)
    ├── mark-ink.svg                # inverse mark, ink tile
    ├── app-icon-512.png            # Play icon
    ├── feature-graphic.png         # 1024 × 500
    ├── hero.png                    # hero image (PNG fallback)
    └── hero.webp                   # hero image, served first (~46 KB)
```

## The hero image

`assets/hero.png` / `hero.webp` is generated with an image model via the Vercel AI
Gateway (`google/gemini-3-pro-image`), from the clean v3 UI capture
`../terminalV2/android/screenshots/uat/20260928-DEV-BASE-v3ui/06-terminal-ready.png`.
The script composes the screenshot onto a dark indigo gradient and asks the model to
render it as a photorealistic **Google Pixel** phone, preserving every on-screen
character. Generator: `/tmp/opencode/hero.py` (endpoint
`https://ai-gateway.vercel.sh/v1/chat/completions`, key read from
`~/.local/share/opencode/auth.json` under `.vercel.key` — never commit the key).

## Design

The site mirrors the app's Linear-anchored language
(`../terminalV2/android/.../ui/theme/Color.kt` and `Tokens.kt`): near-black surfaces
(`#0b0c0e`), `#23252b` hairlines, the indigo action accent `#5e6ad2`, system sans for
prose and a mono face for metadata. Light mode is supplied via `prefers-color-scheme`,
using the same light tokens as the app. The logo is the chosen **Dock** mark.

## Publish with GitHub Pages

Live at `shyam511/website` (branch `main`, root). The `CNAME` file names
`www.bitlane.in`, so `www` is canonical and the apex redirects to it:

- Apex `bitlane.in` → four `A` records `185.199.108.153 … 185.199.111.153`
  (plus the four `AAAA` records for IPv6).
- `www` → `CNAME shyam511.github.io`.

## Before launch

The hero CTA is a **"Coming soon on Google Play"** placeholder. Once ProTerm is
published, replace it with the listing link
(`https://play.google.com/store/apps/details?id=com.proterm.app`) — there is a comment
marking the spot in `index.html`.
