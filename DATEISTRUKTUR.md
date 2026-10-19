# Dateistruktur – Portfolio

Statische Website mit HTML, CSS und JavaScript, ohne Framework und ohne Build-Schritt.
Die Hauptsprache ist **Englisch** (direkt in `public/`), **Deutsch** liegt als Spiegelung unter `public/de/`.

Alle Pfade in den Aufgaben (z. B. `projects/index.html`) beziehen sich auf den Ordner `public/`. Für die Website ist `public/` das Wurzelverzeichnis: `public/assets/css/base.css` ist online unter `/assets/css/base.css` erreichbar.

```
Portfolio/
│
├── public/                       # ALLES, was online geht (Netlify veröffentlicht nur diesen Ordner)
│   │
│   ├── index.html                # Startseite (EN)
│   ├── about.html                # Über mich (EN)
│   ├── contact.html              # Kontakt mit Formular (EN)
│   ├── contact-thanks.html       # Bestätigung nach dem Absenden des Formulars (EN)
│   ├── accessibility.html        # Erklärung zur Barrierefreiheit (EN)
│   ├── imprint.html              # Impressum / Legal Notice (EN)
│   ├── privacy.html              # Datenschutzerklärung / Privacy Policy (EN)
│   ├── 404.html                  # Fehlerseite „Seite nicht gefunden“ (EN)
│   │
│   ├── projects/
│   │   ├── index.html            # Projektübersicht (EN)
│   │   ├── _template.html        # Vorlage für neue Projektseiten (wird nicht verlinkt)
│   │   └── portfolio.html        # Erstes Projekt: dieses Portfolio (EN)
│   │
│   ├── de/                       # Deutsche Version, gleiche Struktur, gleiche Dateinamen
│   │   ├── index.html
│   │   ├── about.html
│   │   ├── contact.html
│   │   ├── contact-thanks.html
│   │   ├── accessibility.html
│   │   ├── imprint.html
│   │   ├── privacy.html
│   │   ├── 404.html
│   │   └── projects/
│   │       ├── index.html
│   │       └── portfolio.html
│   │
│   ├── assets/
│   │   ├── css/
│   │   │   ├── reset.css         # Einheitliche Grundlage über alle Browser
│   │   │   ├── tokens.css        # Design-Variablen: Farben, Abstände, Schriftgrößen
│   │   │   ├── base.css          # Typografie, Links, Fokus-Stile, Grundelemente
│   │   │   ├── layout.css        # Header, Footer, Raster, Container
│   │   │   ├── components.css    # Buttons, Karten, Navigation, Tags, Formulare
│   │   │   ├── pages.css         # Seitenspezifische Stile (falls nötig)
│   │   │   ├── demos.css         # Stile für interaktive Projekt-Demos
│   │   │   └── print.css         # Druckansicht
│   │   │
│   │   ├── js/
│   │   │   ├── main.js           # Einstiegspunkt, lädt die Module
│   │   │   ├── navigation.js     # Mobile Navigation (Menü öffnen/schließen)
│   │   │   ├── theme.js          # Hell/Dunkel-Umschalter
│   │   │   ├── project-filter.js # Filter der Projektübersicht nach Technologie
│   │   │   ├── contact-form.js   # Prüfung und Fehlermeldungen im Kontaktformular
│   │   │   └── demos/            # Ein Skript pro interaktiver Projekt-Demo
│   │   │       └── portfolio.js  # Demo des ersten Projekts
│   │   │
│   │   ├── img/
│   │   │   ├── profile/          # Profilfoto
│   │   │   ├── projects/         # Screenshots und Vorschaubilder pro Projekt
│   │   │   │   └── portfolio/
│   │   │   └── icons/            # SVG-Icons (GitHub, LinkedIn, Mail, Theme, Menü …)
│   │   │
│   │   ├── fonts/                # Lokal gehostete Schriften (KEIN Google-Fonts-CDN)
│   │   │
│   │   └── docs/
│   │       ├── cv-en.pdf         # Lebenslauf EN (barrierefreies PDF)
│   │       └── cv-de.pdf         # Lebenslauf DE (barrierefreies PDF)
│   │
│   ├── favicon.ico
│   ├── favicon.svg
│   ├── apple-touch-icon.png
│   ├── site.webmanifest          # Name, Icons, Farben der Seite
│   ├── robots.txt                # Hinweise für Suchmaschinen
│   ├── sitemap.xml               # Liste aller Seiten inkl. Sprachversionen
│   └── _redirects                # Netlify: Weiterleitungen und deutsche 404-Seite
│
├── docs/
│   ├── projekt-tagebuch.md       # Entscheidungen und Probleme, Grundlage für die Projektseite
│   └── sessions/                 # Sitzungsprotokolle
│
├── netlify.toml                  # Netlify-Einstellungen (veröffentlicht nur public/)
├── .gitignore
├── CLAUDE.md                     # Regeln für Claude Code in diesem Projekt (Lernmodus)
├── README.md
├── DATEISTRUKTUR.md              # Diese Datei
└── AUFGABEN.md                   # Aufgabenliste
```

## Begründung der Entscheidungen

**Website in `public/`, Planung außerhalb.**
Netlify veröffentlicht nur den Ordner `public/` (festgelegt in `netlify.toml`). Planungsdateien, Dokumentation und Projekteinstellungen liegen im Repository, aber nicht auf der Website. So landet nichts versehentlich online, das nicht dorthin gehört.

**Zwei Sprachen als getrennte HTML-Dateien statt Umschaltung per JavaScript.**
Ein reiner JS-Umschalter tauscht nur Texte aus. Screenreader lesen die Seite dann eventuell mit falscher Aussprache vor, weil das `lang`-Attribut nicht stimmt. Suchmaschinen sehen nur eine Sprache, und ohne JavaScript gibt es gar keine Übersetzung. Mit getrennten Dateien hat jede Sprache eine eigene URL und ein korrektes `lang`. Der Sprachumschalter ist dann ein normaler Link auf dieselbe Seite in der anderen Sprache.
Der Preis dafür: Jede Textänderung musst du in zwei Dateien machen. Das ist der Grund, warum `de/` exakt dieselben Dateinamen wie die englische Version verwendet.

**Pflichtseiten `imprint`, `privacy`, `accessibility`.**
Wenn du die Seite in Deutschland betreibst, sind Impressum und Datenschutzerklärung in der Praxis Pflicht, weil jeder Server Zugriffsdaten wie IP-Adressen protokolliert. Die Seite zur Barrierefreiheit ist bei privaten Seiten freiwillig. Für dein Ziel ist sie aber ein starkes Signal an Arbeitgeber, weil sie zeigt, dass du das Thema bewusst umgesetzt hast.

**Schriften lokal in `assets/fonts/`.**
Das Einbinden von Google Fonts über deren Server ist in Deutschland datenschutzrechtlich problematisch (LG München, 2022). Lokal gehostete Schriften vermeiden das.

**CSS in mehrere Dateien aufgeteilt.**
Diese Aufteilung dient der Übersicht beim Lernen. Später kannst du die Dateien zu einer zusammenführen, falls dir das lieber ist.

**`projects/_template.html`.**
Jede Projektseite hat denselben Aufbau. Mit der Vorlage kopierst du für ein neues Projekt nur die Datei und füllst die Inhalte.

**Kontaktformular über Netlify Forms, ohne eigenes Backend.**
Ein Formular braucht normalerweise ein Backend (z. B. PHP), um Nachrichten zu verschicken. Netlify nimmt Formulareingaben aber selbst entgegen, wenn das Formular entsprechend markiert ist. Damit bleibt das Projekt bei reinem HTML, CSS und JS. Im kostenlosen Tarif sind 100 Einsendungen pro Monat enthalten. `contact-thanks.html` ist die Seite, auf die man nach dem Absenden geleitet wird.

**Hosting auf Netlify, Domain bei Porkbun.**
Netlify ist mit dem GitHub-Repository verbunden und veröffentlicht automatisch jeden Push auf `main`. Die Domain von Porkbun zeigt per DNS auf Netlify, und HTTPS richtet Netlify selbst ein. PHP wird nicht benötigt: Alles Interaktive läuft als JavaScript im Browser. Falls später doch Logik auf dem Server nötig ist, bietet Netlify „Functions“ an, und die schreibt man ebenfalls in JavaScript.

**`_redirects`.**
Netlify liefert bei unbekannten Adressen automatisch `/404.html` aus. Damit Besucher unter `/de/…` die deutsche Fehlerseite sehen, braucht es eine Regel in dieser Datei.

**Erstes Projekt: das Portfolio selbst.**
`projects/portfolio.html` erzählt, wie diese Website entstanden ist: Entscheidungen, Barrierefreiheit, Probleme und Lösungen. `projects/_template.html` bleibt die leere Vorlage für alle weiteren Projekte.
