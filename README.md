# IEEE International Conference on eScience — Conference Series

The landing site for the [IEEE International Conference on e-Science](https://escience-conference.org/)
series. It presents the current edition, the full archive of past conferences, the Steering and
Advisory Committees, and the Steering Committee Charter.

Built with [Jekyll](https://jekyllrb.com/). Content lives in YAML data files, so updating the site
(new editions, committee members, statistics) rarely requires touching HTML.

## Getting started

```bash
# Install Jekyll (once)
gem install jekyll

# Build the static site into _site/
jekyll build

# Or run a live-reloading dev server at http://localhost:4000/about/
jekyll serve
```

> The site is configured with `baseurl: /about` (see `_config.yml`), so the local dev URL is
> `http://localhost:4000/about/`. In production it is served from the root of the custom domain
> `escience-conference.org`.

## Project structure

```
index.html                 Home page — hero, stats, about, map, conferences, committees, charter
_config.yml                Jekyll configuration (title, baseurl, plugins)
_layouts/default.html      Page shell (header, content, footer, theme bootstrap)
_includes/
  head.html                <head>: meta tags, icons, stylesheets
  header.html              Sticky top navigation (desktop + mobile)
  footer.html              Footer
  charter.html             Steering Committee Charter text
_data/
  conferences.yml          Every edition + location, links, stats, proceedings
  steering-committee.yml   Current Steering Committee members
  advisory-committee.yml   Advisory Committee members
assets/
  css/main.css             Base theme + the "eScience — Modern Redesign" design system
  js/theme.js              Theme toggle, smooth scroll, mobile menu, misc UI
images/
  conferences/             Edition posters/logos (referenced from conferences.yml)
  sc/                       Committee member photos (referenced from the committee YAML)
favicon.*, apple-touch-icon.png, android-chrome-*.png
                           Site icons (see "Favicons" below)
```

## Updating content

All the frequently-changing content is data-driven — edit the YAML, no HTML needed.

### Add or update a conference (`_data/conferences.yml`)

```yaml
- edition: 22nd
  year: 2026
  location: Naples, Italy
  link: /2026            # conference website (external URL or internal path)
  current: true          # marks the hero / "Next Edition" card — set on exactly one entry
  image: escience2026.png # file in images/conferences/
  accepted: 33           # optional statistics (shown as pills on the card)
  submitted: 98
  attendees: 200
  proceedings: https://ieeexplore.ieee.org/...   # optional
  cancelled: true        # optional — renders a "Cancelled" banner
  reason: COVID-19       # optional, shown with the cancelled banner
  announcement: https://... # optional link on the cancelled banner
```

- Set `current: true` on the upcoming edition only; it drives the hero. All others render in the
  **Past Conferences** grid.
- The home page derives the "Editions" and "Papers presented" stats automatically from this file.

### Update committees (`_data/steering-committee.yml`, `_data/advisory-committee.yml`)

```yaml
- name: Kyle Chard
  role: Chair          # optional — Chair / Vice-Chair get a highlighted badge
  term: Third term through 2027
  photo: chard.jpg     # file in images/sc/ (use noimage.png if none)
  comment: Former Chair, 2013-2018   # optional extra note
```

## Deployment

`jekyll build` outputs the static site to `_site/` (git-ignored). Deploy that directory to the host
serving `escience-conference.org`.
