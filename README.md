# eurozig.eu

The EuroZig website, built with [Zine](https://zine-ssg.io) (0.12.0). The design
is ported from the taz-inspired HTML+CSS prototype in `~/repos/taz-theme`.

## Commands

- `zine` — dev server on http://localhost:1990 with live reload
- `zine release` — build the site into `public/`
- `zine install-schemas` — refresh Ziggy schemas for editor support

## Structure

- `content/index.smd` — homepage lead article (kicker/headline in `.custom`).
  Also published unchanged at `/club/` via `.aliases`, which is where the
  header nav's "club" link points.
- `content/*.smd` (e.g. `conferences.smd`) — homepage cards, subpages of the
  homepage index. Each card sets `.custom` fields: `section` (`mission` |
  `join`) and `image` + `image_alt` (a file in `assets/`). Top-level pages
  without a `section` field (like the events index) are ignored by the card
  loop. Cards are ordered newest-`date`-first — the `date` field is used
  purely as a sort weight.
- `content/events/` — events section. One `.smd` per event with `date`,
  `description`, and `.custom` `location`. The listing splits upcoming/past
  automatically at build time.
- `layouts/` — SuperHTML templates; `templates/base.shtml` holds the page
  chrome (top bar, header, footer). Placeholder links (`login`, `club`,
  `become a member`, `donate`, `Imprint`, `Privacy Policy`) live there.
- `assets/style.css` — ported taz-theme stylesheet (system font fallbacks, no
  bundled webfonts).
