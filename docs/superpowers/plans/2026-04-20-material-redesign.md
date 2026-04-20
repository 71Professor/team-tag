# Material-Überarbeitung Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Redesign alle 6 HTML-Druckvorlagen in `/material` auf das Designsystem von `index-team.html` (Fraunces + DM Sans, warme Palette, WF-Farbcodierung) und bereinige Anglizismen.

**Architecture:** Jede Datei erhält ein eigenständiges inline CSS-Update (kein externes Stylesheet — die Dateien müssen standalone druckbar bleiben). Font-Import wechselt von IBM Plex Sans auf Fraunces + DM Sans. CSS-Variablen werden in `:root` ergänzt. WF-Akzentfarben werden kontextspezifisch eingesetzt. Minimale HTML-Änderungen ergänzen strukturelle Wrapper für den neuen Header-Stil. Anglizismen werden inline ersetzt.

**Tech Stack:** HTML, CSS (keine Build-Tools, kein JavaScript)

---

## Gemeinsame Design-Tokens (Referenz für alle Tasks)

```css
/* Font-Import (ersetzt IBM Plex Sans in jeder Datei) */
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,700;0,9..144,900&family=DM+Sans:wght@300;400;500;600;700&display=swap');

/* CSS-Variablen (in :root jeder Datei hinzufügen) */
:root {
  --ink: #3A3A3A;
  --ink-soft: #6A6A6A;
  --ink-faint: #9A9A9A;
  --paper: #F4EEE6;
  --white: #ffffff;
  --border: #BFC5C9;
  --wf1: #9DB8A5;  /* Salbeigrün */
  --wf2: #8FA9C4;  /* Staubiges Blau */
  --wf3: #C8927B;  /* Terrakotta */
  --wf4: #D4B46A;  /* Senf */
}
```

---

## Task 1: dienstepass.html (A5)

**Files:**
- Modify: `material/dienstepass.html`

- [ ] **Schritt 1: Kompletten `<style>`-Block ersetzen**

Ersetze den gesamten Inhalt des `<style>`-Tags (Zeilen 8–126) durch:

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,700;0,9..144,900&family=DM+Sans:wght@300;400;500;600;700&display=swap');

:root {
  --ink: #3A3A3A; --ink-soft: #6A6A6A; --ink-faint: #9A9A9A;
  --paper: #F4EEE6; --white: #ffffff; --border: #BFC5C9;
  --wf3: #C8927B;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'DM Sans', sans-serif;
  font-size: 11pt;
  color: var(--ink);
  background: var(--paper);
  width: 148mm;
  min-height: 210mm;
  padding: 10mm 12mm;
  margin: 0 auto;
}

.doc-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  border-bottom: 2px solid var(--wf3);
  padding-bottom: 6px;
  margin-bottom: 4px;
}

h1 {
  font-family: 'Fraunces', serif;
  font-size: 14pt;
  font-weight: 900;
}

.block-badge {
  background: var(--wf3);
  color: white;
  font-size: 8pt;
  font-weight: 700;
  padding: 3px 9px;
  border-radius: 20px;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.subtitle { font-size: 9pt; color: var(--ink-soft); margin-bottom: 10px; }

.name-line {
  border-bottom: 1px solid var(--border);
  margin-bottom: 10px;
  font-size: 9pt;
  padding-bottom: 2px;
  color: var(--ink-faint);
}

.task {
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 6px 8px;
  margin-bottom: 7px;
  background: var(--white);
}

.task-header { display: flex; align-items: flex-start; gap: 7px; }

.check {
  display: inline-block;
  flex-shrink: 0;
  width: 15px;
  height: 15px;
  border: 1.5px solid var(--wf3);
  border-radius: 2px;
  margin-top: 1px;
}

.task-title { font-weight: 600; font-size: 10pt; }
.task-url { font-size: 8pt; color: var(--ink-faint); }
.task-desc { font-size: 9pt; color: var(--ink-soft); margin: 4px 0 4px 22px; }
.task-note { margin-left: 22px; }
.note-label { font-size: 8pt; color: var(--ink-faint); }
.note-line { border-bottom: 1px solid var(--border); height: 14px; margin-top: 2px; }

.task.optional { border-style: dashed; }
.optional-badge {
  font-size: 7.5pt;
  border: 1px solid var(--border);
  padding: 1px 4px;
  border-radius: 10px;
  color: var(--ink-soft);
  margin-left: 6px;
  vertical-align: middle;
}

.tip-box {
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 5px 8px;
  margin-top: 8px;
  font-size: 8.5pt;
  background: var(--white);
}
.tip-box strong { font-size: 9pt; }

.footer {
  font-size: 7.5pt;
  color: var(--ink-faint);
  border-top: 1px solid var(--border);
  padding-top: 5px;
  margin-top: 10px;
}

@media print {
  body { background: white; width: 148mm; min-height: 210mm; padding: 8mm 10mm; margin: 0; }
  @page { size: A5; margin: 0; }
}
```

- [ ] **Schritt 2: HTML-Struktur — Header-Wrapper ergänzen**

Ersetze im `<body>`:
```html
<h1>Dienstepass</h1>
<div class="subtitle">Block 3 (10:30–10:55) · Ziel: 5 von 6 Aufgaben schaffen</div>
```
Mit:
```html
<div class="doc-header">
  <h1>Dienstepass</h1>
  <span class="block-badge">Block 3</span>
</div>
<div class="subtitle">Block 3 (10:30–10:55) · Ziel: 5 von 6 Aufgaben schaffen</div>
```

- [ ] **Schritt 3: Im Browser öffnen und prüfen**

Öffne `material/dienstepass.html` im Browser.
Erwartetes Ergebnis:
- Warmer Papierhintergrund (#F4EEE6)
- Fraunces-Titel mit Terrakotta-Badge rechts
- Checkboxen mit Terrakotta-Rahmen
- Aufgaben-Boxen: weißer Hintergrund, heller Rahmen

- [ ] **Schritt 4: Commit**

```bash
git add material/dienstepass.html
git commit -m "style: redesign dienstepass.html – Fraunces/DM Sans, WF3-Farbcodierung"
```

---

## Task 2: laufzettel.html (A4)

**Files:**
- Modify: `material/laufzettel.html`

- [ ] **Schritt 1: Kompletten `<style>`-Block ersetzen**

Ersetze den gesamten Inhalt des `<style>`-Tags durch:

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,700;0,9..144,900&family=DM+Sans:wght@300;400;500;600;700&display=swap');

:root {
  --ink: #3A3A3A; --ink-soft: #6A6A6A; --ink-faint: #9A9A9A;
  --paper: #F4EEE6; --white: #ffffff; --border: #BFC5C9;
  --wf1: #9DB8A5; --wf2: #8FA9C4; --wf3: #C8927B; --wf4: #D4B46A;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'DM Sans', sans-serif;
  font-size: 11pt;
  color: var(--ink);
  background: var(--paper);
  padding: 16mm 16mm 12mm 16mm;
}

h1 {
  font-family: 'Fraunces', serif;
  font-size: 16pt;
  font-weight: 900;
  border-bottom: 2px solid var(--ink);
  padding-bottom: 4px;
  margin-bottom: 10px;
}

.meta {
  font-size: 9.5pt;
  color: var(--ink-soft);
  margin-bottom: 14px;
  display: flex;
  gap: 24px;
}

/* ── TAGESPLAN ── */
table.agenda {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 14px;
}

table.agenda th {
  background: var(--ink);
  color: var(--white);
  font-size: 9pt;
  font-weight: 600;
  padding: 4px 6px;
  text-align: left;
}

table.agenda td {
  border: 1px solid var(--border);
  vertical-align: top;
  padding: 4px 6px;
  font-size: 9.5pt;
}

table.agenda tr.pause td {
  background: #F0EDE8;
  color: var(--ink-soft);
  font-style: italic;
  font-size: 9pt;
}

table.agenda tr.highlight td { font-weight: 600; }

/* Farbstreifen links für Workflow-Blöcke */
table.agenda tr.wf1 td:first-child { border-left: 3px solid var(--wf1); }
table.agenda tr.wf2 td:first-child { border-left: 3px solid var(--wf2); }
table.agenda tr.wf3 td:first-child { border-left: 3px solid var(--wf3); }
table.agenda tr.wf4 td:first-child { border-left: 3px solid var(--wf4); }

.note-cell {
  height: 18px;
  min-width: 120px;
  border-left: 1px solid var(--border);
}

.col-time  { width: 13%; }
.col-block { width: 12%; }
.col-inhalt{ width: 40%; }
.col-notiz { width: 35%; }

/* ── DIENSTEPASS ── */
.section-title {
  font-family: 'Fraunces', serif;
  font-size: 12pt;
  font-weight: 700;
  border-bottom: 1.5px solid var(--ink);
  margin: 14px 0 8px 0;
  padding-bottom: 3px;
}

.pass-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 6px;
  margin-bottom: 14px;
}

.pass-item {
  border: 1px solid var(--border);
  border-radius: 5px;
  padding: 5px 7px;
  font-size: 9pt;
  background: var(--white);
}

.pass-item .check {
  display: inline-block;
  width: 14px;
  height: 14px;
  border: 1.5px solid var(--border);
  border-radius: 2px;
  vertical-align: middle;
  margin-right: 5px;
}

.pass-item .service { font-weight: 600; }
.pass-item .task { font-size: 8.5pt; color: var(--ink-soft); margin-top: 2px; }
.pass-item .link-line { border-bottom: 1px solid var(--border); margin-top: 5px; height: 1px; }
.pass-item .link-label { font-size: 7.5pt; color: var(--ink-faint); }

/* ── TRANSFER ── */
.transfer-box {
  border: 1.5px solid var(--ink);
  border-radius: 6px;
  padding: 8px 10px;
  margin-bottom: 10px;
  background: var(--white);
}

.transfer-box .label { font-size: 9pt; font-weight: 600; margin-bottom: 4px; }

.transfer-box .wf-options {
  display: flex;
  gap: 12px;
  margin-bottom: 8px;
  flex-wrap: wrap;
}

.transfer-box .wf-opt {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 9pt;
}

.transfer-box .wf-opt .check {
  display: inline-block;
  width: 13px;
  height: 13px;
  border: 1.5px solid var(--border);
  border-radius: 2px;
}

.write-line { border-bottom: 1px solid var(--border); height: 20px; margin-bottom: 6px; }
.write-label { font-size: 8pt; color: var(--ink-soft); margin-bottom: 2px; }

/* ── FOOTER ── */
.footer {
  font-size: 8pt;
  color: var(--ink-faint);
  border-top: 1px solid var(--border);
  padding-top: 5px;
  margin-top: 8px;
  display: flex;
  justify-content: space-between;
}

@media print {
  body { background: white; padding: 12mm 14mm 10mm 14mm; }
  @page { size: A4; margin: 0; }
}
```

- [ ] **Schritt 2: Tabellen-Zeilen mit WF-Klassen versehen**

In der `<tbody>` der Agenda-Tabelle, füge WF-Klassen nach diesem Muster hinzu.
Die Block-Farben folgen dem Farbschema von index-team.html:

```html
<!-- Block 1 → Salbeigrün (wf1) -->
<tr class="highlight wf1">
  <td>09:30–09:45</td><td>Block 1</td><td>Ankommen &amp; Erwartungsabfrage</td><td class="note-cell"></td>
</tr>
<!-- Block 2 → Staubiges Blau (wf2) -->
<tr class="wf2">
  <td>09:45–10:30</td><td>Block 2</td><td>KITA HUB: Alle Dienste kennenlernen (Demo)</td><td class="note-cell"></td>
</tr>
<!-- Block 3 → Terrakotta (wf3) -->
<tr class="wf3">
  <td>10:30–10:55</td><td>Block 3</td><td>Dienstepass: Kernhandlungen ausprobieren <em>(→ unten)</em></td><td class="note-cell"></td>
</tr>
<!-- Pause: keine WF-Klasse -->
<tr class="pause">
  <td>10:55–11:10</td><td></td><td>☕ Kaffeepause</td><td></td>
</tr>
<!-- Block 3b → Staubiges Blau (wf2) -->
<tr class="wf2">
  <td>11:10–11:20</td><td>Block 3b</td><td>Gruppen-Briefing: Gruppen bilden, Alltagsanker setzen</td><td class="note-cell"></td>
</tr>
<!-- Block 4 → Senf (wf4) -->
<tr class="highlight wf4">
  <td>11:20–12:05</td><td>Block 4</td><td>Workflow-Labor I — WF 1 &amp; WF 2 (geführt)</td><td class="note-cell"></td>
</tr>
<!-- Pause -->
<tr class="pause">
  <td>12:05–13:05</td><td></td><td>🍽 Mittagspause</td><td></td>
</tr>
<!-- Block 5 → Salbeigrün (wf1) -->
<tr class="highlight wf1">
  <td>13:05–14:05</td><td>Block 5</td><td>Workflow-Labor II — WF 3 &amp; WF 4 (eigenständig)</td><td class="note-cell"></td>
</tr>
<!-- Block 5b → Staubiges Blau (wf2) -->
<tr class="wf2">
  <td>14:05–14:20</td><td>Block 5b</td><td>Gruppen-Auswertung: Erkenntnisse &amp; Querverbindungen</td><td class="note-cell"></td>
</tr>
<!-- Pause -->
<tr class="pause">
  <td>14:20–14:35</td><td></td><td>☕ Kaffeepause</td><td></td>
</tr>
<!-- Block 6 → Terrakotta (wf3) -->
<tr class="wf3">
  <td>14:35–14:50</td><td>Block 6</td><td>Rundgang — Punktabstimmung</td><td class="note-cell"></td>
</tr>
<!-- Block 7 → Senf (wf4) -->
<tr class="highlight wf4">
  <td>14:50–15:20</td><td>Block 7</td><td>Transfer: „Ab Montag" + Team-Commitment <em>(→ unten)</em></td><td class="note-cell"></td>
</tr>
<!-- Block 8 → Salbeigrün (wf1) -->
<tr class="wf1">
  <td>15:20–15:30</td><td>Block 8</td><td>Abschluss, Fragen &amp; Blitzlicht</td><td class="note-cell"></td>
</tr>
```

- [ ] **Schritt 3: Anglizismen in section-titles und Dienstepass-Abschnitt ersetzen**

Ändere:
```html
<div class="section-title">Tagesplan &amp; Notizen</div>
```
→ bleibt (bereits Deutsch)

```html
<div class="section-title">Dienstepass (Block 3) — Hake ab, was du erledigt hast</div>
```
→ bleibt (bereits Deutsch)

```html
<div class="section-title">Transfer: Mein nächster Schritt (Block 7)</div>
```
→ bleibt (bereits Deutsch)

Ändere in der `.transfer-box`:
```html
<div class="wf-opt"><span class="check"></span> WF 1 — Fachwissen ins Team bringen</div>
<div class="wf-opt"><span class="check"></span> WF 2 — Teamsitzung digital vorbereiten</div>
<div class="wf-opt"><span class="check"></span> WF 3 — Elternabend hybrid organisieren</div>
<div class="wf-opt"><span class="check"></span> WF 4 — Neue Kolleg:in einarbeiten</div>
```
→ bleibt (bereits Deutsch)

- [ ] **Schritt 4: Im Browser öffnen und prüfen**

Öffne `material/laufzettel.html` im Browser.
Erwartetes Ergebnis:
- Fraunces-Seitentitel
- Tabellenkopf in #3A3A3A (nicht reines Schwarz)
- Farbige linke Randstreifen an Workflow-Zeilen
- Pausen in warmem #F0EDE8
- Begriffe: „Gruppen-Briefing", „Gruppen-Auswertung", „Workflow-Labor", „Rundgang", „Punktabstimmung"

- [ ] **Schritt 5: Commit**

```bash
git add material/laufzettel.html
git commit -m "style: redesign laufzettel.html – Farbstreifen, Fraunces, Anglizismen bereinigt"
```

---

## Task 3: qr-handout.html (A5 quer)

**Files:**
- Modify: `material/qr-handout.html`

- [ ] **Schritt 1: Kompletten `<style>`-Block ersetzen**

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,700;0,9..144,900&family=DM+Sans:wght@300;400;500;600;700&display=swap');

:root {
  --ink: #3A3A3A; --ink-soft: #6A6A6A; --ink-faint: #9A9A9A;
  --paper: #F4EEE6; --white: #ffffff; --border: #BFC5C9;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'DM Sans', sans-serif;
  font-size: 10.5pt;
  color: var(--ink);
  background: var(--paper);
  width: 210mm;
  min-height: 148mm;
  padding: 10mm 14mm;
  margin: 0 auto;
}

h1 {
  font-family: 'Fraunces', serif;
  font-size: 13pt;
  font-weight: 900;
  border-bottom: 2px solid var(--ink);
  padding-bottom: 4px;
  margin-bottom: 8px;
}

.intro { font-size: 9pt; color: var(--ink-soft); margin-bottom: 10px; }

table.services {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 10px;
  font-size: 9pt;
}

table.services th {
  background: var(--ink);
  color: var(--white);
  padding: 4px 6px;
  text-align: left;
  font-size: 8.5pt;
  font-weight: 600;
}

table.services td {
  border: 1px solid var(--border);
  padding: 4px 6px;
  vertical-align: top;
}

table.services tr:nth-child(even) td { background: #F0EDE8; }

.col-dienst { width: 18%; font-weight: 700; }
.col-url    { width: 28%; font-family: monospace; font-size: 8.5pt; }
.col-func   { width: 38%; }
.col-acc    { width: 16%; text-align: center; }
.acc-no     { color: var(--ink-soft); }
.acc-yes    { font-weight: 600; }

.two-col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin-bottom: 10px;
}

.box {
  border: 1.5px solid var(--border);
  border-radius: 6px;
  padding: 6px 9px;
  background: var(--white);
}

.box-title {
  font-family: 'Fraunces', serif;
  font-size: 9pt;
  font-weight: 700;
  border-bottom: 1px solid var(--border);
  margin-bottom: 5px;
  padding-bottom: 2px;
}

.box ul { padding-left: 15px; font-size: 8.5pt; }
.box ul li { margin-bottom: 3px; }

.start-url {
  font-size: 10pt;
  font-weight: 700;
  text-align: center;
  border: 2px solid var(--ink);
  border-radius: 6px;
  padding: 5px 10px;
  margin-bottom: 10px;
  background: var(--white);
}
.start-url span { font-family: monospace; }

.footer {
  font-size: 8pt;
  color: var(--ink-faint);
  border-top: 1px solid var(--border);
  padding-top: 5px;
  display: flex;
  justify-content: space-between;
}

@media print {
  body { background: white; padding: 8mm 12mm; }
  @page { size: A5 landscape; margin: 0; }
}
```

- [ ] **Schritt 2: Textänderung — „Single Sign-On" ersetzen**

Ändere:
```html
<strong>Single Sign-On:</strong> Einmal anmelden auf <strong>kita.bayern/webapp</strong> → alle Dienste nutzen.
```
Zu:
```html
<strong>Zentrale Anmeldung:</strong> Einmal anmelden auf <strong>kita.bayern/webapp</strong> → alle Dienste nutzen.
```

- [ ] **Schritt 3: Im Browser öffnen und prüfen**

Öffne `material/qr-handout.html` im Browser.
Erwartetes Ergebnis:
- Fraunces-Titel, warmer Hintergrund
- Tabellenköpfe in #3A3A3A
- Gerade Zeilen in warmem #F0EDE8 (statt neutralem Grau)
- Boxen mit weichem Rahmen (#BFC5C9), weißem Hintergrund
- Text lautet „Zentrale Anmeldung"

- [ ] **Schritt 4: Commit**

```bash
git add material/qr-handout.html
git commit -m "style: redesign qr-handout.html – Fraunces, warme Palette, zentrale Anmeldung"
```

---

## Task 4: rollenkarten.html (A4)

**Files:**
- Modify: `material/rollenkarten.html`

- [ ] **Schritt 1: Kompletten `<style>`-Block ersetzen**

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,700;0,9..144,900&family=DM+Sans:wght@300;400;500;600;700&display=swap');

:root {
  --ink: #3A3A3A; --ink-soft: #6A6A6A; --ink-faint: #9A9A9A;
  --paper: #F4EEE6; --white: #ffffff; --border: #BFC5C9;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'DM Sans', sans-serif;
  font-size: 10.5pt;
  color: var(--ink);
  background: var(--paper);
  padding: 14mm 16mm;
  width: 210mm;
  margin: 0 auto;
}

h1 {
  font-family: 'Fraunces', serif;
  font-size: 13pt;
  font-weight: 900;
  border-bottom: 2px solid var(--ink);
  padding-bottom: 4px;
  margin-bottom: 6px;
}

.intro { font-size: 9pt; color: var(--ink-soft); margin-bottom: 14px; }

.cards-row {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 0;
}

.card {
  border: 1.5px dashed var(--border);
  padding: 10px 12px;
  min-height: 120mm;
  position: relative;
  background: var(--white);
}

.card-badge {
  font-size: 8pt;
  font-weight: 700;
  background: var(--ink);
  color: var(--white);
  border-radius: 3px;
  padding: 2px 7px;
  display: inline-block;
  margin-bottom: 5px;
  letter-spacing: 0.5px;
}

.card h2 {
  font-family: 'Fraunces', serif;
  font-size: 13pt;
  font-weight: 900;
  margin-bottom: 8px;
  border-bottom: 1.5px solid var(--border);
  padding-bottom: 4px;
}

.card .task-title {
  font-size: 9pt;
  font-weight: 700;
  margin: 8px 0 3px 0;
  text-transform: uppercase;
  letter-spacing: 0.3px;
  color: var(--ink-soft);
}

.card ul { padding-left: 14px; font-size: 8.5pt; }
.card ul li { margin-bottom: 4px; }

.card .tip {
  margin-top: 10px;
  font-size: 8pt;
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 4px 6px;
  color: var(--ink-soft);
  background: var(--paper);
}
.card .tip strong { font-size: 8.5pt; color: var(--ink); }

.cut-hint {
  font-size: 8pt;
  color: var(--ink-faint);
  margin: 10px 0 12px 0;
  text-align: center;
}

@media print {
  body { background: white; padding: 8mm 10mm; width: 210mm; }
  .card { background: white; }
  .card .tip { background: #F4EEE6; }
  @page { size: A4; margin: 0; }
  .cut-hint { display: block; }
}
```

- [ ] **Schritt 2: Anglizismen in beiden Karten-Sets ersetzen**

Beide Sets (Zeilen ~119–172 und ~177–232) haben dieselben Texte. Ersetze in **beiden Sets** folgende Passagen:

**In Protokollant:in-Karte**, Abschnittstitel:
```html
<div class="task-title">Im Lab-Debrief (Block 5b)</div>
```
→
```html
<div class="task-title">In der Gruppen-Auswertung (Block 5b)</div>
```

**In Ausprobier-Person-Karte**, Abschnittstitel:
```html
<div class="task-title">Im Gallery Walk (Block 6)</div>
```
→
```html
<div class="task-title">Im Rundgang (Block 6)</div>
```

**In Ausprobier-Person-Karte**, Listenitem:
```html
<li>Spricht laut, was gerade passiert (Thinking aloud)</li>
```
→
```html
<li>Spricht laut, was gerade passiert (laut denken)</li>
```

**In Moderator:in-Karte**, Abschnittstitel:
```html
<div class="task-title">Im Lab-Briefing</div>
```
→
```html
<div class="task-title">Im Gruppen-Briefing</div>
```

- [ ] **Schritt 3: Im Browser öffnen und prüfen**

Öffne `material/rollenkarten.html` im Browser.
Erwartetes Ergebnis:
- Karten mit gestricheltem Rand in #BFC5C9 (nicht #999)
- Karten-Badge: dunkles #3A3A3A mit weißer Schrift (statt Outline)
- Rollentitel in Fraunces
- Tipps-Boxen: #F4EEE6 Hintergrund
- Begriffe: „Gruppen-Briefing", „Gruppen-Auswertung", „Rundgang", „laut denken"

- [ ] **Schritt 4: Commit**

```bash
git add material/rollenkarten.html
git commit -m "style: redesign rollenkarten.html – Fraunces, weiche Rahmen, Anglizismen bereinigt"
```

---

## Task 5: transfer-planer.html (A5) → Transferplaner

**Files:**
- Modify: `material/transfer-planer.html`

- [ ] **Schritt 1: `<title>` und `<h1>` umbenennen**

```html
<!-- Zeile 7: -->
<title>Transferplaner – KITA HUB Team-Tag</title>

<!-- Im body: -->
<!-- Alt: -->
<h1>Transfer-Planer</h1>
<div class="subtitle">Block 7 (14:50–15:20) · Schritt 1: Einzelarbeit (8 Min.)</div>
<!-- Neu: -->
<div class="doc-header">
  <h1>Transferplaner</h1>
  <span class="block-badge">Block 7</span>
</div>
<div class="subtitle">Block 7 (14:50–15:20) · Schritt 1: Einzelarbeit (8 Min.)</div>
```

- [ ] **Schritt 2: Kompletten `<style>`-Block ersetzen**

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,700;0,9..144,900&family=DM+Sans:wght@300;400;500;600;700&display=swap');

:root {
  --ink: #3A3A3A; --ink-soft: #6A6A6A; --ink-faint: #9A9A9A;
  --paper: #F4EEE6; --white: #ffffff; --border: #BFC5C9;
  --wf1: #9DB8A5; --wf2: #8FA9C4; --wf3: #C8927B; --wf4: #D4B46A;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'DM Sans', sans-serif;
  font-size: 10.5pt;
  color: var(--ink);
  background: var(--paper);
  width: 148mm;
  min-height: 210mm;
  padding: 10mm 12mm;
  margin: 0 auto;
}

.doc-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  border-bottom: 2px solid var(--wf4);
  padding-bottom: 6px;
  margin-bottom: 4px;
}

h1 {
  font-family: 'Fraunces', serif;
  font-size: 13pt;
  font-weight: 900;
}

.block-badge {
  background: var(--wf4);
  color: white;
  font-size: 8pt;
  font-weight: 700;
  padding: 3px 9px;
  border-radius: 20px;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.subtitle { font-size: 9pt; color: var(--ink-soft); margin-bottom: 10px; }

.name-line {
  border-bottom: 1px solid var(--border);
  margin-bottom: 10px;
  font-size: 9pt;
  padding-bottom: 2px;
  color: var(--ink-faint);
}

.section-title {
  font-family: 'Fraunces', serif;
  font-size: 10pt;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.4px;
  border-bottom: 1.5px solid var(--border);
  margin: 12px 0 7px 0;
  padding-bottom: 2px;
  color: var(--ink-soft);
}
.section-title:first-of-type { margin-top: 0; }

.wf-choice {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6px;
  margin-bottom: 10px;
}

.wf-opt {
  border: 1px solid var(--border);
  border-left-width: 3px;
  border-radius: 4px;
  padding: 5px 8px;
  display: flex;
  align-items: flex-start;
  gap: 7px;
  font-size: 9pt;
  background: var(--white);
}

.wf-opt.wf1 { border-left-color: var(--wf1); }
.wf-opt.wf2 { border-left-color: var(--wf2); }
.wf-opt.wf3 { border-left-color: var(--wf3); }
.wf-opt.wf4 { border-left-color: var(--wf4); }

.check {
  display: inline-block;
  flex-shrink: 0;
  width: 14px;
  height: 14px;
  border: 1.5px solid var(--border);
  border-radius: 2px;
  margin-top: 2px;
}

.wf-opt .wf-label { font-weight: 600; display: block; }
.wf-opt .wf-desc  { font-size: 8pt; color: var(--ink-soft); }

.write-group { margin-bottom: 8px; }
.write-label { font-size: 9pt; font-weight: 600; margin-bottom: 2px; }
.write-line  { border-bottom: 1px solid var(--border); height: 20px; margin-bottom: 4px; }

.team-box {
  border: 2px solid var(--ink);
  border-radius: 6px;
  padding: 8px 10px;
  margin-bottom: 10px;
  background: var(--white);
}

.team-box .tb-title { font-family: 'Fraunces', serif; font-size: 10pt; font-weight: 700; margin-bottom: 6px; }

.team-table { width: 100%; border-collapse: collapse; font-size: 9pt; }
.team-table th {
  background: var(--ink);
  color: var(--white);
  padding: 3px 6px;
  text-align: left;
  font-size: 8.5pt;
  font-weight: 600;
}
.team-table td {
  border: 1px solid var(--border);
  padding: 3px 6px;
  height: 22px;
  vertical-align: bottom;
}

.col-wf  { width: 35%; }
.col-wer { width: 25%; }
.col-was { width: 25%; }
.col-bis { width: 15%; }

.next-step {
  border: 1.5px dashed var(--border);
  border-radius: 4px;
  padding: 6px 10px;
  margin-bottom: 10px;
  font-size: 9pt;
  background: var(--white);
}
.next-step .ns-label  { font-weight: 700; margin-bottom: 4px; }
.next-step .ns-line   { border-bottom: 1px solid var(--border); height: 22px; margin-bottom: 5px; }

.footer {
  font-size: 7.5pt;
  color: var(--ink-faint);
  border-top: 1px solid var(--border);
  padding-top: 5px;
  margin-top: 10px;
}

@media print {
  body { background: white; padding: 8mm 10mm; }
  .team-box, .wf-opt, .next-step { background: white; }
  @page { size: A5; margin: 0; }
}
```

- [ ] **Schritt 3: WF-Klassen an `.wf-opt`-Elementen ergänzen**

Ändere die vier `.wf-opt`-Divs in der `.wf-choice`-Sektion:

```html
<div class="wf-opt wf1">
  <span class="check"></span>
  <div>
    <span class="wf-label">WF 1</span>
    <span class="wf-desc">Fachwissen ins Team bringen</span>
  </div>
</div>
<div class="wf-opt wf2">
  <span class="check"></span>
  <div>
    <span class="wf-label">WF 2</span>
    <span class="wf-desc">Teamsitzung digital vorbereiten</span>
  </div>
</div>
<div class="wf-opt wf3">
  <span class="check"></span>
  <div>
    <span class="wf-label">WF 3</span>
    <span class="wf-desc">Elternabend hybrid organisieren</span>
  </div>
</div>
<div class="wf-opt wf4">
  <span class="check"></span>
  <div>
    <span class="wf-label">WF 4</span>
    <span class="wf-desc">Neue Kolleg:in einarbeiten</span>
  </div>
</div>
```

- [ ] **Schritt 4: Im Browser öffnen und prüfen**

Öffne `material/transfer-planer.html` im Browser.
Erwartetes Ergebnis:
- Titel lautet „Transferplaner" (ein Wort), Senf-Badge rechts
- WF-Optionen mit farbigen linken Randstreifen (je WF-Farbe)
- Team-Commitment-Tabelle mit dunklem Kopf
- Warmer Hintergrund, weiche Rahmen

- [ ] **Schritt 5: Commit**

```bash
git add material/transfer-planer.html
git commit -m "style: redesign transfer-planer.html – Transferplaner, WF-Farbränder, Senf-Badge"
```

---

## Task 6: workflow-karte.html (A4, 4 Seiten)

**Files:**
- Modify: `material/workflow-karte.html`

- [ ] **Schritt 1: WF-Klassen an `.page`-Divs ergänzen**

Ändere jeden der vier `<div class="page">` Opener:

```html
<!-- Seite 1: -->
<div class="page wf1">

<!-- Seite 2: -->
<div class="page wf2">

<!-- Seite 3: -->
<div class="page wf3">

<!-- Seite 4: -->
<div class="page wf4">
```

- [ ] **Schritt 2: `.wf-header`-Wrapper in jeder Seite ergänzen**

In jeder der 4 `.page`-Divs, umschließe `.wf-badge` und `h1` mit einem `.wf-header`-Wrapper:

```html
<!-- Vorher: -->
<div class="wf-badge">WF 1</div>
<h1>Fachwissen ins Team bringen</h1>
<div class="szenario">...</div>

<!-- Nachher (Beispiel Seite 1): -->
<div class="wf-header">
  <div class="wf-badge">WF 1</div>
  <h1>Fachwissen ins Team bringen</h1>
</div>
<div class="szenario">...</div>
```

Wiederhole dieses Muster für WF 2, WF 3 und WF 4.

- [ ] **Schritt 3: Kompletten `<style>`-Block ersetzen**

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,700;0,9..144,900&family=DM+Sans:wght@300;400;500;600;700&display=swap');

:root {
  --ink: #3A3A3A; --ink-soft: #6A6A6A; --ink-faint: #9A9A9A;
  --paper: #F4EEE6; --white: #ffffff; --border: #BFC5C9;
  --wf1: #9DB8A5; --wf2: #8FA9C4; --wf3: #C8927B; --wf4: #D4B46A;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'DM Sans', sans-serif;
  font-size: 10.5pt;
  color: var(--ink);
  background: var(--paper);
}

.page {
  width: 210mm;
  min-height: 297mm;
  padding: 0 0 12mm 0;
  page-break-after: always;
  position: relative;
  background: var(--white);
}
.page:last-child { page-break-after: avoid; }

/* ── WF-FARBKOPF ── */
.wf-header {
  padding: 14mm 16mm 12mm 16mm;
  color: white;
}
.page.wf1 .wf-header { background: var(--wf1); }
.page.wf2 .wf-header { background: var(--wf2); }
.page.wf3 .wf-header { background: var(--wf3); }
.page.wf4 .wf-header { background: var(--wf4); }

.wf-badge {
  display: inline-block;
  font-size: 8pt;
  font-weight: 700;
  border: 2px solid rgba(255,255,255,0.6);
  border-radius: 4px;
  padding: 2px 9px;
  margin-bottom: 5px;
  color: white;
  letter-spacing: 0.05em;
}

h1 {
  font-family: 'Fraunces', serif;
  font-size: 15pt;
  font-weight: 900;
  color: white;
  line-height: 1.2;
}

/* ── SEITENINHALT ── */
.page-body {
  padding: 12px 16mm 0 16mm;
}

.szenario {
  font-size: 9.5pt;
  color: var(--ink-soft);
  border-left: 3px solid var(--border);
  padding-left: 8px;
  margin-bottom: 12px;
  font-style: italic;
}
.page.wf1 .szenario { border-left-color: var(--wf1); }
.page.wf2 .szenario { border-left-color: var(--wf2); }
.page.wf3 .szenario { border-left-color: var(--wf3); }
.page.wf4 .szenario { border-left-color: var(--wf4); }

.section-title {
  font-family: 'Fraunces', serif;
  font-size: 10pt;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  border-bottom: 1px solid var(--border);
  margin-bottom: 6px;
  padding-bottom: 2px;
  color: var(--ink-soft);
}

table.steps {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 12px;
  font-size: 9.5pt;
}

table.steps th {
  background: var(--ink);
  color: var(--white);
  font-weight: 600;
  padding: 4px 6px;
  text-align: left;
  font-size: 9pt;
}

table.steps td {
  border: 1px solid var(--border);
  padding: 4px 6px;
  vertical-align: top;
}

table.steps tr:nth-child(even) td { background: #F0EDE8; }

.col-nr    { width: 6%; text-align: center; font-weight: 700; }
.col-dienst{ width: 22%; font-weight: 600; }
.col-aktion{ width: 72%; }

.rollen-grid {
  display: flex;
  gap: 10px;
  margin-bottom: 12px;
  flex-wrap: wrap;
}

.rolle {
  border: 1px solid var(--border);
  border-radius: 5px;
  padding: 5px 10px;
  font-size: 9pt;
  flex: 1;
  min-width: 100px;
  background: var(--white);
}
.rolle strong { display: block; font-size: 9.5pt; }

.output-box {
  background: #F0EDE8;
  border: 1px solid var(--border);
  border-radius: 5px;
  padding: 6px 10px;
  font-size: 9pt;
  margin-bottom: 12px;
}
.output-box .label { font-weight: 700; margin-bottom: 3px; }

.fill-section { margin-bottom: 10px; }
.fill-row { display: flex; align-items: baseline; gap: 8px; margin-bottom: 6px; }
.fill-label { font-size: 9pt; font-weight: 600; white-space: nowrap; min-width: 130px; }
.fill-line { flex: 1; border-bottom: 1px solid var(--border); height: 18px; }

.links-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6px;
  margin-bottom: 10px;
}

.link-field {
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 4px 7px;
  background: var(--white);
}
.link-field .lf-label { font-size: 8pt; color: var(--ink-faint); }
.link-field .lf-line  { border-bottom: 1px solid var(--border); height: 16px; margin-top: 3px; }

.nutzen-box {
  border: 2px solid var(--ink);
  border-radius: 5px;
  padding: 6px 10px;
  margin-bottom: 10px;
  background: var(--white);
}
.nutzen-box .label { font-size: 9pt; font-weight: 700; margin-bottom: 3px; }
.nutzen-box .line  { border-bottom: 1px solid var(--border); height: 20px; }

.footer {
  position: absolute;
  bottom: 10mm;
  left: 16mm;
  right: 16mm;
  font-size: 8pt;
  color: var(--ink-faint);
  border-top: 1px solid var(--border);
  padding-top: 4px;
  display: flex;
  justify-content: space-between;
}

@media print {
  body { background: white; }
  .page { background: white; padding: 0 0 10mm 0; }
  .wf-header { padding: 10mm 14mm 10mm 14mm; }
  .page-body { padding: 10px 14mm 0 14mm; }
  @page { size: A4; margin: 0; }
}
```

- [ ] **Schritt 4: `.szenario`-Divs und Restinhalt in `.page-body` einwickeln**

Der Inhalt nach `.wf-header` (alles von `.szenario` bis `.footer`) muss in ein `<div class="page-body">` eingewickelt werden, damit der Innen-Padding nur auf diesen Bereich wirkt (der `.wf-header` hat eigenes Padding).

Beispiel Seite 1 (vollständige Struktur):
```html
<div class="page wf1">
  <div class="wf-header">
    <div class="wf-badge">WF 1</div>
    <h1>Fachwissen ins Team bringen</h1>
  </div>
  <div class="page-body">
    <div class="szenario">...</div>
    <div class="section-title">Schritte</div>
    <table class="steps">...</table>
    <div class="section-title">Rollen</div>
    <div class="rollen-grid">...</div>
    <div class="output-box">...</div>
    <div class="section-title">Unsere Ergebnisse</div>
    <div class="links-grid">...</div>
    <div class="fill-section">...</div>
    <div class="nutzen-box">...</div>
    <div class="footer">...</div>
  </div>
</div>
```

Wiederhole dieses Muster für alle 4 Seiten.

- [ ] **Schritt 5: Im Browser öffnen und alle 4 Seiten prüfen**

Öffne `material/workflow-karte.html` im Browser und scrolle durch alle 4 Seiten.
Erwartetes Ergebnis:
- WF 1: Salbeigrüner Kopf
- WF 2: Blauer Kopf
- WF 3: Terrakotta-Kopf
- WF 4: Senf-Kopf
- Szenario-Streifen links in jeweiliger WF-Farbe
- Tabellenköpfe in #3A3A3A
- Gerade Tabellenzeilen in #F0EDE8
- Warme weiße Seitenkörper (kein reines Weiß — #ffffff, aber umgeben von --paper)

- [ ] **Schritt 6: Commit**

```bash
git add material/workflow-karte.html
git commit -m "style: redesign workflow-karte.html – farbige WF-Köpfe, Fraunces, warme Palette"
```

---

## Abschluss-Check

- [ ] **Alle 6 Dateien nebeneinander im Browser öffnen** — prüfe visuelle Konsistenz untereinander und mit index-team.html (gleiche Fonts, gleiche Akzentfarben)
- [ ] **Print-Preview prüfen** — öffne jede Datei im Browser, drücke Strg+P, prüfe dass Layouts auf den richtigen Papierformaten (A4/A5) sitzen
- [ ] **Finaler Commit falls nötig**

```bash
git add material/
git commit -m "style: material-redesign abgeschlossen – alle 6 Dateien konsistent mit index-team.html"
```
