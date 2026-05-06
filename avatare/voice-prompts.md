# Voice-Prompts für HeyGen

Voice-Prompts für die fünf Avatare. Format orientiert am HeyGen-Beispiel: erst Stimme (Wärme, Tonhöhe, Tempo, Artikulation, Akzent, Emotion), dann visuelle Verankerung (Hintergrund, Licht, Kleidung, Vibe), zum Schluss der Anwendungsfall.

> **Wichtig:** Alle Skripte sind **deutsch**, also bei Akzent immer **„native Standard German / Hochdeutsch"** angeben — sonst rutscht HeyGen leicht in einen englischen Sprecher-Default.

---

## 1 · Miriam (wf1)

> **Rolle im Skript:** Fachkraft, Anfang 30, erzählt abends vertraulich am Küchentisch („weißt du…"). Locker, enthusiastisch, real.

```
This person would have a warm, friendly, slightly enthusiastic voice with a medium-bright pitch and a natural, conversational pace — like someone telling a close colleague an exciting story over coffee. Clear articulation but unforced, with small natural pauses, occasional softer trailing sentences, and a hint of a smile in her tone. Native Standard German / Hochdeutsch accent, no regional dialect, no broadcaster polish — emotionally engaged, curious, real. Set against a plain, softly lit warm beige-cream background with gentle natural light, her sage-green knitted cardigan over a cream cotton shirt evokes a cosy late-evening home setup. Suited to peer-to-peer storytelling, behind-the-scenes practice reports, and informal tutorials for early-childhood educators.
```

---

## 2 · Sandra (wf2, wf3 Stimme 2, wf4)

> **Rolle im Skript:** Kitaleitung, Anfang 40. LinkedIn-Tonfall — souverän, leicht stolz, glaubwürdig. Wird in drei Videos eingesetzt — gleicher Stimm-Charakter durchgehend.

```
This person would have a calm, confident, composed voice with a medium pitch and a steady, measured pace — the kind of voice you trust to chair a meeting without raising it. Crisp clear articulation, balanced breath, well-formed sentences, with a quietly proud undertone when describing what worked. Native Standard German / Hochdeutsch accent, professional but never stiff, warm at the edges, faintly smiling. Set against a plain, softly lit light blue-grey background with even daylight, her tailored navy blazer over a soft white blouse evokes a modern leadership setting — credible, approachable, LinkedIn-ready. Suited to leadership reflections, professional case studies, and digital-transformation storytelling for Kita directors and team leads.
```

---

## 3 · Anna (wf3 Stimme 1)

> **Rolle im Skript:** Fachkraft Ende 30, koordiniert Elternkommunikation. Verbindlich, organisiert, herzlich, Eltern-zugewandt.

```
This person would have a warm, kind, gently organised voice with a medium pitch and a calm, even pace — the tone of someone who routinely speaks with worried parents and makes them feel at ease within a sentence. Soft but clearly articulated, with steady breath, small reassuring inflections at sentence ends, and a quietly smiling undertone. Native Standard German / Hochdeutsch accent, approachable and grounded, never bureaucratic. Set against a plain, softly lit warm peach-cream background with diffused natural light, her terracotta-orange long-sleeve blouse evokes a comfortable, parent-facing space — calm, caring, real. Suited to parent communication, inclusive Elternabend reports, and warm explanatory content for Kita families.
```

---

## 4 · Lisa (wf3 Stimme 3)

> **Rolle im Skript:** Technikvertraute Kollegin, Mitte/Ende 30. „Die mit dem Laptop am schnellsten umgeht." Praktisch, geerdet, ruhig erklärend.

```
This person would have a calm, grounded, gently analytical voice with a medium-low pitch and a deliberate, unhurried pace — like someone who thinks one beat ahead before she speaks. Precise articulation without sharpness, even rhythm, dry warmth, occasional understated humour, no rising inflections. Native Standard German / Hochdeutsch accent, matter-of-fact, reassuringly competent — the voice of the colleague everyone asks when something doesn't work. Set against a plain, softly lit warm beige-amber background, her amber-mustard fine-knit pullover and dark-tortoise rectangular glasses evoke a hands-on, makers'-table vibe — tech-confident but not corporate. Suited to step-by-step tech walkthroughs, tool explainers, and calm troubleshooting content for non-technical audiences.
```

---

## 5 · Petra (wf4)

> **Rolle im Skript:** Mentorin Anfang 50, erzählt auf einer Leitungskonferenz. Erfahren, warm, leicht mütterlich, sehr glaubwürdig.

```
This person would have a warm, mature, deeply reassuring voice with a medium-low pitch and a slower, deliberate pace — the kind of voice that makes a room of people lean in and stop checking their phones. Soft natural breath, gentle weight on key words, smooth phrasing, occasional thoughtful pauses, a faint smile audible throughout. Native Standard German / Hochdeutsch accent, lived-in and authentic — experienced without being lecturing, calm without being slow. Set against a plain, softly lit warm cream background with a faint hint of green, her terracotta-coral fine-knit cardigan over an oat-coloured linen blouse evokes a calm conference-keynote moment — trustworthy, grounded, human. Suited to mentor stories, conference keynotes, onboarding narratives, and reflective practice reports for early-childhood leaders.
```

---

## Tipps für die Voice-Erstellung in HeyGen

- **Sample-Text mitgeben:** HeyGen klingt deutlich besser, wenn du beim Voice-Cloning ein deutsches Beispielskript aus `geschichten-vorlesen.md` mitgibst — dann übernimmt das Modell den Sprachrhythmus mit.
- **Pitch-Hierarchie:** Petra → tiefste, langsamste Stimme · Lisa → ruhig, mittel-tief · Sandra → mittel, kontrolliert · Anna → mittel, weich · Miriam → mittel-hell, lebendigste. So bleibt jede Sprecherin in Video 3 (Anna / Sandra / Lisa) im Wechsel klar unterscheidbar.
- **Konsistenz Sandra:** Sie spricht in drei Videos. Stimme **einmal** erstellen und in allen drei Projekten denselben Voice-Slot nutzen — nicht neu generieren, sonst klingt sie pro Video minimal anders.
- **Falls HeyGen-Stimmen zu „glatt" klingen:** Im Voice-Prompt explizit `"with small natural micro-pauses, slight breath sounds, no broadcaster polish"` ergänzen — das macht den Sprachfluss menschlicher und passt zum dokumentarischen Praxisbericht-Charakter eurer Geschichten.
- **Emotionale Anker:** In den Skripten in `geschichten-vorlesen.md` sind in *kursiven eckigen Klammern* Sprechhinweise wie *[leiser, persönlich]* eingebaut — die kannst du in HeyGen als „Pause / emphasis"-Marker übernehmen.
