# Phase 1: Recherche

Stand: 2026-10-20. Rechtsabschnitt im Gesetzeswortlaut geprüft. Status: **Entwurf, Teil B (Beispielanalyse) offen**, weil der Proxy die Seiten
der Beispiele sperrt (siehe `open-questions.md`, Abschnitt "Freischaltungen"). Alles unten ist
aus Suchergebnissen belegt; wo nur Sekundärquellen vorliegen, steht das dabei. Keine Rechtsberatung.

## A. Was die Recherche belegt

### Aufbau und Inhalt eines Portfolios
- Entscheidung fällt oft am Portfolio: Eine Umfrage der Creative Group (250 Marketing- und
  Designverantwortliche, über Format zitiert) nennt 63 % allein auf Basis des Portfolios.
  Sekundärquelle, Zahl nicht selbst geprüft.
- Empfehlung von Format: 10 bis 15 Projekte, breit nach Branche und Aufgabe. Für Seitenschwung
  (wenige, echte Kundenseiten) gilt das Gegenteil: **lieber 4 bis 6 gut erzählte Fallstudien
  als eine lange Galerie.**
- Fiverr rät zu kurzer Vorstellung der Person und Arbeitsweise plus Referenzen (Empfehlungsschreiben).
  Für uns: Zitate nur mit Zustimmung des Owners.
- Zielgruppe (kleine Unternehmen, Vereine, Selbstständige) sucht Verständlichkeit, nicht
  Agentur-Jargon: Festpreis-Pakete, klare Schritte, ein Ansprechpartner.

### Marktumfeld Kiel / Schleswig-Holstein (Suchtreffer, Selbstdarstellungen)
- Mick Ihde (Schwentinental-Raisdorf): Websites für Vereine, Schulen, Kleinunternehmen, dazu
  CMS-Abo für laufende Pflege. Nächster direkter Wettbewerber im Zuschnitt.
- ow WebSolutions (Kiel-Ravensberg): WordPress-Agentur für lokale Betriebe, Shops.
- kopfundstift.de: "Full Service aus einer Hand", wirbt mit SEO und DSGVO-Konformität.
- Weitere nur als Verzeichniseinträge (Das Örtliche): wavefrontdesign, Anker Webdesign.
- **Lücke, die Seitenschwung besetzen kann:** messbare Qualität (Lighthouse, Barrierefreiheit,
  Ladezeit) offen belegen, statt nur "responsive und SEO" zu behaupten. Die Wettbewerber setzen
  nach Selbstdarstellung auf WordPress oder Baukästen; eine statische, schnelle Seite ist
  Alleinstellung, muss aber in Kundennutzen übersetzt werden (schnell, sicher, wenig Wartung).

### Lokale Sichtbarkeit und SEO (Praxisquellen, keine offiziellen Vorgaben)
- Google-Unternehmensprofil anlegen; Name, Adresse, Telefon überall **identisch** führen.
- `LocalBusiness`/`ProfessionalService`-Schema mit Adresse, Telefon, `areaServed`, Geo.
  Bewertungen nur auszeichnen, wenn echte Daten vorliegen.
- Stadt-Landingpages (Kiel, Rendsburg, Österreich ...) nur mit **eigenem Inhalt** (lokale
  Referenzen, Anfahrt, eigene FAQ). Copy-Paste mit getauschtem Stadtnamen gilt als Doorway-Page.
  Empfehlung: zunächst **keine** Stadtseiten, nur eine gute Seite "Webdesign in Schleswig-Holstein
  und Österreich" und echte Referenzen vor Ort; Stadtseiten erst, wenn es je Ort Substanz gibt.
- Die Zahl "46 % der Suchen sind lokal" ist von 2018 und nicht regional: nicht verwenden.
- Deutsch texten: Du/Sie festlegen (offene Frage), kurze Sätze, Nutzen vor Technik, Preisrahmen
  oder "ab"-Preise nennen, eine Kontaktaufforderung pro Abschnitt.

### Recht und Datenschutz (Stand der Suchergebnisse)
- **Impressum:** § 5 Abs. 1 DDG (gesetze-im-internet.de, abgerufen 2026-10-20): leicht erkennbar,
  unmittelbar erreichbar, ständig verfügbar. Pflichtangaben: (1) Name und Anschrift der
  Niederlassung, (2) Angaben für schnelle elektronische Kontaktaufnahme **einschließlich E-Mail-Adresse**,
  (3) Aufsichtsbehörde bei erlaubnispflichtiger Tätigkeit, (4) Register und Registernummer, falls
  eingetragen, (5) Kammer/Berufsbezeichnung bei reglementierten Berufen, (6) **USt-IdNr. oder
  Wirtschafts-IdNr., falls vorhanden**, (7) bis (8) Liquidation bzw. audiovisuelle Mediendienste.
  Für Seitenschwung vermutlich relevant: 1, 2, 6; 3 bis 5 sind zu prüfen (Webdesign ist meist
  nicht reglementiert). Konkrete Daten liefert der Owner (Frage 6), nicht ins Repo vor Freigabe.
  Zusätzlich Abs. 2: weitere Informationspflichten aus anderen Gesetzen bleiben unberührt.
- **Cookies/Tracker:** § 25 TDDDG (früher TTDSG, Wortlaut geprüft): Speichern auf und Zugriff auf
  Informationen im Endgerät nur mit Einwilligung nach klarer, umfassender Information (Abs. 1).
  Ausnahmen (Abs. 2): reine Nachrichtenübertragung, oder **unbedingt erforderlich**, um einen vom
  Nutzer ausdrücklich gewünschten digitalen Dienst bereitzustellen. **Entscheidung: keine Cookies, keine Tracker, kein Banner.**
  Dann entfällt der Banner komplett (besser für Lighthouse und Vertrauen). Reichweitenmessung
  nur serverseitig/anonym oder gar nicht; Entscheidung beim Owner.
- **Schriften:** LG München I, 20.01.2022, Az. 3 O 17493/20: dynamische Einbindung von Google
  Fonts ohne Einwilligung = DSGVO-Verstoß (100 EUR Schadensersatz). Lokale Einbindung gilt als
  unproblematisch. **Entscheidung: Schriften selbst hosten (WOFF2, `font-display`, Subset).**
  Dasselbe gilt für Karten, Videos, Icon-CDNs, reCAPTCHA: nichts von Dritten laden.
- **Kontaktformular:** Datenschutzerklärung nennt Zweck, Speicherdauer, Empfänger. Einfachste
  saubere Lösung ist `mailto:` plus optional Formular über eigenen Endpunkt (Plan, Phase 4).
- **Barrierefreiheit (BFSG, seit 28.06.2025):** § 3 Abs. 3 BFSG (Wortlaut geprüft): Abs. 1 gilt
  „nicht für Kleinstunternehmen, die Dienstleistungen anbieten oder erbringen“. Die Definition
  (unter 10 Personen und höchstens 2 Mio. EUR Umsatz oder Bilanzsumme) steht nicht in § 3, sondern
  laut IHK/Händlerbund in der EU-Empfehlung; sie ist hier nicht im Wortlaut geprüft.
  Für Seitenschwung selbst damit nicht verpflichtend; **für Kunden mit Online-Shop oder
  B2C-Dienstleistung kann es relevant sein** und ist ein Verkaufsargument. Wir bauen trotzdem
  nach WCAG 2.2 AA. Behauptungen über Bußgelder stammen aus Anbieter-Blogs: ungeprüft.

## B. Beispielanalyse (5 bis 8 Beispiele): **offen**
Der Auftrag verlangt konkrete, begründete Beispiele. Ich konnte keine Seite abrufen
(`proxy refused the connection`), also analysiere ich nichts, was ich nicht gesehen habe.
Kandidaten aus den Suchtreffern: lukasrudrof.com (Webflow-Showcase, Nürnberg, reduziert,
hochwertig), Mick Ihde (Kiel, Wettbewerber), ow WebSolutions (Kiel), kopfundstift.de, sowie
die in Elementors Liste genannten robertbuergel und Komini Media. Sobald der Owner Domains
freigibt, ergänze ich je Beispiel: Hero-Versprechen, Navigation, Angebot, Vertrauenselemente,
Preissignal, Kontaktweg, was wir übernehmen und was nicht.

## C. Konsequenzen für Design und Plan (vorläufig)
1. Hero: ein Versprechen, ein Button ("Projekt anfragen"), darunter Belege (Messwerte).
2. Referenzen als Fallstudien (Problem, Lösung, Ergebnis), wenige und gut.
3. Festpreis-Pakete mit "ab"-Preis oder Rahmen, Ablauf in 4 Schritten.
4. Kontakt: E-Mail und Telefon sichtbar, Formular optional; Antwortzeit nennen.
5. Null Drittanfragen: kein Banner, kein CDN, Schriften lokal, Seite im Docker-Image statisch.

## Quellen
- Hostinger, Elementor, Format, Fiverr (Portfolio-Ratgeber, Suchtreffer)
- Webflow Showcase: Lukas Rudrof
- RA Plutte, Händlerbund, Otto Schmidt, DFN (LG München I zu Google Fonts)
- IHK München, IHK Koblenz, Händlerbund (BFSG)
- e-recht24, dr-datenschutz.de (TDDDG), IHK Nürnberg (Impressum)
- Semrush, blckalpaca.at, seo-day.de (lokale SEO)
