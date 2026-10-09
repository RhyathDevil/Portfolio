# Aufgaben – Portfolio

Diese Liste beschreibt, **was** auf jeder Seite vorhanden sein muss, aber nicht, **wie** du es programmierst.
Arbeite die Phasen in der angegebenen Reihenfolge ab. Mit `[ ]` und `[x]` kannst du deinen Fortschritt abhaken.

> **Grundregel:** Zuerst muss die Seite **nur mit HTML** vollständig funktionieren und bedienbar sein.
> CSS macht sie danach schön, JavaScript macht sie anschließend komfortabler.
> Wenn JavaScript ausfällt, darf kein Inhalt verloren gehen.

---

## Phase 0 – Design-Vorgaben

Diese Vorgaben sind ein Vorschlag. Du darfst sie ändern, solange die Kontrastwerte eingehalten bleiben.

**Stil:** Ruhig, sachlich und mit viel Weißraum. Das Design soll die Projekte in den Vordergrund stellen und nicht sich selbst. Es gibt genau eine Akzentfarbe, keine Effekthascherei und keine automatisch abspielenden Animationen.

**Schriften (lokal hosten):**
- Fließtext und Überschriften: *Atkinson Hyperlegible Next*. Sie wurde speziell für gute Lesbarkeit bei Sehbeeinträchtigung entwickelt.
- Code: *JetBrains Mono*

**Farben (Startwerte, jeden Wert mit einem Kontrast-Checker prüfen):**

| Rolle            | Hell      | Dunkel    | Mindestkontrast zum Hintergrund |
|------------------|-----------|-----------|---------------------------------|
| Hintergrund      | `#FAFAF7` | `#121417` | –                               |
| Fläche (Karten)  | `#FFFFFF` | `#1B1E23` | –                               |
| Text             | `#1C1F24` | `#E6E6E1` | 4.5 : 1                         |
| Text gedämpft    | `#555B66` | `#A3A8B0` | 4.5 : 1                         |
| Akzent / Links   | `#1D4ED8` | `#93B4FF` | 4.5 : 1                         |
| Rahmen / Fokus   | Akzent    | Akzent    | 3 : 1                           |

- [ ] Kontrastwerte aller Farbpaare in beiden Modi geprüft und dokumentiert
- [ ] Information wird nie *nur* über Farbe vermittelt (z. B. Links auch unterstrichen)

---

## Phase 1 – HTML

### 1.1 Gemeinsame Bausteine (auf jeder Seite gleich)

**`<html>`**
- [ ] Sprachattribut passend zur Sprachversion (EN oder DE)

**`<head>`**
- [ ] Zeichenkodierung (meta charset)
- [ ] Viewport-Angabe für mobile Geräte, Zoomen darf **nicht** gesperrt sein
- [ ] Seitentitel nach dem Muster „Seitenname – Dein Name“, auf jeder Seite einzigartig
- [ ] Meta-Description, auf jeder Seite einzigartig
- [ ] Verweise auf die CSS-Dateien
- [ ] Verweis auf die Druck-CSS (nur für Druckausgabe)
- [ ] Verweis auf das JavaScript (darf das Rendern nicht blockieren)
- [ ] Favicon-Verweise (SVG, ICO, Apple-Touch-Icon) und Web-Manifest
- [ ] Theme-Color für hellen und dunklen Modus
- [ ] Canonical-URL
- [ ] Alternative Sprachversionen (hreflang für EN, DE und x-default)
- [ ] Open-Graph-Angaben (Titel, Beschreibung, Bild, URL, Typ), damit Links in LinkedIn und anderen Diensten eine Vorschau zeigen

**`<body>` – Kopfbereich**
- [ ] „Zum Inhalt springen“-Link als allererstes fokussierbares Element
- [ ] Header-Bereich mit:
  - [ ] Name/Logo als Link zur Startseite
  - [ ] Hauptnavigation, als Navigation ausgezeichnet und beschriftet (z. B. „Main“), mit den Punkten: Home, Projects, About, Contact
  - [ ] Kennzeichnung des aktuellen Menüpunkts für Screenreader
  - [ ] Sprachumschalter als Link zur **selben** Seite in der anderen Sprache. Der Linktext steht in der Zielsprache und hat das passende Sprachattribut
  - [ ] Button für den Hell/Dunkel-Modus (vorerst nur das HTML, die Funktion folgt in Phase 3)
  - [ ] Button für das mobile Menü (vorerst nur das HTML)

**`<body>` – Hauptbereich**
- [ ] Genau ein Hauptbereich (main), Ziel des Sprunglinks
- [ ] Genau eine Überschrift der Ebene 1 pro Seite
- [ ] Überschriften-Hierarchie ohne Sprünge (h1 → h2 → h3, nie h1 → h3)

**`<body>` – Fußbereich**
- [ ] Footer mit:
  - [ ] Copyright-Zeile mit Namen und Jahr
  - [ ] Links zu GitHub, LinkedIn und E-Mail, jeweils mit verständlichem Text (nicht nur ein Icon)
  - [ ] Zweite Navigation, beschriftet (z. B. „Legal“), mit Imprint, Privacy und Accessibility

---

### 1.2 Startseite – `index.html`

Head: Titel, Description und OG-Bild passend zur Startseite

Body, Hauptbereich mit **vier Abschnitten**:
- [ ] **Hero / Intro:** h1 mit deinem Namen und deiner Rolle, ein bis zwei Sätze, wer du bist und was du suchst, zwei Handlungslinks („View projects“, „Contact me“)
- [ ] **Featured Projects:** h2, zwei bis drei Projektkarten (Aufbau siehe 1.3), Link „All projects“
- [ ] **Skills / Tech Stack:** h2, eine Liste der Technologien, gruppiert mit h3 (z. B. Frontend, Tools, Lernend)
- [ ] **Kurzer Kontakt-Aufruf:** h2, ein Satz und ein Link zur Kontaktseite

---

### 1.3 Projektübersicht – `projects/index.html`

Body, Hauptbereich:
- [ ] h1 „Projects“ und ein einleitender Satz
- [ ] **Filterbereich:** Gruppe von Filter-Buttons nach Technologie, als Gruppe beschriftet (vorerst nur HTML)
- [ ] Statusbereich, der Screenreadern die Anzahl der angezeigten Projekte mitteilt (wird in Phase 3 befüllt)
- [ ] **Projektliste** als Liste. Jede Projektkarte enthält:
  - [ ] Vorschaubild mit sinnvollem Alternativtext (oder leer, wenn rein dekorativ)
  - [ ] Projekttitel als h2, der Titel ist der Link zur Projektseite
  - [ ] Kurzbeschreibung (ein bis zwei Sätze)
  - [ ] Liste der verwendeten Technologien (Tags)
  - [ ] Die ganze Karte ist klickbar, aber es gibt nur **einen** Link pro Karte, damit Screenreader nichts doppelt ansagen
- [ ] Hinweis, falls es noch keine Projekte gibt („Coming soon“)

---

### 1.4 Projektseite – `projects/_template.html`

Head: Titel und Description individuell pro Projekt, OG-Bild ist ein Screenshot des Projekts

Body, Hauptbereich mit **sieben Abschnitten**:
- [ ] Breadcrumb-Navigation (Home › Projects › Projektname), als Navigation beschriftet, aktuelle Seite gekennzeichnet
- [ ] **Projektkopf:** h1 Projektname, Kurzbeschreibung, Metadaten (Zeitraum, Rolle, Technologien), Links zu Live-Demo und Quellcode
- [ ] **Overview:** h2, worum geht es und für wen ist das Projekt
- [ ] **The Problem:** h2, welches Problem wird gelöst
- [ ] **Approach:** h2, wie du vorgegangen bist, mit h3-Unterabschnitten für einzelne Schritte und Entscheidungen
- [ ] **Interactive Demo:** h2, Erklärung, was die Demo zeigt und wie man sie bedient, der Demo-Container und eine Textalternative / Beschreibung des Ergebnisses für alle, die die Demo nicht nutzen können
- [ ] **Challenges & Learnings:** h2, was schwierig war und was du gelernt hast
- [ ] **Screenshots:** h2, Abbildungen mit Bildunterschrift und Alternativtext
- [ ] Navigation zum vorherigen und nächsten Projekt sowie zurück zur Übersicht

---

### 1.5 Über mich – `about.html`

Body, Hauptbereich mit **vier Abschnitten**:
- [ ] h1 „About me“, Profilfoto mit Alternativtext, kurze Einleitung
- [ ] **Background:** h2, Werdegang als Text
- [ ] **Experience & Education:** h2, chronologische Liste (Zeitraum, Station, Beschreibung) mit korrekt ausgezeichneten Datumsangaben
- [ ] **Skills:** h2, Fähigkeiten in Gruppen, ohne Prozentbalken oder Sterne (die sagen nichts aus und sind schwer zugänglich)
- [ ] **CV:** h2, Download-Links für den Lebenslauf. Der Linktext nennt Sprache, Dateiformat und Größe

---

### 1.6 Kontakt – `contact.html`

Body, Hauptbereich:
- [ ] h1 „Contact“ und ein einleitender Satz (wofür man dich kontaktieren kann)
- [ ] **Kontaktwege:** h2, E-Mail-Link, LinkedIn, GitHub
- [ ] Optional / später: Kontaktformular (braucht ein Backend, siehe DATEISTRUKTUR.md)

---

### 1.7 Rechtliche Seiten – `imprint.html`, `privacy.html`

- [ ] Jeweils h1 und Abschnitte mit h2 entsprechend der gesetzlichen Pflichtangaben
- [ ] Inhalte mit einem Generator oder einer Vorlage erstellen und an deinen Hoster anpassen

---

### 1.8 Barrierefreiheit – `accessibility.html`

Body, Hauptbereich mit **vier Abschnitten**:
- [ ] h1 „Accessibility“
- [ ] **Standard:** h2, welcher Standard angestrebt wird (WCAG 2.2, Stufe AA)
- [ ] **What I did:** h2, Liste der umgesetzten Maßnahmen
- [ ] **Known limitations:** h2, ehrliche Liste der bekannten Einschränkungen
- [ ] **Feedback:** h2, wie man dir Barrieren melden kann

---

### 1.9 Fehlerseite – `404.html`

- [ ] h1 mit einer verständlichen Meldung (nicht nur „404“)
- [ ] Hinweis, was man jetzt tun kann, mit Links zu Startseite und Projekten

---

### 1.10 Deutsche Version – `de/`

- [ ] Alle Seiten aus 1.2 bis 1.9 übersetzt
- [ ] Sprachattribut, Titel, Description und Alternativtexte ebenfalls übersetzt
- [ ] Sprachumschalter zeigt jeweils auf die passende englische Seite

---

### 1.11 Weitere Dateien

- [ ] `robots.txt`
- [ ] `sitemap.xml` mit allen Seiten beider Sprachen
- [ ] `site.webmanifest`
- [ ] Favicons

---

## Phase 2 – CSS

### 2.1 Grundlage
- [ ] `reset.css`: einheitliche Ausgangsbasis
- [ ] `tokens.css`: alle Farben, Schriftgrößen, Abstände, Radien und Breiten als Variablen, mit einem Satz für den hellen und einem für den dunklen Modus
- [ ] Schriften lokal eingebunden, Text bleibt während des Ladens sichtbar

### 2.2 Typografie und Grundelemente (`base.css`)
- [ ] Schriftgrößen in relativen Einheiten, damit die Browser-Einstellung des Nutzers respektiert wird
- [ ] Zeilenlänge im Fließtext auf eine angenehm lesbare Breite begrenzt
- [ ] Großzügige Zeilenhöhe
- [ ] Links im Fließtext unterstrichen und von normalem Text unterscheidbar
- [ ] **Deutlich sichtbarer Fokus-Stil** für alle interaktiven Elemente, nur bei Tastaturbedienung
- [ ] Sprunglink ist unsichtbar, bis er Fokus bekommt
- [ ] Hilfsklasse für Text, der nur für Screenreader sichtbar ist

### 2.3 Layout (`layout.css`)
- [ ] Mobile-first: Grundstil für kleine Bildschirme, Erweiterungen für größere
- [ ] Header: Logo, Navigation, Sprach- und Theme-Umschalter
- [ ] Mobile Navigation: Darstellung im geschlossenen und geöffneten Zustand
- [ ] Footer-Layout
- [ ] Inhalts-Container mit maximaler Breite und seitlichem Abstand
- [ ] Bei 320 px Breite und bei 400 % Zoom gibt es **kein** horizontales Scrollen

### 2.4 Komponenten (`components.css`)
- [ ] Buttons und Handlungslinks: Zustände für Normal, Hover, Fokus, Aktiv und Deaktiviert
- [ ] Klickflächen mindestens 24 × 24 px (besser 44 × 44 px)
- [ ] Projektkarten mit vergrößerter Klickfläche über die ganze Karte
- [ ] Technologie-Tags
- [ ] Filter-Buttons inklusive sichtbarem Zustand „ausgewählt“ (nicht nur über Farbe)
- [ ] Breadcrumb
- [ ] Bilder skalieren mit und sprengen nie das Layout

### 2.5 Seiten und Demos (`pages.css`, `demos.css`)
- [ ] Hero-Bereich der Startseite
- [ ] Raster der Projektübersicht (ein bis drei Spalten je nach Breite)
- [ ] Aufbau der Projektseite
- [ ] Lebenslauf-Zeitleiste auf der About-Seite
- [ ] Rahmen und Steuerelemente der Demos

### 2.6 Nutzerpräferenzen
- [ ] Dunkelmodus folgt standardmäßig der Systemeinstellung
- [ ] Manuelle Wahl per Button überschreibt die Systemeinstellung
- [ ] Reduzierte Bewegung: Animationen und Übergänge werden deaktiviert, wenn das System es verlangt
- [ ] Hoher Kontrast / erzwungene Farben (Windows): Rahmen und Fokus bleiben sichtbar

### 2.7 Druck (`print.css`)
- [ ] Navigation, Buttons und Demos ausgeblendet
- [ ] Schwarzer Text auf Weiß
- [ ] Link-Adressen hinter dem Linktext ausgegeben

---

## Phase 3 – JavaScript

Für jede Funktion gilt: Ohne JavaScript ist die Seite trotzdem vollständig nutzbar.

### 3.1 Einstieg (`main.js`)
- [ ] Lädt die einzelnen Module
- [ ] Setzt eine Markierung, dass JavaScript verfügbar ist (damit CSS JS-abhängige Elemente erst dann zeigt)

### 3.2 Mobile Navigation (`navigation.js`)
- [ ] Menü-Button öffnet und schließt das Menü
- [ ] Zustand „offen/geschlossen“ wird Screenreadern mitgeteilt
- [ ] Escape schließt das Menü, danach liegt der Fokus wieder auf dem Menü-Button
- [ ] Ohne JavaScript ist die Navigation immer sichtbar

### 3.3 Theme-Umschalter (`theme.js`)
- [ ] Button wechselt zwischen hell und dunkel
- [ ] Der aktuelle Zustand wird Screenreadern mitgeteilt
- [ ] Die Wahl wird gespeichert und beim nächsten Besuch wiederhergestellt
- [ ] Kein kurzes Aufblitzen des falschen Themes beim Laden
- [ ] Ohne gespeicherte Wahl gilt die Systemeinstellung

### 3.4 Projektfilter (`project-filter.js`)
- [ ] Klick auf einen Filter zeigt nur passende Projekte
- [ ] Ausgewählter Filter wird Screenreadern mitgeteilt
- [ ] Statusbereich meldet die Anzahl der Treffer
- [ ] Filter „All“ setzt zurück
- [ ] Optional: Gewählter Filter wird in der URL gespeichert, damit man ihn teilen kann
- [ ] Ohne JavaScript werden alle Projekte angezeigt und die Filter ausgeblendet

### 3.5 Interaktive Projekt-Demos (`demos/*.js`)
Anforderungen an **jede** Demo:
- [ ] Vollständig per Tastatur bedienbar
- [ ] Alle Steuerelemente haben eine sichtbare Beschriftung
- [ ] Änderungen und Ergebnisse werden Screenreadern angekündigt
- [ ] Kein Inhalt blinkt mehr als dreimal pro Sekunde
- [ ] Nichts startet automatisch. Wenn sich etwas bewegt, kann man es pausieren
- [ ] Reduzierte Bewegung wird respektiert
- [ ] Die Demo wird erst geladen, wenn sie gebraucht wird (Performance)
- [ ] Ohne JavaScript bleibt die Textalternative aus Phase 1.4 sichtbar

---

## Phase 4 – Prüfen und Testen

### 4.1 Barrierefreiheit
- [ ] Ganze Website nur mit der Tastatur durchgehen: Ist alles erreichbar, ist die Reihenfolge logisch und ist der Fokus immer sichtbar?
- [ ] Test mit einem Screenreader (NVDA unter Windows oder Orca unter Linux)
- [ ] Automatischer Test mit Lighthouse und axe DevTools auf jeder Seite
- [ ] HTML-Validierung (W3C Validator) für jede Seite
- [ ] Browser-Zoom auf 200 % und 400 %
- [ ] Bildschirmbreite 320 px
- [ ] Beide Themes und reduzierte Bewegung getestet
- [ ] Alle Bilder auf Alternativtexte geprüft
- [ ] Ergebnisse auf `accessibility.html` eingetragen

### 4.2 Qualität
- [ ] Test in Firefox, Chrome/Edge und Safari (oder einem WebKit-basierten Browser)
- [ ] Test auf einem echten Smartphone
- [ ] Keine toten Links
- [ ] Bilder komprimiert, in modernen Formaten und mit festen Abmessungen (verhindert Layout-Sprünge)
- [ ] Lighthouse-Werte für Performance, Barrierefreiheit, Best Practices und SEO notiert
- [ ] Keine Fehler in der Browser-Konsole

### 4.3 Veröffentlichung
- [ ] Hosting gewählt
- [ ] Eigene Domain mit HTTPS
- [ ] Die 404-Seite ist beim Server eingerichtet
- [ ] Impressum und Datenschutz sind an den Hoster angepasst
