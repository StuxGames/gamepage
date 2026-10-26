# Changelog

All notable changes to the Stux.Games Game Page are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Date Versioning](https://datevers.ing) since v26.10.23 (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/).

## v26.10.26

### Security

- The CI workflow runs on Node.js 24 instead of the end-of-life Node.js 20, which has no fix for the Brotli decoder vulnerability CVE-2026-111497

## v26.10.23-1

### Added

- A Discord link preview for every page except the 404 page: a `discord:component-embed` in each `<head>` with the page's name and description, Stux.Games's colour and icon, and a link back to Stux.Games. The Open Graph and other tags are unchanged. `python scripts/build-embeds.py` writes them from each page's `<title>` and meta description, and `scripts/build-sitemap.py` does the same for the sitemap page
- A full favicon set at the web root: `favicon.ico` (16, 32 and 48), `apple-touch-icon.png` (180) and `site.webmanifest`, with 192, 512 and maskable 512 icons in `assets/img/`, all made from the Stux.Games icon. The same four tags are in every page's `<head>`
- `tests/site.sh`, which checks that every Discord embed is valid JSON under 3,000 bytes, that the 404 page has none, that the favicon files have the right sizes, and that every `<head>` has the favicon tags

### Changed

- The favicon is now served from this site instead of following the browser's light or dark theme from the media host, so it is the same everywhere (browser tab, home screen, bookmarks)

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.3
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.0.3

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.2

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.1

### Added

- The home page's footer has a copyright line ("© 2026 Stux.Games. All rights reserved."), like the legal pages, with the years kept current automatically

### Fixed

- The legal, changelog and sitemap footers name Stux.Games in the copyright line instead of Stux.Group, and no longer say Stux.Games is operated by Stux Group Ltd: that belongs on the Imprint only, which still says it

## v1.0.0

### Added

- A placeholder page for a Stux.Games game whose page hasn't been set up yet: a handheld console whose screen reads GAME PAGE NOT FOUND, with a D-pad, A/B buttons, and Visit Stux.Games and Ask About It links
- Light and dark themes in Stux.Games' gold pair (`#FFBA1A` on dark, `#855D00` on light), with the matching logo for each, a pixel-dot grid and faint CRT scanlines; the theme follows the system until the toggle is used, and is remembered in `localStorage`
- Oxanium, self-hosted under `assets/fonts/` with its SIL Open Font License
- The Boring Legal Stuff hub (`/legal`) with Privacy Policy, Terms and Ethics, Cookies Policy, Imprint, Disclaimer and Opt-Out Preferences, a changelog page that renders this file (sections sorted Added, Changed, Fixed, Removed, Security, Deprecated), a themed 404 page, and `/sitemap/` + `sitemap.xml` + `robots.txt`
- Footer with the Stux.Games logo, "Every Stux.Games Game" (games.stux.games) and "Created with love / code / coffee by Stux.Games"
- `dev-server.sh` / `dev-server.bat`: PHP 7.4's built-in server with a router that serves the folder like GitHub Pages, with DEV_MODE on by default (dev banner, `?banner=` previews) and `--no-dev-mode` to render as production
- GitHub Actions: Pages deployment, plus CI that validates `index.html` and lints the Markdown
- `README.md`, `CONTRIBUTING.md`, `VERSION.md` and `commit.sh` / `commit.bat`
