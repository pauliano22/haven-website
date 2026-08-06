# haven-website

Marketing site for Haven — a single `index.html`, no build step, deployed via
GitHub Pages.

## Swapping the hero mark

Seven logo concepts were designed for Haven; **Radiant Bloom (`g`) is live**.
To change it, open `index.html`, find:

```js
var ACTIVE_LOGO = 'g';
```

and set it to `a` (Orb), `b` (Softened Wave), `c` (Canopy), `d` (Soft H —
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

- `index.html` — everything: markup, styles, and the hero-swap script.
- `assets/logos/` — all seven marks as standalone `.svg` files.
- `assets/screenshots/` — real app screenshots (Home/Tune/Hearing), kept in
  sync by hand when the app's UI changes meaningfully.
- `assets/favicon.png`, `assets/og-image.png` — generated from the Soft H
  and Radiant Bloom marks respectively.

## Local preview

No build step — just serve the folder:

```sh
python3 -m http.server 8000
```
