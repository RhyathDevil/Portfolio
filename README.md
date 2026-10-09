# Portfolio

Personal portfolio website that presents my projects and explains them interactively. It is in English, with an optional German version.

**Status:** In development. The project structure is in place; the pages are being built.

## Features (planned)

- Project pages written as case studies, each with an interactive demo
- English and German versions with a language switcher
- Accessibility target: WCAG 2.2 AA, with an AAA colour contrast palette
- Light and dark mode that follows the system setting and can be switched manually
- Contact form handled by Netlify Forms
- Works without JavaScript (progressive enhancement)

## Tech stack

- HTML, CSS and vanilla JavaScript: no framework, no build step
- Hosting: Netlify
- Locally hosted fonts: Atkinson Hyperlegible Next, JetBrains Mono

## Installation

```
git clone https://github.com/RhyathDevil/Portfolio.git
cd Portfolio
```

There are no dependencies to install.

## Usage

Start a local server with `public/` as the root:

```
python -m http.server 8000 --directory public
```

Then open http://localhost:8000. Paths are root-relative (`/assets/...`), so opening the files directly via `file://` will not work.

Every push to `main` is deployed automatically by Netlify.

## Project structure

```
public/          Website (the only folder that is published)
  assets/        CSS, JavaScript, images, fonts, documents
  projects/      Project overview and project pages
  de/            German version, same file names as the English one
docs/            Project documentation and session logs
netlify.toml     Netlify configuration
```

See `DATEISTRUKTUR.md` for the full tree and the reasoning behind it, and `AUFGABEN.md` for the task list (both in German).

## Documentation

Session logs are in [`docs/sessions/`](docs/sessions/).
