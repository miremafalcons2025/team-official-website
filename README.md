# Mirema Falcons — Official Website

A lightweight, static website for the Mirema Falcons basketball club. Built with plain
HTML, CSS and JavaScript — no build step, no fake images, no fabricated reviews or
statistics.

## Features

- **Liquid glass / glassmorphism** UI: translucent panels with backdrop blur, soft
  shadows, subtle borders.
- **Adaptive theming**: follows the device's colour scheme (`prefers-color-scheme`)
  by default, with a manual toggle persisted in `localStorage`.
- **System typography**: uses the device's native font stack so the site matches the
  host platform's type.
- **Device-aware**: responsive from mobile to desktop.
- **Honest content**: no AI-generated images, no fake reviews, no invented scores or
  player stats. Data is loaded from small JSON files that the club fills in.

## Structure

```
index.html        Home
about.html        About the club
roster.html       Player roster
schedule.html     Fixtures & results
news.html         Club updates
contact.html      Contact form
css/styles.css    Design system
js/main.js        Behaviour + data rendering
assets/logo.png  Transparent circular badge (raster PNG, 1192x1196)
data/*.json       Club data (roster, schedule, news)
```

## Data files

- `data/roster.json` — array of `{ name, number, position, height, note }`
- `data/schedule.json` — array of `{ date, time, opponent, home, venue, result, score }`
- `data/news.json` — array of `{ title, date, body }`
- `data/gallery.json` — array of `{ src, alt, caption }` (real photos only)

Empty arrays (`[]`) render a graceful "coming soon" state.

## Preview locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening the HTML files directly over `file://` will also work, but the JSON data
fetch may be blocked by some browsers' security policies — use a local server.

## Customising

- Colours: CSS variables in `css/styles.css` (`--blue`, `--yellow`, …).
- Logo: replace `assets/logo.png` (and update favicon MIME if changing format).
- Theme defaults: `js/main.js` reads `prefers-color-scheme`.
- Contact backend: the form is currently client-only. Wire it to your service by
  changing the submit handler in `js/main.js`.
