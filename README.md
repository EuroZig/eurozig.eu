# eurozig.eu

The EuroZig website, built with [Zine](https://zine-ssg.io) (0.12.0).

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
- `content/news/` — the news blog. One `.smd` per post with `date` and
  `description`; the listing shows posts newest-first. An RSS feed is
  published at `/news/index.xml` (declared as an `.alternatives` entry in
  `news/index.smd`, rendered by `layouts/news.xml`).
- `content/faq.smd` — the FAQ, a single Markdown page: each question is a
  `##` heading with the answer below it.
- `content/imprint.smd` + `content/privacy-policy.smd` — legal pages (linked
  from the footer), with German versions at `content/impressum.smd` and
  `content/datenschutz.smd`; the language versions cross-link via
  `$link.page`. Plain pages, not Zine i18n mode.
- `layouts/` — SuperHTML templates; `templates/base.shtml` holds the page
  chrome (top bar, header, footer). Placeholder links (`login`, `donate`)
  live there.
- `assets/style.css` — the site stylesheet (system font fallbacks, no
  bundled webfonts).

## Assets

The following assests were created using Canva:

- `assets/support.png`
- `assets/joinus.png`
- `assets/conf.png`
