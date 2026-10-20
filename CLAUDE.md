# Seitenschwung Portfolio

## Purpose
Portfolio-Website von Seitenschwung (Webdesign & Websites, Philipp Nirnberger, Bünsdorf, SH).
Ziel: Kunden gewinnen (kleine Firmen, Vereine, Selbstständige im DACH-Raum). Produktions-URL:
offen (siehe docs/open-questions.md).

## Status
Planungsphase. Gebaut wird erst nach Freigabe von docs/research.md, design.md, plan.md durch den Owner.
Phasen: 1 Recherche, 2 Projekte (docs/projects.md), 3 Design + Prototyp, 4 Plan. Auftrag: ~/inbox/BRIEF.md.

## Stack
Aktuell statischer Platzhalter (`public/`, nginx). Endgültige Wahl (reines HTML/CSS oder
Astro/Eleventy im Multi-Stage-Dockerfile, Ergebnis immer in nginx) steht in docs/plan.md.

## Commands
- Dev: `python3 -m http.server 8080 --directory public --bind 0.0.0.0` (bis ein Generator gewählt ist)
- Tests/Lint/Build: noch keine (kein package-lock.json). Kommen mit der Technikwahl.
- Docker lokal: `docker build --build-arg APP_VERSION=dev -t portfolio .` (falls Docker verfügbar)

## Layout
- `docs/` Recherche, Projekte, Design, Plan, offene Fragen
- `public/` ausgelieferte Seite; `nginx.conf`, `Dockerfile`, `docker-compose.yml`: Deploy

## CI and deploy contract
`.github/workflows/` nicht ändern. Image: Port 8080, `/healthz` 200, `/version.txt` = APP_VERSION,
non-root, read-only Root-FS. CI: axe (WCAG AA), Lighthouse >= 90 (Ziel 95). `docker-compose.yml`
behält `image: ${IMAGE}`, CrowdSec-Labels (`crowdsec.enable=true`, `crowdsec.labels.type=nginx`)
und json-file-Rotation. `main` = Produktion, nur über PRs.

## Conventions
- UI-Sprache Deutsch (Du/Sie offen). Doku auf Deutsch.
- Datenschutz: keine Cookies, keine Tracker, keine Drittanbieter-Requests, Schriften selbst hosten.
- Farben aus dem Logo: Orange #FF690F (nur Flächen/Grafik/Buttons mit dunkler Schrift, 2,9:1 auf
  Weiß), Blau #0165FE, Blau Text #0340CD (~8:1), Grau #798291, Hintergrund #FDFDFD. Kontrast prüfen.
- Kundennamen, Screenshots, Zahlen, Zitate nur mit Zustimmung des Owners veröffentlichen.
- Offene Fragen gebündelt in docs/open-questions.md.
