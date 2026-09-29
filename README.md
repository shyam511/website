# bitlane.in — website

Static marketing site for **Bitlane** and its first product, **ProTerm** (an SSH
client / terminal for Android built to run AI coding agents). Plain HTML and CSS,
no JavaScript, no build step. Hosted on GitHub Pages at `https://www.bitlane.in`.

## Layout

```
website/
├── index.html                      # home: Bitlane + ProTerm landing page
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
    └── screenshots/                # clean app screenshots (720 × 1280)
        ├── 01-agent-session.png
        ├── 02-resume.png
        ├── 03-terminal.png
        ├── 04-keys.png
        ├── 05-host-key.png
        └── 06-hosts.png
```

The screenshots are the raw v3 UI captures from
`../terminalV2/android/screenshots/uat/20260928-DEV-BASE-v3ui/`, not the Play
creatives, whose baked-in marketing copy would duplicate the page copy.

## Design

The site mirrors the app's Linear-anchored language
(`../terminalV2/android/.../ui/theme/Color.kt` and `Tokens.kt`): near-black
surfaces (`#0b0c0e`), `#23252b` hairlines, the indigo action accent `#5e6ad2`,
system sans for prose and a mono face for metadata. Light mode is supplied via
`prefers-color-scheme`, using the same light tokens as the app. The logo is the
chosen **Dock** mark (`>` chevron, dot and cursor bar).

## Publish with GitHub Pages

1. Create a repo (e.g. `shyam511/bitlane-website`) and push this folder.
2. **Settings → Pages →** source *Deploy from a branch*, branch `main`, folder `/ (root)`.
3. **Settings → Pages → Custom domain:** `www.bitlane.in` (the `CNAME` file already
   names it), then enable **Enforce HTTPS**. Point the domain's DNS at GitHub Pages
   (`A` records for the apex, `CNAME www → shyam511.github.io`).

`privacy.html` is served at `https://www.bitlane.in/privacy` — the exact URL the app's
Settings row and the Play Console listing use.

## Before launch

- The hero CTA is a **"Coming soon on Google Play"** placeholder. Once ProTerm is
  published, replace it with the listing link
  (`https://play.google.com/store/apps/details?id=com.proterm.app`) — there is a
  comment marking the spot in `index.html`.
- The privacy policy content matches `../terminalV2/launch-assets/privacy-policy.md`.
  Keep the two in step if the policy changes.
