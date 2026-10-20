# Phase 3: Design (Entwurf, zwei Richtungen)

Stand: 2026-10-20. Prototyp folgt als eigener PR. Alle Kontrastwerte unten habe ich mit dem
WCAG-2.x-Verfahren berechnet (relative Luminanz, Verhältnis auf zwei Nachkommastellen).
Keine Messwerte zu Seiten, keine Wirkungsbehauptungen.

## 1. Ziel und Versprechen
Zielgruppe: kleine Unternehmen, Vereine, Selbstständige im DACH-Raum. Sie wollen eine gute,
schnelle, rechtssichere Seite ohne Fachchinesisch. Die Seite muss selbst der Beweis sein:
ruhig, präzise, schnell, ohne Banner.

**Hero-Versprechen (Vorschlag, Du/Sie offen, hier neutral):**
> Websites, die schnell laden, für alle funktionieren und rechtlich sauber sind.
> Handgebaut in Schleswig-Holstein. Für Unternehmen, Vereine und Selbstständige.

Ein Handlungsaufruf: **„Projekt anfragen“** (Anker zum Kontakt). Zweitlink: „Referenzen ansehen“ (Textlink, kein zweiter Button).

## 2. Informationsarchitektur
Einseitige Startseite mit Ankern plus eigene Unterseiten für Tiefe. Navigation (5 Punkte, mobil als Menü-Button, Fokusfalle nur im geöffneten Menü):

1. **Start**: Hero, drei Belege (Schnell / Barrierefrei / Datenschutz ohne Banner), Auswahl Referenzen, Ablauf in Kurzform, Kontakt.
2. **Leistungen**: Webseite für Unternehmen, Vereine, Selbstständige; Pflege; Rechtliches (Impressum/Datenschutz-Texte als Vorlage). Preisrahmen oder „ab“-Preise (offene Frage 4).
3. **Referenzen**: Übersicht, je Projekt eine Fallstudie (Aufgabe, Lösung, Technik, Ergebnis). Ergebnisse nur belegt (Messung wiederholbar).
4. **Vorgehen**: 4 Schritte (Gespräch, Entwurf, Umsetzung, Start und Pflege), je Schritt was der Kunde bekommt und tut.
5. **Über mich**: kurze Vorstellung, Ort, Arbeitsweise.
6. **Kontakt** (Button im Header, kein Menüpunkt zweiter Ordnung): E-Mail und Telefon sichtbar, Formular optional, Antwortzeit nennen.
Footer: Impressum, Datenschutz, Barrierefreiheitshinweis (freiwillig), Region.

Pro Abschnitt genau ein Ziel und höchstens ein Handlungsaufruf.

## 3. Farbsystem
Aus dem Logo: Orange `#FF690F`, Blau (Flügel) `#0165FE`, Blau (Schrift) `#0340CD`, Schiefergrau `#798291`, Hintergrund `#FDFDFD`.
Regel: **Blau trägt Text und Links, Orange ist Akzent in Fläche und Grafik, Grau ist Linie und Nebensächliches.**

### Kontraste der Logofarben (WCAG, berechnet)
| Vordergrund | Hintergrund | Verhältnis | Folge |
| --- | --- | --- | --- |
| Orange `#FF690F` | `#FDFDFD` | 2,84 | **nicht für Text**, nur Fläche/Grafik (Grafik braucht 3,0: knapp darunter, also nie als einziges Merkmal) |
| Blau `#0165FE` | `#FDFDFD` | 4,81 | AA für normalen Text, nur knapp; Links/Buttons |
| Blau `#0340CD` | `#FDFDFD` | 7,88 | AAA für Text, **Standard für Überschriften-Akzente und Links** |
| Grau `#798291` | `#FDFDFD` | 3,81 | **nicht für normalen Text**; nur Linien, Icons, große Schrift ab 24 px |
| Weiß | Orange | 2,88 | **Weiß auf Orange verboten** |
| Dunkel `#14181F` | Orange | 6,17 | Orange-Buttons mit dunkler Schrift |
| Weiß | `#0340CD` | 8,02 | Blaue Buttons mit weißer Schrift |

### Tokens (hell)
| Token | Wert | Verwendung | Kontrast auf `--bg` |
| --- | --- | --- | --- |
| `--bg` | `#FDFDFD` | Hintergrund | |
| `--surface` | `#EEF3FF` | Flächen, Karten (leichtes Blau) | |
| `--text` | `#14181F` | Fließtext, Überschriften | 17,49 |
| `--text-muted` | `#4A5160` | Nebentext | 7,83 |
| `--link` | `#0340CD` | Links, Fokusrand | 7,88 |
| `--accent` | `#FF690F` | Flächen, Linien, Hover-Füllung | 2,84 (nur Fläche) |
| `--accent-text` | `#9A3C00` | orangener Text (selten, z. B. „schwung“-Akzent in Fließtext) | 6,84 |
| `--line` | `#798291` | Trennlinien, Icon-Konturen | 3,81 |
| `--btn-primary-bg / fg` | `#FF690F` / `#14181F` | Haupt-Button | 6,17 |
| `--btn-secondary-bg / fg` | `#0340CD` / `#FFFFFF` | zweiter Button | 8,02 |
Zusatz: `#5F6877` auf `--bg` 5,53 und auf `--surface` 5,06 (zulässiger Nebentext).

### Dunkle Variante
| Token | Wert | Kontrast auf `#0B1633` |
| --- | --- | --- |
| `--bg-dark` | `#0B1633` | |
| `--text-on-dark` | `#F2F4F8` | 16,21 |
| `--muted-on-dark` | `#A9B3C4` | 8,44 |
| `--accent-on-dark` | `#FF690F` | 6,19 (auch als Text zulässig) |
| `--link-on-dark` | `#7FA8FF` | 7,60 |
| Blau `#0165FE` auf `#0B1633` | | **3,65: nicht für Text**, nur große Grafik |
Das Grau `#798291` auf `#0B1633` erreicht 4,60 (Linien, kleine Hinweise).

### Zustände
- **Fokus:** 3 px Rand `#0340CD` (hell) bzw. `#7FA8FF` (dunkel), 2 px Abstand, auf allen interaktiven Elementen sichtbar (WCAG 2.2: Fokus nicht verdeckt).
- **Hover:** Haupt-Button hellt auf `#FF8A47` (dunkle Schrift 7,61), Links: Unterstreichung bleibt, nie nur Farbwechsel.
- **Aktiv, deaktiviert, Fehler:** Fehler nie nur rot, immer Text und Symbol.
- **Links im Fließtext:** immer unterstrichen.
Im Prototyp prüft ein kleines Skript alle Token-Paare erneut (Plan, Phase 4).

## 4. Typografie
Schriften **selbst gehostet**, WOFF2, Subset Latin, `font-display: swap`, Metrik-Fallback gegen Layout-Sprung. Keine Google-Fonts-Einbindung.

- **Überschriften:** Serifenschrift mit Charakter passend zur Wortmarke. Vorschlag **Fraunces** (variable, SIL OFL).
- **Fließtext/UI:** **Inter** (variable, SIL OFL), Alternative: Systemschrift, wenn Ladezeit wichtiger ist.
- Lizenz und Bezug (Quelle, SHA) werden im Plan dokumentiert; Dateien kommen ins Repo, nicht per CDN.

Skala (1,25, fluid mit `clamp`): 16 → 20 → 25 → 31 → 39 → 49 → 61 px. Fließtext 18 px mobil und Desktop, Zeilenhöhe 1,6, **Zeilenlänge 60 bis 72 Zeichen** (`max-width: 68ch`). Überschriften Zeilenhöhe 1,1 bis 1,2, `text-wrap: balance`. Absätze `text-wrap: pretty`. Sprache `lang="de"`, echte Anführungszeichen („…“), geschützte Leerzeichen bei Einheiten.

## 5. Raster und Abstände
- 12 Spalten ab 960 px, 4 Spalten mobil; Seitenrand 16 px mobil, 32 px ab 768, Inhalt max. 1200 px.
- Abstände in einer 4-px-Basis: 4, 8, 12, 16, 24, 32, 48, 64, 96, 128. Abschnitte 64 px mobil, 128 px Desktop.
- Mobile zuerst; Breakpoints bei 600, 960, 1280. Touch-Ziele mindestens 44 px.
- Bilder mit festem `aspect-ratio`, `width/height` gesetzt (kein Layout-Sprung), AVIF/WebP, `loading="lazy"` außer Hero.

## 6. Komponenten
Header (Wortmarke als SVG, Menü, Button), Hero, Belegleiste (3 Punkte), Referenzkarte, Fallstudien-Kopf, Ablauf-Schritte (nummerierte Liste), Preis-/Paketkarte, FAQ (native `<details>`), Kontaktblock, Footer. Alle ohne Bibliothek, semantisches HTML, Tastatur bedienbar. Skip-Link als erstes Element.

**Logo:** Das Raster-Logo wird als sauberes SVG nachgezeichnet (Zeichen aus drei Flügeln, Wortmarke „seiten“ in Blau, „schwung“ in Orange). Wortmarke im Header als SVG mit `<title>`, Orange nur als Fläche. Für Text neben dem Logo gilt Abschnitt 3.

## 7. Bewegung
Dezent und wertend: Bewegung zeigt Zusammenhang, nie Dekoration.
- Eintritt: Opazität und 12 px Verschiebung, 400 ms, `cubic-bezier(.2,.7,.2,1)`, per CSS `animation-timeline: view()` wo verfügbar, sonst ohne Animation.
- Hover: 150 bis 200 ms; Seitenübergang optional per View Transitions (nur Progressive Enhancement).
- Das Logo-Zeichen schwingt einmal beim Laden (≤ 800 ms), nicht in Schleife.
- **`prefers-reduced-motion: reduce`:** alle Übergänge aus, nichts bewegt sich automatisch; Inhalt bleibt vollständig sichtbar. Ohne JavaScript ist alles sichtbar.
- Kein Parallax, kein Autoplay-Video, kein Scroll-Hijacking.

## 8. Zwei Richtungen

### Richtung A: „Ruhige Redaktion“ (hell, Serif)
- Heller Grund `#FDFDFD`, viel Weißraum, große Serif-Überschriften in Dunkel mit einem blauen Wort, Orange als dünne Linie und als Button-Fläche.
- Referenzen als große, ruhige Bildkarten, Text in Spalten mit 68 ch.
- Ein dunkler Streifen (`#0B1633`) nur für den Schlussaufruf „Projekt anfragen“.
- **Stärken:** passt zum Logo (Serif, heller Hintergrund), wirkt hochwertig und seriös für Vereine und Selbstständige, höchster Kontrast, geringste Last.
- **Risiken:** kann zu leise wirken, wenn Bilder fehlen; lebt von gutem Text und guten Screenshots.

### Richtung B: „Kontrastreich“ (dunkler Hero, Sans)
- Navy-Hero `#0B1633`, große Sans-Headline, Orange als kräftiger Akzent, danach helle Abschnitte.
- Stärker, technischer, mehr „Agentur“.
- **Stärken:** hohe Aufmerksamkeit im Hero, Orange wirkt auf dunkel am besten (6,19).
- **Risiken:** entfernt sich vom hellen Logo-Auftritt; Hell/Dunkel-Wechsel verdoppelt den Prüfaufwand; wirkt eher austauschbar „Tech“.

### Empfehlung: **Richtung A**, mit dunklem Schlussband aus B
Begründung: Sie übernimmt Logo (Serifen-Wortmarke, helle Fläche) und Zielgruppe (Vertrauen vor Effekt), hat die einfachsten Kontrast-Verhältnisse und die kleinste Last für das Ziel Lighthouse ≥ 95 und LCP < 2 s. Das dunkle Schlussband gibt dem Kontaktaufruf Gewicht, ohne die ganze Seite zu wechseln.

## 9. Barrierefreiheit (Mindeststandard)
WCAG 2.2 AA: Skip-Link, sinnvolle Überschriftenebenen, Landmarks, sichtbarer Fokus, Kontrast wie oben, Ziel 24 × 24 px (empfohlen 44), Fehlerhinweise im Formular, `alt` nur wo Inhalt, keine reine Farbcodierung, Bewegung abschaltbar, Seite bis 200 % Zoom und 320 px Breite ohne horizontales Scrollen.

## 10. Offen
- Du oder Sie (beeinflusst Hero-Text).
- Preise: „ab“-Preis, Rahmen oder Anfrage.
- Welche Referenzen mit Screenshots (Urheberrecht der gezeigten Inhalte klären).
- Schriftwahl endgültig (Fraunces/Inter sind Vorschläge, Lizenz und Download-Quelle prüfen).
