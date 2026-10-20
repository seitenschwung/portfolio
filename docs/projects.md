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
| ZwW CAU Kiel e.V., nora-solcher, gruppe42 | Repos nicht sichtbar | Nur mit Angaben des Owners |

Die Klone sind flach (1 Commit), die Historie ist nicht auswertbar.

## Fallstudie 1: Simon Ernst Nirnberger, Zeichnung und Malerei (simonernstnirnberger.at)
- **Aufgabe:** Künstlerportfolio mit 13 Werken; österreichische Domain (österreichisches Recht fürs Impressum).
- **Lösung (im Repo belegt):** statische Seite ohne Build-Schritt (`site/` wird so ausgeliefert); Galerie mit Filtern, Großansicht mit Deep-Link (`?werk=13`), Menü-Overlay, Scroll-Sequenz im Hero. „Bewegung reduzieren“ und Datensparmodus schalten die Sequenz ab, `<noscript>`-Fallback mit Links zu allen Werken.
- **Technik:** nginx-unprivileged (UID 101), Port 8080, strenge CSP (`default-src 'self'`), keine Bibliotheken, kein Tracking, keine externen Fonts (Systemschriften). Container: read-only, `cap_drop: ALL`, `no-new-privileges`, Limits. Bilder eine Woche gecacht, ersetzte Bilder bekommen neue Dateinamen.
- **Pipeline:** Seite prüfen (JS/JSON-Syntax, alle Links, keine Fremdhost-Anfragen), Image gehärtet testen, danach ghcr.io und Deploy über Coolify mit Prüfung von `/version.txt` und automatischem Rollback.
- **Offen:** Screenshots der Werke (Urheberrecht des Künstlers), Zitat gibt es keines.

## Weitere Kundenseiten (Platzhalter, Angaben nötig)
habibihermanos, lola-dieber, jacky, nora, ZwW CAU Kiel e.V., gruppe42: ohne Angaben schreibe ich nichts. Je Projekt brauche ich:
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
