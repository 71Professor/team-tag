# Design-Spec: Material-Überarbeitung /material

**Datum:** 2026-04-20  
**Status:** Genehmigt

## Ausgangslage

Die 6 Druckvorlagen im `/material`-Ordner verwenden IBM Plex Sans, reines Schwarz-Weiß und haben keinen visuellen Bezug zur Hauptseite `index-team.html`. Ziel ist es, beide Welten konsistent zu machen.

## Designsystem (Basis: index-team.html)

### Typografie
- **Überschriften:** Fraunces (serif, weight 700/900)
- **Fließtext / Beschriftungen:** DM Sans (weight 400/600/700)
- Google Fonts via `@import` (wie index-team.html)

### Farbpalette
| Variable | Wert | Verwendung |
|---|---|---|
| `--ink` | `#3A3A3A` | Haupttext, Tabellenköpfe |
| `--ink-soft` | `#6A6A6A` | Untertitel, Metainfo |
| `--ink-faint` | `#9A9A9A` | Beschriftungen, Platzhalter |
| `--paper` | `#F4EEE6` | Seitenhintergrund (Screen) |
| `--white` | `#ffffff` | Karten-/Boxhintergrund |
| `--border` | `#BFC5C9` | Rahmen, Trennlinien |

### Workflow-Akzentfarben
| Workflow | Farbe | Hex |
|---|---|---|
| WF 1 | Salbeigrün | `#9DB8A5` |
| WF 2 | Staubiges Blau | `#8FA9C4` |
| WF 3 | Terrakotta | `#C8927B` |
| WF 4 | Senf | `#D4B46A` |

## Dateien und Änderungen

### 1. `dienstepass.html` (A5)
- **Header:** Fraunces-Titel + Badge mit WF3-Farbe (Terrakotta, da Block 3)
- **Aufgaben-Boxen:** weißer Hintergrund, `--border`-Rahmen, Checkbox in WF3-Farbe
- **Hintergrund (Screen):** `--paper`
- **Print:** weißer Hintergrund, Farben erhalten

### 2. `laufzettel.html` (A4)
- **Tabellenköpfe:** `--ink` statt reines Schwarz
- **Workflow-Blöcke:** farbiger linker Randstreifen (3px) in jeweiliger WF-Farbe
- **Pausenzeilen:** `#f0ede8` (wärmer als reines Grau)
- **Fraunces** für Seitentitel

### 3. `qr-handout.html` (A5 quer)
- **Tabellenköpfe:** `--ink`
- **Zeilenstreifen:** `#f0ede8` statt `#f8f8f8`
- **Boxen:** `--border`-Rahmen statt harter schwarzer Border
- **Fraunces** für H1
- **Textänderung:** „Single Sign-On" → „zentrale Anmeldung"

### 4. `rollenkarten.html` (A4)
- **Karten:** `--border` Strichlinie statt `#999`
- **Karten-Badge:** `--ink` Hintergrund statt schwarzer Border
- **Tipps-Box:** `--paper` Hintergrund, `--border` Rahmen
- **Fraunces** für Rollentitel
- **Textänderung:** „Thinking aloud" → „laut denken"

### 5. `transfer-planer.html` (A5) → Titel: „Transferplaner"
- **Header:** Fraunces + WF4-Badge (Senf)
- **WF-Optionen:** farbiger linker Rand (3px) je WF-Farbe
- **Team-Tabelle:** `--ink` Kopfzeile
- **Textänderung:** „Transfer-Planer" → „Transferplaner" (auch `<title>`)

### 6. `workflow-karte.html` (A4, 4 Seiten)
- **Seitenkopf je WF:** vollflächige WF-Farbe, weißer Text, Fraunces H1
- **Szenario:** linker Rand in WF-Farbe statt Schwarz
- **Tabellenköpfe:** `--ink`
- **Rollen-Boxen:** `--border`
- **Nutzen-Box:** `--ink` Border (2px)
- **WF-Badge:** farbiger Hintergrund statt schwarze Border

## Textänderungen (Anglizismen)

| Alt | Neu | Wo |
|---|---|---|
| Transfer-Planer | Transferplaner | transfer-planer.html (Titel, h1, subtitle) |
| Workflow-Lab I / II | Workflow-Labor I / II | laufzettel.html |
| Lab-Briefing | Gruppen-Briefing | laufzettel.html, rollenkarten.html |
| Lab-Debrief | Gruppen-Auswertung | laufzettel.html, rollenkarten.html |
| Gallery Walk | Rundgang | laufzettel.html, rollenkarten.html |
| Dot-Voting | Punktabstimmung | laufzettel.html |
| Single Sign-On | zentrale Anmeldung | qr-handout.html |
| Thinking aloud | laut denken | rollenkarten.html |

**Bleiben erhalten** (Produktnamen / etablierte Begriffe): Chat, Meeting, Link, Account, QR-Code, Browser, Kurzlink, Workflow (als Eigennamen WF1–WF4)

## Print-Verhalten
- `@media print`: Hintergrund weiß, Farben (Rahmen, Randstreifen, Badges) bleiben erhalten
- mm-Maße und Seitenformate (A4/A5) unverändert
- Jede Datei ist standalone (kein externes CSS)

## Nicht in Scope
- Inhaltliche Änderungen an Aufgaben, Links, Szenarien
- Strukturelle Umbauten der HTML-Layouts
- Neue Dateien erstellen
