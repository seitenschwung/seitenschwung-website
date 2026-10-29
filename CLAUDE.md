# seitenschwung-website

## Purpose
The studio site of seitenschwung (Philipp und Sari), live at https://seitenschwung.com.
One page: hero with the three pages, scroll transition into the works, case studies, process, studio, contact.

## Stack
Static HTML, CSS and a small inline script, no build step in this repository. Served by unprivileged nginx.

## Layout
- `public/index.html`: the page. It is built outside this repository from the design workspace
  (`.werkstatt/template-himmel.html` + `build.py`, which inlines the logo SVGs) and copied here.
  Edit the template there, rebuild, then copy the result to `public/index.html`.
- `public/assets/`: fonts (self-hosted) and the work screenshots (webp).
- `public/og.png`, favicons, `robots.txt`, `sitemap.xml`.

## Commands
- Local preview: `python3 -m http.server -d public 8080`
- Tests and deploy: CI only (see below).

## CI and deploy contract
`.github/workflows/ci.yml` calls the shared pipeline `seitenschwung/template/.github/workflows/pipeline.yml@v1`.
The image listens on 8080, answers `/healthz` and serves `/version.txt`. `main` is production:
every push deploys to Coolify after green CI (repository variables `DEPLOY=auto`, `APP_DOMAIN=seitenschwung.com`).
`docker-compose.yml` keeps `image: ${IMAGE}`, the CrowdSec labels and the log rotation.

## Impressum and Datenschutz
Never by hand: fill in `legal.json` with the owners' real details; CI generates both pages.
The live deploy stops while a required field is empty.

## Conventions
UI language German, per Du. No external requests (fonts and images ship with the site).
