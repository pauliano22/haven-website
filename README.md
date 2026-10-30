# haven-website

Marketing site for Haven: a static site with no build step of its own, deployed via
GitHub Pages. Design: "Sanctuary" (Evergreen + honey, chosen 2026-10-30 from three
directions; the other two live on the `redesign/directions` branch).

## Swapping the hero mark

Seven logo concepts were designed for Haven; **Radiant Bloom (`g`) is live**.
To change it, open `index.html`, find:

```js
var ACTIVE_LOGO = 'g';
```

(inside the hero-mark script at the bottom) and set it to `a` (Orb), `b` (Softened Wave), `c` (Canopy), `d` (Soft H —
also the app icon), `e` (Harbor Line), `f` (Damped Ligature), or `g`
(Radiant Bloom, current). Commit and push; GitHub Pages redeploys
automatically.

To preview any option without editing anything, add `?logo=e` (or any of the
letters above) to the live URL — useful for showing the others to someone
before committing to a swap.

Each concept's own reasoning is in the design review:
https://claude.ai/code/artifact/780deca4-9bb7-43ea-9869-33e8a70b66ca

Standalone copies of all seven marks (for use outside the site — decks,
READMEs, anything else) live in `assets/logos/`.

## Structure

- `index.html` — the page: markup, styles, the hero-mark script and the (unconnected)
  sign-up form. Radiant Bloom (`g`) is the breathing glow behind the wordmark; icon
  marks (`a`–`d`) render above the wordmark, `e` replaces the glow, `f` replaces the
  wordmark with its lockup.
- `explorer/index.html` — the interactive 3D model of the v2 earbud in an ear
  (three.js). Embedded in "How it works" with `?embed=1`; its panel colors are
  remapped to the site's tokens, the 3D content matches
  `haven_workspace/visuals/haven_ear_explorer.html`.
- `demo/` — static web export of the real app in demo mode (simulated earbud,
  example data), embedded in the App section's phone frame as `demo/?demo=1`.
  **Generated — don't edit by hand.** Rebuild from the `haven-app` repo:
  `npm run export:demo` (builds `dist-demo/` for the `/haven-website/demo/` base
  path), then replace this folder with it. `.nojekyll` must stay, or Pages drops
  the export's `_expo/` folder.
- `assets/logos/` — all seven marks as standalone `.svg` files.
- `assets/screenshots/` — real app screenshots (Home/Tune/Hearing).
- `assets/favicon.png`, `assets/og-image.png` — generated from the Soft H
  and Radiant Bloom marks respectively.
- `redesign/shots/` — screenshots from the redesign's checks.

## Local preview

The demo's assets use absolute `/haven-website/demo/` paths (the GitHub Pages
project path), so serve the folder under that name:

```sh
mkdir -p /path/to/scratch && ln -sfn "$PWD" /path/to/scratch/haven-website
cd /path/to/scratch && python3 -m http.server 8000
# open http://localhost:8000/haven-website/
```
