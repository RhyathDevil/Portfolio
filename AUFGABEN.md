# Aufgaben – Portfolio

Diese Liste beschreibt, **was** auf jeder Seite vorhanden sein muss und **warum**. Sie beschreibt nicht, **wie** du es programmierst. Den Weg dorthin findest du selbst.

> **Grundregel:** Zuerst muss die Seite **nur mit HTML** vollständig funktionieren und bedienbar sein.
> CSS macht sie danach schön, JavaScript macht sie anschließend komfortabler.
> Wenn JavaScript ausfällt, darf kein Inhalt verloren gehen.

---

## So arbeitest du mit dieser Datei

Jeder Abschnitt ist gleich aufgebaut:

- **Ziel:** Was am Ende des Abschnitts erreicht ist.
- **Aufgaben:** Die Checkliste. Unter jedem Punkt steht, was gemeint ist und warum es wichtig ist.
- **Fertig, wenn …:** Woran du selbst überprüfst, ob du den Abschnitt geschafft hast.
- **Hinweise zum Nachschlagen:** Zugeklappt. Darin stehen nur Fachbegriffe, nach denen du suchen kannst, aber keine Lösungen. Klapp sie erst auf, wenn du nicht weiterkommst.

**Ablauf für jede Aufgabe:**
1. Aufgabe lesen und verstehen, was verlangt ist.
2. Selbst nachschlagen. Die beste Quelle ist [MDN Web Docs](https://developer.mozilla.org/de/), weil sie zuverlässig und auf Deutsch verfügbar ist.
3. Umsetzen.
4. Mit „Fertig, wenn …“ prüfen.
5. Abhaken und committen.

**Wann du mich fragen solltest:** Wenn du eine Aufgabe nicht verstehst, wenn du nach eigenem Nachschlagen nicht weiterkommst oder wenn du wissen willst, ob deine Lösung gut ist. Zeig mir dann deinen Code, und ich gebe dir Rückmeldung.

---

## Empfohlene Reihenfolge

Die Phasen sind nach Technik sortiert (HTML, CSS, JS). Arbeiten solltest du aber in dieser Reihenfolge, damit du früh Ergebnisse siehst und nichts doppelt machst:

1. **1.0** Vorbereitung
2. **1.1 und 1.2** Grundgerüst und Inhalt der Startseite, nur in `index.html`
   → danach **4.3** Veröffentlichung einrichten, damit jeder weitere Schritt sofort live zu sehen ist
3. **2.1 bis 2.4** CSS-Grundlage, getestet an der Startseite
4. **1.3** Grundgerüst auf die anderen englischen Seiten übertragen
5. **1.4 bis 1.10** restliche Seiten, jeweils mit ihrem CSS aus **2.5**
6. **2.6 und 2.7** Nutzerpräferenzen und Druck
7. **Phase 3** JavaScript
8. **1.11** deutsche Version, erst wenn die englische fertig ist
9. **1.12** weitere Dateien
10. **Phase 4** Prüfen. Die Tastaturprüfung (4.1) machst du zusätzlich nach jeder fertigen Seite.

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
| Text gedämpft    | `#4A505A` | `#A3A8B0` | 4.5 : 1 (hell erreicht 7 : 1)   |
| Akzent / Links   | `#1E40AF` | `#93B4FF` | 4.5 : 1 (hell erreicht 7 : 1)   |
| Link Hover       | `#1E3A8A` | `#BFD3FF` | 4.5 : 1                         |
| Rahmen / Fokus   | Akzent    | Akzent    | 3 : 1                           |

- [x] Kontrastwerte aller Farbpaare in beiden Modi geprüft und dokumentiert
- [ ] Information wird nie *nur* über Farbe vermittelt (z. B. Links auch unterstrichen)

---

## Phase 1 – HTML

### 1.0 Vorbereitung

**Ziel:** Du kannst deine Seite im Browser so ansehen, wie sie später online aussieht.

- [x] **Lokalen Server starten**, und zwar mit dem Ordner `public/` als Wurzel, und die Seite unter `http://localhost:8000` öffnen.
  Alle Dateipfade in dieser Liste beziehen sich auf `public/`. Online ist `public/` das Wurzelverzeichnis deiner Domain.
  Öffne die Dateien nicht per Doppelklick (`file://…`). Sonst funktionieren wurzel-relative Pfade (`/assets/…`) und später auch JavaScript-Module nicht.
- [x] **Entwicklerwerkzeuge des Browsers kennenlernen** (F12): die Reiter *Elemente/Inspektor*, *Konsole* und *Netzwerk*.
  Mit diesen Werkzeugen findest du die meisten Fehler selbst.
- [x] **Barrierefreiheits-Inspektor finden.** In Firefox heißt der Reiter „Barrierefreiheit“, in Chrome liegt er unter „Elemente → Barrierefreiheit“.
  Dort siehst du, wie ein Screenreader deine Seite „sieht“.
- [x] **HTML-Validator als Lesezeichen** speichern: validator.w3.org/nu

**Pfad-Regel für das ganze Projekt:** Alle Verweise auf eigene Dateien beginnen mit `/`, also wurzel-relativ. Das gilt für CSS, JS, Bilder und Links zu anderen Seiten.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- Python: „http.server --directory“
- MDN: „Was sind die Browser-Entwicklerwerkzeuge?“
- Firefox: „Accessibility Inspector“

</details>

---

### 1.1 Grundgerüst – zuerst nur in `index.html`

> **Wie ist dieser Abschnitt gemeint?**
> Das Grundgerüst baust du **einmal**, und zwar in `index.html`. Schreib es nicht jetzt schon in alle Dateien.
> Beim Lernen wirst du das Gerüst noch oft ändern, zum Beispiel Klassen ergänzen oder die Navigation umbauen. Wenn es schon in 15 Dateien steht, musst du jede Änderung 15-mal machen.
> Erst wenn die Startseite steht und das Grund-CSS dazu fertig ist, kopierst du das Gerüst in Abschnitt **1.3** auf die anderen Seiten. Dort passt du nur noch an, was pro Seite anders ist.
>
> Ganz vermeiden lässt sich die Wiederholung bei einer statischen Website ohne Hilfsprogramme nicht. Wenn du später etwas im Header änderst, hilft dir in WebStorm „Replace in Files“ (Strg + Umschalt + R).

**Ziel:** Ein vollständiges, gültiges HTML-Dokument mit Kopfbereich, Hauptbereich und Fußbereich, das ohne CSS bereits sinnvoll lesbar und vollständig per Tastatur bedienbar ist.

#### A) Dokument und `<head>`

- [ ] **Doctype** als allererste Zeile.
  Er sagt dem Browser, dass er die Seite nach modernem Standard darstellen soll.
- [ ] **Sprachattribut** am `<html>`-Element (Englisch).
  Screenreader wählen danach die Aussprache. Mit falscher Sprache wird die Seite unverständlich vorgelesen.
- [ ] **Zeichenkodierung** als erstes Element im `<head>`.
  Ohne sie werden Umlaute und Sonderzeichen falsch dargestellt.
- [ ] **Viewport-Angabe.**
  Ohne sie zeigen Smartphones die Seite verkleinert wie auf einem Desktop an. **Zoomen darf nicht gesperrt werden.** Menschen mit Sehbeeinträchtigung sind darauf angewiesen.
- [ ] **Seitentitel** nach dem Muster „Seitenname – Dein Name“.
  Der Titel ist das Erste, was ein Screenreader vorliest, und er steht im Browser-Tab. Deshalb muss er auf jeder Seite eindeutig sein, und der Seitenname steht vorne.
- [ ] **Meta-Description** mit ein bis zwei Sätzen.
  Suchmaschinen zeigen diesen Text in den Suchergebnissen an.
- [ ] **CSS-Dateien einbinden**, in dieser Reihenfolge: reset → tokens → base → layout → components → pages → demos.
  Die Reihenfolge ist wichtig, weil spätere Dateien Regeln aus früheren überschreiben.
- [ ] **Druck-CSS einbinden** und dabei festlegen, dass sie nur beim Drucken gilt.
- [ ] **JavaScript einbinden** (`main.js`), ohne dass das Laden der Seite blockiert wird.
  Das Skript soll erst laufen, wenn das HTML vollständig gelesen wurde.
- [ ] **Favicons und Web-Manifest** verlinken: SVG, ICO und Apple-Touch-Icon.
  Die Dateien sind noch leer, das ist in Ordnung. Die Verweise kannst du trotzdem schon setzen.
- [ ] **Theme-Color**, einmal für den hellen und einmal für den dunklen Modus.
  Mobile Browser färben damit die Adressleiste passend zu deiner Seite ein.
- [ ] **Canonical-URL.**
  Sie sagt Suchmaschinen, welche Adresse die „offizielle“ für diese Seite ist. Sie braucht eine vollständige URL mit Domain. Solange du keine Domain hast, trägst du einen Platzhalter ein und merkst dir die Stelle.
- [ ] **Sprachalternativen**: je ein Verweis auf die englische Version, die deutsche Version und eine Standardversion (Englisch).
  Damit zeigen Suchmaschinen deutschen Nutzern die deutsche Seite. Auch hier brauchst du vollständige URLs.
- [ ] **Open-Graph-Angaben**: Titel, Beschreibung, Bild, URL und Typ.
  Wenn jemand deinen Link auf LinkedIn teilt, erscheint daraus eine Vorschaukarte mit Bild.

#### B) Kopfbereich im `<body>`

- [ ] **Sprunglink „Skip to main content“** als allererstes Element im `<body>`.
  Wer mit der Tastatur navigiert, müsste sonst auf jeder Seite erst durch die gesamte Navigation tabben. Das Ziel des Links ist der Hauptbereich (siehe C).
- [ ] **Header-Bereich** als eigenes Landmark-Element.
- [ ] **Name/Logo** als Link zur Startseite.
- [ ] **Hauptnavigation**
  - [ ] als Navigations-Element ausgezeichnet
  - [ ] mit einer unsichtbaren Beschriftung („Main“), weil die Seite zwei Navigationen hat und Screenreader sie unterscheiden müssen
  - [ ] Links als Liste: Home, Projects, About, Contact
  - [ ] Der Link zur aktuellen Seite ist für Screenreader als „aktuelle Seite“ gekennzeichnet, nicht nur optisch.
- [ ] **Sprachumschalter**
  - [ ] ein normaler Link (kein Button), der zur **gleichen** Seite in der anderen Sprache führt
  - [ ] Der Linktext steht in der Zielsprache („Deutsch“), damit Deutschsprachige ihn auch auf der englischen Seite finden.
  - [ ] Der Link ist mit der Sprache seines Textes ausgezeichnet, damit „Deutsch“ deutsch ausgesprochen wird, und gibt die Sprache des Ziels an.
- [ ] **Button für Hell/Dunkel** und **Button für das mobile Menü**
  - [ ] als echte Buttons, nicht als Links oder `div`s
  - [ ] jeweils mit einem Namen, den ein Screenreader vorlesen kann, auch wenn später nur ein Icon sichtbar ist
  - [ ] Sie funktionieren erst mit JavaScript (Phase 3). Ohne JavaScript dürfen sie später nicht sichtbar sein, denn ein Button, der nichts tut, verwirrt. Merk dir das für 3.1.

#### C) Hauptbereich

- [ ] **Genau ein Hauptbereich** (`main`) pro Seite, mit einer ID als Ziel für den Sprunglink.
- [ ] **Genau eine Überschrift der Ebene 1.**
- [ ] **Überschriften ohne Sprünge**: auf h1 folgt h2, auf h2 folgt h3. Ebenen werden nie übersprungen.
  Screenreader-Nutzer springen über Überschriften durch die Seite wie durch ein Inhaltsverzeichnis. Wähle die Überschriften-Ebene deshalb nach der Struktur, nie nach der Schriftgröße. Die Größe regelst du mit CSS.
- [ ] Jeder Abschnitt im Hauptbereich ist ein eigenes Abschnitts-Element und beginnt mit einer Überschrift.

#### D) Fußbereich

- [ ] **Footer** als eigenes Landmark-Element.
- [ ] **Copyright-Zeile** mit Namen und Jahr.
- [ ] **Profil-Links** zu GitHub, LinkedIn und E-Mail
  - [ ] Jeder Link hat lesbaren Text. Wenn du später Icons dazu nimmst, werden die Icons für Screenreader ausgeblendet, damit nichts doppelt vorgelesen wird.
  - [ ] Der E-Mail-Link öffnet das Mailprogramm.
- [ ] **Zweite Navigation „Legal“** mit Imprint, Privacy und Accessibility.
  Sie bekommt eine eigene Beschriftung, die sich von „Main“ unterscheidet.

**Fertig, wenn …**
- [ ] Der HTML-Validator meldet **keine Fehler**.
- [ ] Ohne CSS ergibt die Seite von oben nach unten gelesen Sinn.
- [ ] Du kannst mit **Tab** alle Links und Buttons der Reihe nach erreichen, und der Sprunglink kommt zuerst.
- [ ] Nach **Tab + Enter** auf dem Sprunglink steht der nächste Tab-Schritt im Hauptbereich.
- [ ] Der Barrierefreiheits-Inspektor zeigt die Landmarks *banner*, *navigation* (2×, mit unterschiedlichen Namen), *main* und *contentinfo*.
- [ ] Die Überschriften-Übersicht (z. B. mit einer Browser-Erweiterung wie „HeadingsMap“) zeigt eine lückenlose Hierarchie.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „Grundstruktur eines HTML-Dokuments“, „`<meta>`: charset, viewport, description“
- MDN: „`<link>`: rel, media, hreflang“, „`<script>`: defer, type=module“
- MDN: „HTML-Landmarks“ / „Sectioning elements“: `header`, `nav`, `main`, `section`, `footer`
- MDN: „`aria-label`“, „`aria-current`“, „globales Attribut lang“
- Begriffe: „Skip link“, „Open Graph Protocol“, „canonical URL“, „hreflang x-default“, „theme-color media“

</details>

---

### 1.2 Startseite – `index.html` (Inhalt)

**Ziel:** Ein Arbeitgeber versteht innerhalb von zehn Sekunden, wer du bist, was du kannst und wo er deine Projekte findet.

- [ ] **Hero / Intro**
  - [ ] h1 mit deinem Namen
  - [ ] deine Rolle in einer Zeile (z. B. „Junior Web Developer“)
  - [ ] ein bis zwei Sätze, wer du bist und was du suchst (Ausbildung, Festanstellung, Werkstudentenstelle …)
  - [ ] zwei Handlungslinks: „View projects“ (zur Projektübersicht) und „Contact me“ (zur Kontaktseite)
  - Diese beiden sind Links und keine Buttons, weil sie zu einer anderen Seite führen. Merke dir die Faustregel: **Links führen woanders hin, Buttons lösen eine Aktion aus.**
- [ ] **Featured Projects**
  - [ ] h2 „Featured Projects“
  - [ ] zwei bis drei Projektkarten, aufgebaut wie in 1.4 beschrieben. **Achtung:** Hier sind die Kartentitel **h3**, weil sie unter einer h2 stehen. In der Projektübersicht sind sie h2.
  - [ ] Solange es nur ein Projekt gibt (dieses Portfolio), zeigst du eben eine Karte.
  - [ ] Link „All projects“
- [ ] **Skills / Tech Stack**
  - [ ] h2 „Skills“
  - [ ] Gruppen mit h3, z. B. „Languages“, „Tools“, „Currently learning“
  - [ ] jede Gruppe als Liste
  - [ ] Nenne nur, was du wirklich einsetzen kannst. Im Vorstellungsgespräch wird danach gefragt.
- [ ] **Kontakt-Aufruf**
  - [ ] h2 (z. B. „Let's talk“)
  - [ ] ein Satz und ein Link zur Kontaktseite

**Fertig, wenn …**
- [ ] Der Validator zeigt keine Fehler.
- [ ] Die Überschriften-Hierarchie ist h1 → h2 → h3, ohne Sprünge.
- [ ] Kein Linktext ist „hier klicken“ oder „mehr“. Jeder Link ist auch ohne den Satz drumherum verständlich.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „`<ul>`, `<ol>`, `<li>`“, „`<section>` vs. `<article>`“
- Begriffe: „Link vs. Button Barrierefreiheit“, „aussagekräftige Linktexte“

</details>

---

### 1.3 Grundgerüst auf die anderen Seiten übertragen

**Ziel:** Alle englischen Seiten haben das fertige Grundgerüst aus 1.1. Die Hauptbereiche sind noch leer, bis auf die h1.

Mach diesen Schritt erst, wenn 1.1, 1.2 und die CSS-Grundlage (2.1 bis 2.4) fertig sind.

- [ ] Gerüst übertragen auf: `about.html`, `contact.html`, `contact-thanks.html`, `accessibility.html`, `imprint.html`, `privacy.html`, `404.html`, `projects/index.html` und `projects/_template.html`.

**Pro Seite anpassen** (hak die Liste für jede Seite gedanklich ab):
- [ ] Seitentitel
- [ ] Meta-Description
- [ ] Canonical-URL
- [ ] Sprachalternativen zeigen auf **diese** Seite in beiden Sprachen
- [ ] Open-Graph-Titel, -Beschreibung und -URL
- [ ] Sprachumschalter zeigt auf die passende deutsche Seite
- [ ] Die Kennzeichnung „aktuelle Seite“ in der Navigation steht beim richtigen Menüpunkt. Bei Seiten, die nicht in der Hauptnavigation stehen, steht sie bei keinem.
- [ ] neue h1

**Fertig, wenn …**
- [ ] Jede Seite besteht den Validator.
- [ ] Du kannst über die Navigation jede Seite erreichen, und es gibt keine toten Links.
- [ ] Der Sprachumschalter führt auf jeder Seite zur richtigen (noch leeren) deutschen Datei.

---

### 1.4 Projektübersicht – `projects/index.html`

**Ziel:** Alle Projekte auf einen Blick, nach Technologie filterbar.

- [ ] **h1 „Projects“** und ein einleitender Satz.
- [ ] **Filterbereich**
  - [ ] eine Reihe von Buttons: „All“ und je ein Button pro Technologie
  - [ ] Die Buttons sind als zusammengehörige Gruppe ausgezeichnet und beschriftet („Filter by technology“).
  - [ ] Der Filterbereich funktioniert erst mit JavaScript, und ohne JavaScript ist er später ausgeblendet (siehe 3.4).
- [ ] **Statusbereich** (vorerst leer)
  - [ ] ein Element, das Screenreader **automatisch vorlesen**, sobald sich sein Inhalt ändert
  - [ ] Später steht dort z. B. „Showing 3 of 5 projects“. Ohne diese Meldung merkt ein blinder Nutzer nicht, dass der Filter etwas bewirkt hat.
- [ ] **Projektliste** als Liste. Jede Projektkarte enthält:
  - [ ] **Vorschaubild**
    - mit einem Alternativtext, der beschreibt, was zu sehen ist
    - mit angegebener Breite und Höhe, damit die Seite beim Laden nicht springt
  - [ ] **Projekttitel als h2.** Der Titel ist der Link zur Projektseite.
  - [ ] **Kurzbeschreibung** in ein bis zwei Sätzen
  - [ ] **Technologie-Tags** als Liste
  - [ ] Die Karte enthält **nur einen einzigen Link**, nämlich den Titel. Dass später die ganze Karte anklickbar ist, löst du mit CSS (2.4). Mehrere Links auf dasselbe Ziel würden Screenreader und Tastaturnutzer doppelt durchlaufen.
  - [ ] Jede Karte trägt eine maschinenlesbare Information darüber, welche Technologien sie enthält. Diese braucht der Filter in 3.4.
- [ ] **Leerer Zustand:** ein Hinweis „More projects coming soon“, solange es nur wenige Projekte gibt.

**Fertig, wenn …**
- [ ] Die Tab-Reihenfolge ist: Filter-Buttons, dann pro Karte genau **ein** Tab-Stopp.
- [ ] Der Barrierefreiheits-Inspektor zeigt die Liste mit der richtigen Anzahl an Einträgen.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „`<fieldset>` und `<legend>`“ oder „ARIA group role“
- MDN: „ARIA live regions“, „`role="status"`“
- MDN: „`<img>`: alt, width, height“, „data-* Attribute“
- Begriffe: „Alternativtext schreiben“, „Cumulative Layout Shift“

</details>

---

### 1.5 Projektseite – `projects/_template.html`

**Ziel:** Eine Vorlage, mit der jedes Projekt wie eine kleine Fallstudie erzählt wird: Problem → Vorgehen → Ergebnis → Gelerntes. Arbeitgeber wollen sehen, **wie du denkst**, nicht nur das fertige Ergebnis.

> **Erstes Projekt: dieses Portfolio** (`projects/portfolio.html`).
> Wenn die Vorlage fertig ist, kopierst du sie nach `portfolio.html` und füllst sie mit der Geschichte dieser Website.
> - [ ] **Ab sofort ein Projekt-Tagebuch führen** (z. B. `docs/projekt-tagebuch.md`): Entscheidungen, Probleme und Lösungen, jeweils mit Datum. Daraus schreibst du später „Approach“ und „Challenges & Learnings“. Im Nachhinein erinnert man sich an die Hälfte nicht mehr.
> - [ ] **Demo-Idee auswählen.** Die Demo sollte zeigen, was dieses Projekt besonders macht: die Barrierefreiheit. Vorschläge:
>   - *Kontrast-Labor:* Text- und Hintergrundfarbe wählen, und das Kontrastverhältnis mit AA/AAA-Bewertung wird live angezeigt.
>   - *Schichten-Ansicht:* Dieselbe Komponente nur mit HTML, mit CSS und mit JavaScript, umschaltbar, um Progressive Enhancement zu zeigen.
>   - *Struktur-Ansicht:* Zeigt die Landmarks und Überschriften der Seite so an, wie ein Screenreader sie „sieht“.

- [ ] **Breadcrumb** (Home › Projects › Projektname)
  - [ ] als eigene, beschriftete Navigation („Breadcrumb“)
  - [ ] als geordnete Liste, denn die Reihenfolge hat eine Bedeutung
  - [ ] Der letzte Eintrag ist die aktuelle Seite und als solche gekennzeichnet.
  - [ ] Die Trennzeichen (›) werden von Screenreadern nicht vorgelesen.
- [ ] **Projektkopf**
  - [ ] h1 mit dem Projektnamen
  - [ ] Kurzbeschreibung in einem Satz
  - [ ] Metadaten: Zeitraum, deine Rolle, Technologien. Das ist eine Liste von Begriff–Wert-Paaren, und HTML hat dafür ein eigenes Listen-Element.
  - [ ] Zeitangaben sind maschinenlesbar ausgezeichnet.
  - [ ] Links „Live demo“ und „Source code“. Wenn ein Link die Seite verlässt, wird das im Linktext angekündigt.
- [ ] **Overview** (h2): Worum geht es und für wen ist es gedacht?
- [ ] **The Problem** (h2): Welches Problem löst das Projekt?
- [ ] **Approach** (h2): Wie bist du vorgegangen? Jeder wichtige Schritt oder jede Entscheidung bekommt eine h3.
- [ ] **Interactive Demo** (h2)
  - [ ] ein Absatz, was die Demo zeigt
  - [ ] eine Bedienungsanleitung (welche Tasten oder Steuerelemente)
  - [ ] ein leerer Container, in den JavaScript später die Demo lädt
  - [ ] eine **Textalternative**, die beschreibt, was man in der Demo erleben würde. Sie ist immer sichtbar oder zumindest ohne JavaScript sichtbar.
- [ ] **Challenges & Learnings** (h2): Was war schwierig, und was hast du gelernt? Arbeitgeber lesen diesen Teil besonders gern.
- [ ] **Screenshots** (h2)
  - [ ] Jedes Bild steht in einem Element mit Bildunterschrift.
  - [ ] Alternativtext und Bildunterschrift sagen nicht dasselbe. Der Alternativtext beschreibt das Bild, die Bildunterschrift ergänzt es.
- [ ] **Projekt-Navigation** am Ende: vorheriges Projekt, nächstes Projekt und zurück zur Übersicht.
  Die Linktexte nennen den Namen des Ziel-Projekts, nicht nur „Weiter“.

**Fertig, wenn …**
- [ ] Die Seite ergibt ohne CSS und ohne JavaScript vollständig Sinn, auch der Demo-Abschnitt.
- [ ] Ein Screenreader liest die Breadcrumb als „Navigation, Breadcrumb, Liste, 3 Einträge“ (sinngemäß).

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „`<ol>`“, „`<dl>`, `<dt>`, `<dd>`“, „`<time>`“, „`<figure>` und `<figcaption>`“
- MDN: „`<noscript>`“, „aria-hidden“
- Begriffe: „Breadcrumb Pattern WAI-ARIA APG“, „Case Study Portfolio Aufbau“

</details>

---

### 1.6 Über mich – `about.html`

**Ziel:** Ein Arbeitgeber lernt dich als Person kennen und findet deinen Lebenslauf.

- [ ] **Einleitung**
  - [ ] h1 „About me“
  - [ ] Profilfoto. Der Alternativtext ist dein Name, weil das Foto dich zeigt und dein Aussehen keine Information für die Seite ist.
  - [ ] kurze Einleitung in zwei bis drei Sätzen
- [ ] **Background** (h2): dein Werdegang als Fließtext, also wie du zur Webentwicklung gekommen bist.
- [ ] **Experience & Education** (h2)
  - [ ] chronologische Liste, die neuesten Einträge oben
  - [ ] jeder Eintrag mit Zeitraum, Station (Firma oder Schule) und kurzer Beschreibung
  - [ ] Datumsangaben maschinenlesbar ausgezeichnet
- [ ] **Skills** (h2)
  - [ ] Fähigkeiten in Gruppen
  - [ ] **keine** Prozentbalken oder Sterne. „HTML 80 %“ sagt nichts aus und ist für Screenreader schwer verständlich.
- [ ] **CV** (h2)
  - [ ] je ein Download-Link für die englische und die deutsche Version
  - [ ] Der Linktext nennt Sprache, Dateiformat und Größe, z. B. „CV (English, PDF, 120 KB)“, damit niemand unerwartet eine Datei herunterlädt.

**Fertig, wenn …**
- [ ] Der Validator zeigt keine Fehler, und die Hierarchie ist lückenlos.
- [ ] Die Download-Links verraten auch ohne Umgebungstext, was man herunterlädt.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „`<a>`: download“, „`<time>` datetime“
- Begriffe: „Barrierefreies PDF erstellen“ (gilt für deinen Lebenslauf)

</details>

---

### 1.7 Kontakt – `contact.html` und `contact-thanks.html`

**Ziel:** Man kann dich ohne Umwege erreichen, entweder direkt per E-Mail oder über ein Formular, das jeder bedienen kann.

- [ ] h1 „Contact“
- [ ] ein einleitender Satz: wofür man dich kontaktieren kann und wie schnell du antwortest
- [ ] **Kontaktwege** (h2) als Liste: E-Mail, LinkedIn, GitHub
  - [ ] Die E-Mail-Adresse ist als Text sichtbar, nicht nur als Link „Write me“. Manche Nutzer haben kein Mailprogramm eingerichtet und wollen die Adresse kopieren.
- [ ] **Kontaktformular** (h2 „Send a message“), das über Netlify Forms verschickt wird
  - [ ] Das Formular ist für Netlify als Formular markiert und hat einen Namen.
  - [ ] Felder: Name, E-Mail, Nachricht
  - [ ] Jedes Feld hat ein **sichtbares** Label, das mit dem Feld verbunden ist. Ein Platzhaltertext im Feld ersetzt kein Label, denn er verschwindet beim Tippen.
  - [ ] Pflichtfelder sind im HTML als Pflichtfelder gekennzeichnet **und** im Label sichtbar markiert. Vor dem Formular steht ein Satz, was die Markierung bedeutet.
  - [ ] Das E-Mail-Feld hat den passenden Feldtyp, damit Smartphones die richtige Tastatur zeigen.
  - [ ] Name und E-Mail können vom Browser automatisch ausgefüllt werden.
  - [ ] **Spamschutz** über ein verstecktes Lockfeld (Honeypot), das Menschen nicht sehen und Screenreader nicht vorlesen. Kein CAPTCHA, denn CAPTCHAs sind eine der größten Barrieren im Web.
  - [ ] Ein Hinweis mit Link zur Datenschutzerklärung erklärt, was mit den Daten passiert.
  - [ ] Der Absende-Button hat einen eindeutigen Text, z. B. „Send message“ und nicht nur „Send“.
  - [ ] Nach dem Absenden landet man auf `contact-thanks.html` (deutsch: `/de/contact-thanks.html`).
- [ ] **Bestätigungsseite** `contact-thanks.html`
  - [ ] h1, z. B. „Thank you, your message has been sent“
  - [ ] ein Satz, wann du antwortest
  - [ ] Links zurück zur Startseite und zu den Projekten
- [ ] **Fehlermeldungen** (zusammen mit Phase 3 umsetzen, siehe 3.6):
  - [ ] Ohne JavaScript übernimmt der Browser die Prüfung der Pflichtfelder.
  - [ ] Mit JavaScript erscheinen eigene Fehlermeldungen als Text direkt am Feld. Sie sind mit dem Feld verbunden, sodass der Screenreader sie vorliest. Die Meldung sagt, **was** falsch ist und **wie** man es behebt.
  - [ ] Nach einem fehlgeschlagenen Absenden springt der Fokus zum ersten fehlerhaften Feld.

**Fertig, wenn …**
- [ ] Du das Formular nur mit der Tastatur ausfüllen und absenden kannst.
- [ ] Ein Screenreader beim Betreten jedes Felds Label, Feldtyp und „Pflichtfeld“ vorliest.
- [ ] Nach dem Deployment eine Testnachricht im Netlify-Dashboard unter „Forms“ ankommt.
- [ ] Das Lockfeld weder sichtbar ist noch per Tab erreicht oder vorgelesen wird.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- Netlify Docs: „Forms setup“, „Spam filters honeypot“, „custom success page“
- MDN: „`<form>`“, „`<label>` for“, „`<input>` type email“, „required“, „autocomplete“
- MDN: „aria-describedby“, „aria-invalid“, „Constraint Validation API“
- Begriffe: „Accessible form validation“, „WCAG 3.3.1 Error Identification“, „WCAG 3.3.3 Error Suggestion“

</details>

---

### 1.8 Rechtliche Seiten – `imprint.html`, `privacy.html`

**Ziel:** Die Seite ist in Deutschland rechtssicher.

- [ ] Inhalte mit einem seriösen Generator erstellen (z. B. von e-recht24 oder Dr. Schwenke) und an deinen Hoster anpassen.
- [ ] Den generierten Inhalt in **deine** Struktur übertragen: h1, Abschnitte mit h2, Listen und Absätze. Generatoren liefern oft unsauberes HTML, kopier es nicht 1:1.
- [ ] Beide Seiten auch auf Englisch anbieten. Die deutsche Fassung ist rechtlich maßgeblich, das kannst du auf der englischen Seite vermerken.
- [ ] Die Datenschutzerklärung nennt **Netlify** als Hoster (mit Sitz in den USA, Server-Logs) und erklärt, was mit den Daten aus dem **Kontaktformular** passiert.

---

### 1.9 Barrierefreiheit – `accessibility.html`

**Ziel:** Du zeigst, dass du Barrierefreiheit bewusst und ehrlich umgesetzt hast.

- [ ] h1 „Accessibility“
- [ ] **Standard** (h2): welcher Standard angestrebt wird (WCAG 2.2, Stufe AA) und wann du zuletzt geprüft hast
- [ ] **What I did** (h2): eine Liste der umgesetzten Maßnahmen. Füll sie während des Programmierens, dann vergisst du nichts.
- [ ] **How I tested** (h2): Werkzeuge und Methoden (aus Phase 4)
- [ ] **Known limitations** (h2): eine ehrliche Liste der bekannten Einschränkungen. Ehrlichkeit wirkt hier glaubwürdiger als Perfektion.
- [ ] **Feedback** (h2): wie man dir Barrieren melden kann

---

### 1.10 Fehlerseite – `404.html`

**Ziel:** Wer sich verirrt, findet ohne Frust zurück.

- [ ] h1 mit einer verständlichen Meldung, z. B. „Page not found“, nicht nur „404“
- [ ] ein Satz, was passiert sein könnte (veralteter Link, Tippfehler)
- [ ] Links zur Startseite und zur Projektübersicht
- [ ] Der Sprachumschalter führt zur deutschen 404-Seite.
- [ ] Netlify zeigt `/404.html` automatisch an. Damit unter `/de/…` die deutsche Fehlerseite erscheint, brauchst du eine Regel in `_redirects` (siehe 1.12).

**Fertig, wenn …**
- [ ] Die Seite sieht auch dann korrekt aus, wenn du sie über eine tiefe, nicht existierende Adresse aufrufst, z. B. `/projects/gibt/es/nicht`. Das funktioniert nur mit wurzel-relativen Pfaden.

---

### 1.11 Deutsche Version – `de/`

**Ziel:** Jede englische Seite hat eine vollständige deutsche Entsprechung.

Fang erst an, wenn die englische Version **fertig** ist (inklusive CSS und JS).

- [ ] Jede englische Seite nach `de/` kopieren, mit **gleichem** Dateinamen.
- [ ] Pro Seite übersetzen bzw. anpassen:
  - [ ] Sprachattribut auf Deutsch
  - [ ] Seitentitel, Meta-Description und Open-Graph-Texte
  - [ ] alle sichtbaren Texte
  - [ ] alle **unsichtbaren** Texte: Alternativtexte, Beschriftungen von Navigationen und Buttons, Texte nur für Screenreader. Diese werden am häufigsten vergessen.
  - [ ] Links innerhalb der Seite zeigen auf deutsche Seiten (`/de/…`).
  - [ ] Canonical-URL zeigt auf die deutsche Seite.
  - [ ] Der Sprachumschalter zeigt auf die englische Seite und heißt „English“.
  - [ ] Datumsformate in deutscher Schreibweise
- [ ] Texte, die per JavaScript erzeugt werden (z. B. „Showing 3 of 5 projects“), müssen ebenfalls übersetzt werden. Überleg dir, woher das Skript weiß, welche Sprache gilt.

**Fertig, wenn …**
- [ ] Ein Screenreader liest auf deutschen Seiten **kein** englisches Wort mit deutscher Aussprache vor, und umgekehrt.
- [ ] Der Sprachumschalter führt von jeder Seite zur exakt gleichen Seite in der anderen Sprache und wieder zurück.

---

### 1.12 Weitere Dateien

- [ ] **`robots.txt`**: erlaubt Suchmaschinen den Zugriff und verweist auf die Sitemap.
- [ ] **`sitemap.xml`**: listet alle Seiten beider Sprachen mit vollständigen URLs auf. Lass `_template.html` und die 404-Seite weg.
- [ ] **`site.webmanifest`**: Name, Kurzname, Icons, Hintergrund- und Theme-Farbe.
- [ ] **Favicons**
  - [ ] SVG-Favicon, das im dunklen Browser-Modus gut sichtbar bleibt
  - [ ] ICO als Rückfallebene für alte Browser
  - [ ] Apple-Touch-Icon in 180 × 180 px
- [ ] **`_template.html`** wird von Suchmaschinen nicht erfasst.
- [ ] **`_redirects`**: Bei unbekannten Adressen unter `/de/` wird die deutsche 404-Seite mit dem Statuscode 404 ausgeliefert.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- Begriffe: „robots.txt Syntax“, „sitemap.xml hreflang“, „Web App Manifest MDN“
- Begriffe: „SVG favicon prefers-color-scheme“, „meta robots noindex“
- Netlify Docs: „Redirects and rewrites“, „Custom 404 page handling“

</details>

---

## Phase 2 – CSS

### 2.1 Grundlage

**Ziel:** Ein einheitlicher Startpunkt und ein zentraler Ort für alle Design-Werte.

- [ ] **`reset.css`**: gleicht Unterschiede zwischen den Browsern aus.
  Du darfst dich an bekannten modernen Resets orientieren. Übernimm aber nur Regeln, die du verstehst, und schreib zu jeder Regel einen Kommentar, warum sie da ist.
- [ ] **`tokens.css`**: alle Design-Werte als Variablen
  - [ ] die Farben aus Phase 0, mit **gleichen Variablennamen** für hell und dunkel. Nur die Werte unterscheiden sich.
  - [ ] eine Schriftgrößen-Skala (z. B. 6 bis 8 Stufen)
  - [ ] eine Abstands-Skala
  - [ ] Eckenradien, maximale Inhaltsbreite, Dauer von Übergängen
  - [ ] Der dunkle Satz greift, wenn das System dunkel eingestellt ist **oder** wenn die Seite manuell auf dunkel gestellt wurde (Phase 3.3).
  - [ ] Der Browser weiß, welche Farbschemata die Seite unterstützt, damit Scrollbalken und Formularelemente im Dunkelmodus ebenfalls dunkel dargestellt werden.
- [ ] **Schriften**
  - [ ] Schriftdateien im modernen, komprimierten Format in `assets/fonts/` ablegen
  - [ ] die Lizenzdateien der Schriften mit ablegen
  - [ ] Während die Schrift lädt, ist der Text in einer Systemschrift sichtbar, statt unsichtbar zu sein.
  - [ ] Es gibt eine passende Liste von Ersatzschriften.

**Fertig, wenn …**
- [ ] In keiner anderen CSS-Datei steht ein fester Farbwert. Alle Farben kommen aus `tokens.css`.
- [ ] Im Netzwerk-Reiter der Entwicklerwerkzeuge werden die Schriften von deiner eigenen Adresse geladen, nicht von Google.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „CSS custom properties“, „`@font-face`“, „font-display“, „woff2“
- MDN: „prefers-color-scheme“, „color-scheme“, „Attributselektoren“
- Begriffe: „modern CSS reset“, „type scale“, „google-webfonts-helper“

</details>

---

### 2.2 Typografie und Grundelemente (`base.css`)

**Ziel:** Text ist angenehm lesbar, und jedes interaktive Element ist eindeutig erkennbar.

- [ ] **Schriftgrößen in relativen Einheiten**, keine festen Pixel.
  Wer im Browser eine größere Standardschrift eingestellt hat, braucht sie aus gutem Grund.
- [ ] **Überschriften** verwenden Größen aus deiner Skala und unterscheiden sich deutlich voneinander.
- [ ] **Zeilenlänge** im Fließtext auf etwa 60 bis 75 Zeichen begrenzt.
  Lange Zeilen ermüden beim Lesen, weil das Auge den Anfang der nächsten Zeile verliert.
- [ ] **Zeilenhöhe** im Fließtext mindestens 1,5.
- [ ] **Nutzer-Abstände dürfen nichts kaputt machen.** Wenn ein Nutzer Zeilen-, Wort- oder Buchstabenabstand vergrößert, darf kein Text abgeschnitten werden oder überlappen. Vermeide deshalb feste Höhen bei Textcontainern.
- [ ] **Links**
  - [ ] im Fließtext unterstrichen
  - [ ] Hover-Zustand nicht nur über die Farbe erkennbar (z. B. durch eine veränderte Unterstreichung)
  - [ ] Besuchte Links dürfen gleich aussehen, das ist bei einem Portfolio in Ordnung.
- [ ] **Fokus-Stil**
  - [ ] für **alle** interaktiven Elemente deutlich sichtbar: Links, Buttons, Formularfelder
  - [ ] erscheint bei Tastaturbedienung, nicht beim Mausklick
  - [ ] in Akzentfarbe mit mindestens 3 : 1 Kontrast zum Hintergrund, mit etwas Abstand zum Element
  - [ ] Der Fokus-Stil wird **niemals** einfach entfernt, ohne Ersatz.
- [ ] **Sprunglink**: unsichtbar, bis er per Tastatur fokussiert wird. Dann erscheint er gut sichtbar oben links.
- [ ] **Hilfsklasse „nur für Screenreader“**: Der Text ist unsichtbar, wird aber vorgelesen.
  Achtung: Das ist etwas anderes als „ausgeblendet“. Ausgeblendete Elemente liest auch der Screenreader nicht vor.
- [ ] **Textmarkierung** (wenn man Text mit der Maus auswählt) hat guten Kontrast.

**Fertig, wenn …**
- [ ] Wenn du im Browser die Standard-Schriftgröße auf „sehr groß“ stellst, wächst der Text mit.
- [ ] Beim Durchtabben siehst du **immer**, wo der Fokus gerade ist, in beiden Farbmodi.
- [ ] Ein Klick mit der Maus auf einen Button zeigt keinen störenden Fokus-Rahmen.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „rem vs em“, „`clamp()`“, „Einheit ch“, „line-height“
- MDN: „`:focus-visible`“, „outline-offset“, „text-decoration-thickness“, „text-underline-offset“
- Begriffe: „visually hidden CSS“, „WCAG 1.4.12 Text Spacing“, „WCAG 2.4.7 Focus Visible“

</details>

---

### 2.3 Layout (`layout.css`)

**Ziel:** Die Seite funktioniert auf jedem Gerät, vom kleinen Smartphone bis zum großen Monitor.

- [ ] **Mobile-first**: Die Grundregeln gelten für schmale Bildschirme. Für breitere Bildschirme kommen Erweiterungen hinzu.
- [ ] **Inhalts-Container**: maximale Breite, horizontal zentriert und mit seitlichem Abstand, damit Text nie am Bildschirmrand klebt.
- [ ] **Header**
  - [ ] Auf breiten Bildschirmen stehen Logo, Navigation, Sprach- und Theme-Umschalter nebeneinander.
  - [ ] Auf schmalen Bildschirmen ist die Navigation hinter dem Menü-Button versteckt, **aber nur, wenn JavaScript verfügbar ist**. Ohne JavaScript ist sie immer sichtbar, notfalls umgebrochen.
  - [ ] Wenn der Header beim Scrollen oben fixiert ist: Ein fokussiertes Element darf **nie** vom Header verdeckt werden, auch nicht beim Sprung über den Sprunglink.
- [ ] **Footer**: auf schmalen Bildschirmen untereinander, auf breiten nebeneinander.
- [ ] **Abstände** zwischen Abschnitten kommen aus der Abstands-Skala.
- [ ] **Reflow**: Bei 320 px Breite und bei 400 % Zoom gibt es kein horizontales Scrollen, und kein Inhalt geht verloren.

**Fertig, wenn …**
- [ ] Du in den Entwicklerwerkzeugen (Geräte-Modus) die Breite von 320 px bis 1920 px ziehst und das Layout nirgends bricht.
- [ ] Der Header bei 400 % Zoom nicht den halben Bildschirm verdeckt.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „Flexbox“, „CSS Grid“, „Media Queries min-width“, „`margin-inline`“
- MDN: „position: sticky“, „scroll-padding-top“
- Begriffe: „WCAG 1.4.10 Reflow“, „WCAG 2.4.11 Focus Not Obscured“
- Spielerisch üben: „Flexbox Froggy“, „Grid Garden“

</details>

---

### 2.4 Komponenten (`components.css`)

**Ziel:** Wiederverwendbare Bausteine, die auf jeder Seite gleich aussehen und sich gleich verhalten.

- [ ] **Buttons und Handlungslinks**
  - [ ] sichtbar unterschiedliche Zustände für Normal, Hover, Fokus, Aktiv (gedrückt) und Deaktiviert
  - [ ] Eine primäre Variante (gefüllt) und eine sekundäre Variante (umrandet) genügen.
  - [ ] Ein Handlungslink, der wie ein Button aussieht, bleibt im HTML trotzdem ein Link.
- [ ] **Klickflächen** mindestens 24 × 24 px, besser 44 × 44 px. Das gilt besonders für Icon-Buttons und Links in der Navigation.
- [ ] **Projektkarten**
  - [ ] Die ganze Karte reagiert auf Klicks, obwohl im HTML nur der Titel ein Link ist.
  - [ ] Text in der Karte bleibt trotzdem markierbar, oder du nimmst bewusst in Kauf, dass er es nicht ist.
  - [ ] Der Fokus-Rahmen umschließt die ganze Karte.
  - [ ] Hover-Effekt ist dezent, z. B. ein Schatten oder Rahmen, keine großen Bewegungen.
- [ ] **Listen ohne Aufzählungszeichen** (Navigation, Tags, Projektliste) bleiben für Screenreader trotzdem Listen. In Safari ist das ein bekanntes Problem.
- [ ] **Technologie-Tags**: klein, aber lesbar (nicht kleiner als 14 px) und mit ausreichendem Kontrast.
- [ ] **Filter-Buttons**: Der ausgewählte Zustand ist nicht nur über die Farbe erkennbar (z. B. zusätzlich über ein Häkchen, einen Rahmen oder Fettdruck).
- [ ] **Breadcrumb**: Einträge in einer Reihe, Trennzeichen per CSS erzeugt.
- [ ] **Bilder** werden nie breiter als ihr Container und behalten ihr Seitenverhältnis.
- [ ] **Formularfelder**
  - [ ] Rahmen mit mindestens 3 : 1 Kontrast zum Hintergrund, damit man erkennt, wo man klicken kann
  - [ ] Label steht über dem Feld, nicht daneben, damit es bei Zoom nicht abgeschnitten wird
  - [ ] Fehlerzustand nicht nur rot, sondern zusätzlich mit Text und einem Symbol
  - [ ] Das Lockfeld (Honeypot) ist für alle unsichtbar.

**Fertig, wenn …**
- [ ] Alle Zustände der Buttons sind in beiden Farbmodi unterscheidbar.
- [ ] Klickst du irgendwo auf eine Projektkarte, öffnet sich die Projektseite, und die Karte hat trotzdem nur einen Tab-Stopp.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „`:hover`, `:active`, `:disabled`“, „`::before` / `::after`“, „`:focus-within`“
- Begriffe: „Block link / stretched link pattern“, „Inclusive Components Cards“ (Heydon Pickering)
- Begriffe: „list-style none Safari VoiceOver“, „WCAG 2.5.8 Target Size“
- MDN: „aspect-ratio“, „object-fit“

</details>

---

### 2.5 Seiten und Demos (`pages.css`, `demos.css`)

**Ziel:** Jede Seite bekommt ihr eigenes Layout, gebaut aus den vorhandenen Bausteinen.

- [ ] **Startseite – Hero**: großzügig, der Name steht klar im Mittelpunkt. Kein Hintergrundbild, das die Lesbarkeit stört.
- [ ] **Projektübersicht**: Raster mit einer Spalte (schmal), zwei Spalten (mittel) und drei Spalten (breit).
- [ ] **Projektseite**: gut lesbare Textspalte. Screenshots dürfen breiter sein als der Text.
- [ ] **About – Lebenslauf-Zeitleiste**: Die Einträge sind optisch als zeitliche Abfolge erkennbar.
- [ ] **Demos**
  - [ ] Container mit Rahmen, damit klar ist, wo die Demo beginnt und endet
  - [ ] Steuerelemente der Demo verwenden die Button-Stile aus 2.4.

---

### 2.6 Nutzerpräferenzen

**Ziel:** Die Seite respektiert die Einstellungen, die Nutzer in ihrem System gewählt haben.

- [ ] **Farbschema**: Standardmäßig folgt die Seite der Systemeinstellung (hell oder dunkel).
- [ ] **Manuelle Wahl** über den Button überschreibt die Systemeinstellung (Zusammenspiel mit 3.3).
- [ ] **Reduzierte Bewegung**: Wer im System „Bewegung reduzieren“ eingestellt hat, bekommt keine Animationen, keine Übergänge und kein weiches Scrollen.
  Für Menschen mit Gleichgewichtsstörungen können Bewegungen auf dem Bildschirm Schwindel und Übelkeit auslösen.
- [ ] **Erzwungene Farben** (Windows-Kontrastmodus): Rahmen, Fokus und Buttons bleiben sichtbar. Achtung: In diesem Modus verschwinden Hintergrundfarben und Schatten.

**Fertig, wenn …**
- [ ] Du in den Entwicklerwerkzeugen das Farbschema, reduzierte Bewegung und erzwungene Farben simuliert hast und alles nutzbar bleibt.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „prefers-reduced-motion“, „forced-colors“, „prefers-contrast“
- Chrome DevTools: „Rendering → Emulate CSS media feature“

</details>

---

### 2.7 Druck (`print.css`)

**Ziel:** Ein Arbeitgeber druckt deine Projektseite aus, und sie ist auf Papier gut lesbar.

- [ ] Navigation, Buttons, Sprunglink, Theme-Umschalter und Demos sind ausgeblendet.
- [ ] Schwarzer Text auf weißem Hintergrund, unabhängig vom gewählten Farbmodus.
- [ ] Bei Links steht die Adresse in Klammern hinter dem Linktext, denn auf Papier kann man nicht klicken.
- [ ] Überschriften stehen nie allein am Ende einer Seite, und Bilder werden nicht zerschnitten.

**Fertig, wenn …**
- [ ] Die Druckvorschau (Strg + P) zeigt ein sauberes Dokument.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „@media print“, „`attr()` in content“, „break-inside“, „break-after“

</details>

---

## Phase 3 – JavaScript

Für jede Funktion gilt: Ohne JavaScript ist die Seite trotzdem vollständig nutzbar. JavaScript **verbessert** die Seite, es ist nicht Voraussetzung dafür.

### 3.1 Einstieg (`main.js`)

**Ziel:** Ein zentraler Startpunkt, der die übrigen Skripte lädt.

- [ ] `main.js` lädt die übrigen Skripte als Module. Jedes Modul ist für genau eine Aufgabe zuständig.
- [ ] Module, die auf einer Seite nicht gebraucht werden, laufen dort ohne Fehler ins Leere. Zum Beispiel darf der Projektfilter auf der About-Seite keinen Fehler werfen.
- [ ] Sobald JavaScript läuft, wird am Dokument eine **Markierung** gesetzt. Das CSS kann damit unterscheiden, ob JavaScript verfügbar ist, und zum Beispiel erst dann den Menü-Button zeigen und die Navigation verstecken.

**Fertig, wenn …**
- [ ] Die Konsole zeigt auf **keiner** Seite Fehler.
- [ ] Wenn du JavaScript im Browser abschaltest, verschwinden Menü-Button, Theme-Button und Filter, und alles andere funktioniert.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „JavaScript-Module (import/export)“, „document.documentElement“, „classList“
- Begriffe: „Progressive Enhancement“, „JavaScript deaktivieren Firefox about:config“

</details>

---

### 3.2 Mobile Navigation (`navigation.js`)

**Ziel:** Auf schmalen Bildschirmen öffnet und schließt ein Button die Navigation, auch per Tastatur und für Screenreader verständlich.

- [ ] Ein Klick auf den Menü-Button öffnet die Navigation, ein zweiter Klick schließt sie.
- [ ] Der Button teilt Screenreadern seinen Zustand mit (offen oder geschlossen) und welches Element er steuert.
- [ ] Die **Escape**-Taste schließt das offene Menü. Danach liegt der Fokus wieder auf dem Menü-Button.
- [ ] Ein Klick auf einen Menüpunkt schließt das Menü.
- [ ] Wenn das Fenster breiter wird und die Desktop-Navigation erscheint, ist kein „halb offener“ Zustand übrig.
- [ ] Ohne JavaScript ist die Navigation immer sichtbar (siehe 2.3).

**Fertig, wenn …**
- [ ] Du das Menü nur mit der Tastatur öffnen, durchlaufen und mit Escape schließen kannst.
- [ ] Der Barrierefreiheits-Inspektor beim Button „expanded: true/false“ passend zum Zustand anzeigt.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „addEventListener“, „click event“, „keydown event“, „KeyboardEvent.key“
- MDN: „aria-expanded“, „aria-controls“, „hidden-Attribut“, „focus()“
- Begriffe: „Disclosure Navigation Pattern WAI-ARIA APG“, „matchMedia change event“

</details>

---

### 3.3 Theme-Umschalter (`theme.js`)

**Ziel:** Nutzer können zwischen hell und dunkel wechseln, und die Seite merkt sich die Wahl.

- [ ] Ein Klick wechselt zwischen hell und dunkel.
- [ ] Der Button teilt Screenreadern mit, welcher Modus gerade aktiv ist. Sein Name passt zur Aktion.
- [ ] Die Wahl wird im Browser **gespeichert** und beim nächsten Besuch wiederhergestellt, auch auf allen anderen Unterseiten.
- [ ] Ohne gespeicherte Wahl gilt die Systemeinstellung.
- [ ] **Kein Aufblitzen**: Wer dunkel gewählt hat, sieht beim Laden nie kurz die helle Seite.
  Das ist knifflig. Überleg dir, *wann* dein Code laufen muss, damit er vor dem ersten Zeichnen der Seite fertig ist. Ein normales Modul läuft dafür zu spät.
- [ ] Wenn das Speichern im Browser blockiert ist (privater Modus, Datenschutz-Einstellungen), funktioniert der Button trotzdem. Er merkt sich die Wahl dann eben nicht.
- [ ] *Optional:* eine dritte Option „System“, mit der man zur Systemeinstellung zurückkehrt.

**Fertig, wenn …**
- [ ] Nach einem Neuladen mit gewähltem Dunkelmodus ist kein heller Blitz zu sehen.
- [ ] Die Wahl bleibt beim Wechsel auf eine andere Seite und beim Sprachwechsel erhalten.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „localStorage“, „try…catch“, „window.matchMedia“, „dataset“
- MDN: „aria-pressed“
- Begriffe: „Flash of incorrect theme (FOIT / FART)“, „inline script im head“

</details>

---

### 3.4 Projektfilter (`project-filter.js`)

**Ziel:** Ein Arbeitgeber findet schnell die Projekte mit der Technologie, die ihn interessiert.

- [ ] Ein Klick auf einen Filter zeigt nur die Projekte, die zur Technologie passen. Alle anderen werden ausgeblendet, auch für Screenreader.
- [ ] Der aktive Filter teilt Screenreadern mit, dass er ausgewählt ist. Es ist immer genau ein Filter aktiv.
- [ ] Der Statusbereich aus 1.4 meldet nach jedem Filtern die Anzahl der Treffer.
- [ ] „All“ zeigt wieder alle Projekte.
- [ ] Der Fokus bleibt nach dem Klick auf dem Filter-Button und springt nicht weg.
- [ ] Ohne JavaScript sind alle Projekte sichtbar, und die Filter-Buttons sind ausgeblendet.
- [ ] *Optional:* Der gewählte Filter steht in der Adresse (z. B. `?tech=javascript`). So kann man einen gefilterten Link teilen, und der Zurück-Button funktioniert.
- [ ] Die Statusmeldung erscheint in der Sprache der Seite (siehe 1.11).

**Fertig, wenn …**
- [ ] Ein Screenreader nach dem Filtern „Showing 2 of 5 projects“ (sinngemäß) vorliest, ohne dass du dorthin navigierst.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „querySelectorAll“, „forEach“, „dataset“, „hidden-Attribut“, „textContent“
- MDN: „aria-pressed“, „URLSearchParams“, „history.replaceState“
- Begriffe: „ARIA live region polite“

</details>

---

### 3.5 Interaktive Projekt-Demos (`demos/*.js`)

**Ziel:** Projekte lassen sich direkt auf der Seite ausprobieren, für alle Nutzer.

Die genaue Umsetzung hängt vom jeweiligen Projekt ab. Diese Anforderungen gelten aber für **jede** Demo:

- [ ] **Tastatur**: Alles ist ohne Maus bedienbar, und die Reihenfolge ist logisch.
- [ ] **Beschriftung**: Jedes Steuerelement hat eine sichtbare Beschriftung, die auch der Screenreader vorliest.
- [ ] **Rückmeldung**: Ergebnisse und Änderungen werden Screenreadern angekündigt, nicht nur optisch angezeigt.
- [ ] **Keine Anfallsgefahr**: Nichts blinkt mehr als dreimal pro Sekunde.
- [ ] **Kontrolle**: Nichts startet automatisch. Alles, was sich bewegt, kann man anhalten.
- [ ] **Reduzierte Bewegung**: Ist sie eingestellt, verzichtet die Demo auf Animationen oder zeigt nur das Endergebnis.
- [ ] **Performance**: Das Demo-Skript wird erst geladen, wenn die Demo gebraucht wird, z. B. erst nach einem Klick auf „Start demo“ oder wenn sie in den sichtbaren Bereich scrollt.
- [ ] **Rückfallebene**: Ohne JavaScript bleibt die Textalternative aus 1.5 sichtbar.
- [ ] **Fehler**: Wenn das Laden scheitert, sieht der Nutzer eine verständliche Meldung statt einer leeren Fläche.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „dynamic import()“, „IntersectionObserver“, „Promise / async await“
- Begriffe: „WCAG 2.3.1 Three Flashes“, „WCAG 2.2.2 Pause, Stop, Hide“

</details>

---

### 3.6 Kontaktformular (`contact-form.js`, neue Datei)

**Ziel:** Fehler im Formular werden früh, verständlich und für alle wahrnehmbar gemeldet.

- [ ] Die Prüfung findet beim Absenden statt, nicht bei jedem Tastendruck. Meldungen, die schon während des Tippens erscheinen, wirken störend und werden ständig vorgelesen.
- [ ] Bei Fehlern wird nicht abgeschickt. Jede Fehlermeldung erscheint als Text am Feld (siehe 1.7).
- [ ] Felder mit Fehlern sind für Screenreader als „ungültig“ gekennzeichnet. Sobald der Fehler behoben ist, verschwindet die Kennzeichnung.
- [ ] Der Fokus springt zum ersten fehlerhaften Feld.
- [ ] Fehlermeldungen erscheinen in der Sprache der Seite.
- [ ] Ohne JavaScript übernimmt die Prüfung des Browsers (siehe 1.7).

<details>
<summary>Hinweise zum Nachschlagen</summary>

- MDN: „submit event“, „preventDefault“, „Constraint Validation API“, „novalidate“
- MDN: „aria-invalid“, „aria-describedby“

</details>

---

## Phase 4 – Prüfen und Testen

### 4.1 Barrierefreiheit

- [ ] **Tastatur-Test** (nach jeder fertigen Seite). Maus weglegen und mit Tab, Umschalt + Tab, Enter, Leertaste und Escape arbeiten:
  - Ist alles erreichbar?
  - Ist die Reihenfolge logisch?
  - Ist der Fokus immer sichtbar und nie verdeckt?
  - Gibt es keine Stelle, an der man „gefangen“ ist?
- [ ] **Screenreader-Test** mit NVDA (kostenlos, Windows). Navigiere über Überschriften, Landmarks und Links und achte darauf, ob alles verständlich vorgelesen wird.
- [ ] **Automatische Tests** mit Lighthouse und axe DevTools auf **jeder** Seite.
  Achtung: Automatische Tests finden nur etwa ein Drittel aller Probleme. Sie ersetzen den Tastatur- und den Screenreader-Test nicht.
- [ ] **HTML-Validierung** jeder Seite (validator.w3.org/nu)
- [ ] **Zoom** auf 200 % und 400 %
- [ ] **Bildschirmbreite** 320 px
- [ ] **Beide Farbmodi**, reduzierte Bewegung und erzwungene Farben getestet
- [ ] **Alternativtexte** aller Bilder geprüft: Sind sie sinnvoll? Sind dekorative Bilder als dekorativ markiert?
- [ ] **Ergebnisse** auf `accessibility.html` eingetragen

### 4.2 Qualität

- [ ] Test in Firefox, Chrome oder Edge und Safari (oder einem anderen WebKit-Browser, z. B. GNOME Web)
- [ ] Test auf einem echten Smartphone, nicht nur im Geräte-Modus der Entwicklerwerkzeuge
- [ ] Keine toten Links (es gibt Link-Checker als Browser-Erweiterung oder Webseite)
- [ ] Bilder komprimiert, in modernen Formaten und mit angegebenen Abmessungen
- [ ] Lighthouse-Werte für Performance, Barrierefreiheit, Best Practices und SEO notiert. Ziel: überall 90 oder mehr.
- [ ] Keine Fehler und keine Warnungen in der Browser-Konsole

### 4.3 Veröffentlichung (Netlify + Porkbun)

Mach diesen Schritt früh, am besten gleich nach 1.2. Dann siehst du jeden Fortschritt live, und Fehler beim Deployment fallen nicht erst am Ende auf.

- [ ] Netlify mit dem GitHub-Repository verbinden. Jeder Push auf `main` wird automatisch veröffentlicht.
- [ ] Domain von Porkbun per DNS auf Netlify zeigen lassen (beide Varianten: mit und ohne `www`, eine leitet auf die andere weiter).
- [ ] HTTPS in Netlify aktiviert, und `http://` leitet automatisch auf `https://` weiter.
- [ ] Alle Platzhalter-URLs (Canonical, Sprachalternativen, Open Graph, Sitemap) durch die echte Domain ersetzt.
- [ ] Die deutsche 404-Seite funktioniert über `_redirects`.
- [ ] Netlify Forms aktiviert und eine Testnachricht empfangen. Benachrichtigung per E-Mail eingerichtet.
- [ ] Keine leeren Platzhalter-Dateien online (Lebenslauf-PDFs, Favicons).
- [ ] Impressum und Datenschutz für Netlify und das Formular angepasst.
- [ ] Link-Vorschau getestet, z. B. mit dem LinkedIn Post Inspector.

<details>
<summary>Hinweise zum Nachschlagen</summary>

- Netlify Docs: „Import from an existing repository“, „Configure external DNS for a custom domain“, „HTTPS (SSL)“
- Porkbun: „How to connect your domain to Netlify“
- Begriffe: „A record“, „CNAME“, „apex domain vs. www“

</details>

---

## Glossar

| Begriff | Bedeutung |
|---|---|
| **Screenreader** | Software, die Bildschirminhalte vorliest oder auf einer Braillezeile ausgibt. Blinde und sehbehinderte Menschen nutzen sie. |
| **Fokus** | Das Element, das gerade Tastatureingaben empfängt. Mit Tab bewegst du ihn weiter. |
| **Landmark** | Ein Hauptbereich der Seite (Header, Navigation, Main, Footer). Screenreader-Nutzer können direkt dorthin springen. |
| **Alternativtext** | Eine Textbeschreibung eines Bildes. Sie wird vorgelesen oder angezeigt, wenn das Bild nicht geladen wird. |
| **Live-Region** | Ein Bereich, dessen Änderungen ein Screenreader automatisch vorliest. |
| **WCAG** | Web Content Accessibility Guidelines, der internationale Standard für barrierefreie Webinhalte. Stufe AA ist das übliche Ziel. |
| **ARIA** | Zusätzliche HTML-Attribute, die Screenreadern Bedeutung und Zustand von Elementen mitteilen. Grundregel: Wenn ein normales HTML-Element das Gleiche kann, nimm das HTML-Element. |
| **Viewport** | Der sichtbare Bereich der Seite im Browserfenster. |
| **Progressive Enhancement** | Zuerst eine Grundversion, die überall funktioniert, dann schrittweise Verbesserungen für Browser, die mehr können. |
| **Mobile-first** | CSS zuerst für kleine Bildschirme schreiben und für größere erweitern. |
| **Token** | Ein benannter Design-Wert (Farbe, Abstand, Größe), der an einer zentralen Stelle definiert ist. |
