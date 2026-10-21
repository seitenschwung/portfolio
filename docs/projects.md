# Phase 2: Projekte als Referenzen

Stand: 2026-10-20. Freigabe: Kundenprojekte und Domains sind laut Owner (über die Admin-Session) zur Veröffentlichung freigegeben; Verwaltungs-Software nicht. Quelle: nur die Repos, die ich lesen konnte (flache Klone). Live-URLs, Kundennamen,
Zahlen und Zitate kenne ich nicht; Zahlen werden selbst gemessen, Zitate gibt es keine.
Die Fragen an den Owner stehen unten und werden nach dem Merge von PR #1 in `open-questions.md` übernommen.

## Ehrliche Bestandsaufnahme
| Repo | Zustand im Repo | Fallstudie möglich? |
| --- | --- | --- |
| seitenschwung/simonnirnberger | echte Seite (ca. 78 KB Quelltext), README, CI, Härtung | **Ja, ausführlich** |
| seitenschwung/habibihermanos | unverändertes Template (Demo-Seite, CLAUDE.md mit TODOs) | Nein, Inhalt fehlt im Repo |
| seitenschwung/lola-dieber | unverändertes Template | Nein |
| D (Next.js-Blueprint) | Next.js-Blueprint, nur Demo-Seite | Nein |
| Nirnberger/nora-website | nur README-Titel | Nein |
| der Blueprint | Blueprint (nextjs/fastapi nur oberflächlich angesehen) | Als Qualitätsanspruch, kein Kundenprojekt |
| Verwaltungs-Software (privat) | privat, nicht gelesen | Nur mit Zustimmung |
| ZwW CAU Kiel e.V. | von Seitenschwung gebaut, kein Repo in der Organisation | Ja, sobald der Owner die Fakten liefert (Referenz mit Freigabe) |
| nora-solcher, gruppe42 | Repos nicht sichtbar | Nur mit Angaben des Owners |

Die Klone sind flach (1 Commit), die Historie ist nicht auswertbar.

## Fallstudie 1: Simon Ernst Nirnberger, Zeichnung und Malerei (simonernstnirnberger.at)
- **Aufgabe:** Künstlerportfolio mit 13 Werken; österreichische Domain (österreichisches Recht fürs Impressum).
- **Lösung (im Repo belegt):** statische Seite ohne Build-Schritt (`site/` wird so ausgeliefert); Galerie mit Filtern, Großansicht mit Deep-Link (`?werk=13`), Menü-Overlay, Scroll-Sequenz im Hero. „Bewegung reduzieren“ und Datensparmodus schalten die Sequenz ab, `<noscript>`-Fallback mit Links zu allen Werken.
- **Technik:** nginx-unprivileged (UID 101), Port 8080, strenge CSP (`default-src 'self'`), keine Bibliotheken, kein Tracking, keine externen Fonts (Systemschriften). Container: read-only, `cap_drop: ALL`, `no-new-privileges`, Limits. Bilder eine Woche gecacht, ersetzte Bilder bekommen neue Dateinamen.
- **Pipeline:** Seite prüfen (JS/JSON-Syntax, alle Links, keine Fremdhost-Anfragen), Image gehärtet testen, danach ghcr.io und Deploy über Coolify mit Prüfung von `/version.txt` und automatischem Rollback.
- **Offen:** Screenshots der Werke (Urheberrecht des Künstlers), Zitat gibt es keines.

## Fallstudie 2: Zentrum für wissenschaftliche Weiterbildung CAU Kiel e. V. (Verein, Kiel)
Live: <https://zww-kiel.de>. Referenzprojekt mit Freigabe; vom Owner gebaut. Alle Angaben unten sind
von der Live-Seite oder durch eigene Messung belegt (Stand 2026-10-21). **Aufgabe des Vereins und
Ergebnisse kennt nur der Owner** (siehe `open-questions.md`, Nr. 10); dazu steht hier nichts.

Screenshots folgen, sobald die Bildrechte geklärt sind.

- **Inhalt und Aufbau (sichtbar):** Startseite mit klarer Aussage („Berufsbegleitende Masterstudiengänge für Fach- und Führungskräfte im Gesundheitswesen“), zwei Handlungsaufrufen („Unsere Studiengänge“, „Über uns“), den zwei Masterstudiengängen als Karten, Newsletter-Beitrag, Kontaktblock mit Telefon und E-Mail sowie Fußnavigation mit Impressum und Datenschutz. Hauptnavigation: Studiengänge, NOKI Kiel, Aktuelles, Über uns, Kontakt. Sprungmarke „Zum Inhalt springen“ vorhanden, Seitensprache `de`.
- **Technik (aus dem Quelltext):** WordPress mit dem Theme Kadence und Elementor; HSTS gesetzt. Alle beim Laden beobachteten Anfragen gehen an die eigene Domain (16 Anfragen in einem Lighthouse-Lauf, keine Fremdhosts).
- **Gemessen** (Lighthouse CLI, je drei Läufe, 2026-10-21, von der Entwicklungsbox, Simulation; Einzelmessungen, keine Echtnutzerdaten):

| Profil | Performance | Barrierefreiheit | Best Practices | SEO | LCP | CLS | TBT |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Mobil | 100 / 100 / 100 | 96 / 96 / 96 | 100 / 100 / 100 | 100 / 100 / 100 | 1,4 / 1,4 / 1,5 s | 0 / 0 / 0 | 30 / 10 / 50 ms |
| Desktop | 100 / 100 / 100 | 100 / 100 / 100 | 100 / 100 / 100 | 100 / 100 / 100 | 0,4 s (alle) | 0 / 0,001 / 0 | 0 ms (alle) |

- **Offen:** Aufgabe des Vereins, Ergebnis, Zitat; Bildrechte für Screenshots.

## Weitere Kundenseiten (Platzhalter, Angaben nötig)
habibihermanos, lola-dieber, jacky, nora, gruppe42: ohne Angaben schreibe ich nichts. Je Projekt brauche ich:
1. Live-URL (genaue Schreibweise)
2. Ausgangsproblem in einem Satz.
3. Was wurde gebaut, Besonderheiten?
4. Ergebnis: Zahlen oder Zitat, soweit freigegeben.

Vorschlag: zwei Zielgruppen-Kapitel, **Vereine** (ZwW CAU Kiel e.V.) und **Selbstständige** (nora-solcher).

## Eigenprodukt Verwaltungs-Software
Privat, nicht gelesen. Nur mit Zustimmung, nur mit erfundenen Demodaten, nie echte Rechnungen oder Kundendaten. Vorschlag: kurzer Abschnitt „Wie ich arbeite“ oder weglassen.

## Blueprints: Qualitätsanspruch
der Blueprint liefert pro Projekt: gehärtetes Image (read-only, non-root, Port 8080, `/healthz`, `/version.txt`), CI mit axe (WCAG AA) und Lighthouse, Deploy nach grüner CI über Coolify. Als Abschnitt „Qualität, die man prüfen kann“ mit echten Messwerten der eigenen Seite statt Schlagworten.

## Vorschlag für die Seite
1 ausführliche Fallstudie plus 2 bis 4 Kurzfälle, sobald Angaben und Zustimmung da sind. Keine erfundenen Zahlen, keine Platzhalter-Zitate live.

## Fragen an den Owner (Phase 2)
- Je Kundenprojekt: Name, Live-URL, Branche, was gebaut wurde (Admin schaltet die Hosts einzeln frei).
- Pro Kundenprojekt: Name, URL, Screenshots, Problem, Umfang, Ergebnis, Zitat (siehe oben).
- habibihermanos, lola-dieber, jacky und nora-website sind nur Template-Stand: wo liegt die echte Arbeit?
- Simon Nirnberger: Werkfotos als Screenshots zeigen (Urheberrecht des Künstlers klären)?
