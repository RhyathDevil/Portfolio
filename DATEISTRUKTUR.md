# Dateistruktur – Portfolio

Statische Website mit HTML, CSS und JavaScript, ohne Framework und ohne Build-Schritt.
Die Hauptsprache ist **Englisch** (im Wurzelverzeichnis), **Deutsch** liegt als Spiegelung unter `/de/`.

```
Portfolio/
│
├── index.html                    # Startseite (EN)
├── about.html                    # Über mich (EN)
├── contact.html                  # Kontakt (EN)
├── accessibility.html            # Erklärung zur Barrierefreiheit (EN)
├── imprint.html                  # Impressum / Legal Notice (EN)
├── privacy.html                  # Datenschutzerklärung / Privacy Policy (EN)
├── 404.html                      # Fehlerseite „Seite nicht gefunden“ (EN)
│
├── projects/
│   ├── index.html                # Projektübersicht (EN)
│   ├── _template.html            # Vorlage für neue Projektseiten (wird nicht verlinkt)
│   └── project-name.html         # Eine Datei pro Projekt (EN)
│
├── de/                           # Deutsche Version, gleiche Struktur, gleiche Dateinamen
│   ├── index.html
│   ├── about.html
│   ├── contact.html
│   ├── accessibility.html
│   ├── imprint.html
│   ├── privacy.html
│   ├── 404.html
│   └── projects/
│       ├── index.html
│       └── project-name.html
│
├── assets/
│   ├── css/
│   │   ├── reset.css             # Einheitliche Grundlage über alle Browser
│   │   ├── tokens.css            # Design-Variablen: Farben, Abstände, Schriftgrößen
│   │   ├── base.css              # Typografie, Links, Fokus-Stile, Grundelemente
│   │   ├── layout.css            # Header, Footer, Raster, Container
│   │   ├── components.css        # Buttons, Karten, Navigation, Tags, Formulare
│   │   ├── pages.css             # Seitenspezifische Stile (falls nötig)
│   │   ├── demos.css             # Stile für interaktive Projekt-Demos
│   │   └── print.css             # Druckansicht
│   │
│   ├── js/
│   │   ├── main.js               # Einstiegspunkt, lädt die Module
│   │   ├── navigation.js         # Mobile Navigation (Menü öffnen/schließen)
│   │   ├── theme.js              # Hell/Dunkel-Umschalter
│   │   ├── project-filter.js     # Filter der Projektübersicht nach Technologie
│   │   └── demos/                # Ein Skript pro interaktiver Projekt-Demo
│   │       └── project-name.js
│   │
│   ├── img/
│   │   ├── profile/              # Profilfoto
│   │   ├── projects/             # Screenshots und Vorschaubilder pro Projekt
│   │   │   └── project-name/
│   │   └── icons/                # SVG-Icons (GitHub, LinkedIn, Mail, Theme, Menü …)
│   │
│   ├── fonts/                    # Lokal gehostete Schriften (KEIN Google-Fonts-CDN)
│   │
│   └── docs/
│       ├── cv-en.pdf             # Lebenslauf EN (barrierefreies PDF)
│       └── cv-de.pdf             # Lebenslauf DE (barrierefreies PDF)
│
├── favicon.ico
├── favicon.svg
├── apple-touch-icon.png
├── site.webmanifest              # Name, Icons, Farben der Seite
├── robots.txt                    # Hinweise für Suchmaschinen
├── sitemap.xml                   # Liste aller Seiten inkl. Sprachversionen
│
├── docs/
│   └── sessions/                 # Sitzungsprotokolle (nicht Teil der Website)
│
├── README.md
├── DATEISTRUKTUR.md              # Diese Datei
└── AUFGABEN.md                   # Aufgabenliste
```

## Begründung der Entscheidungen

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

**Kein Kontaktformular in der ersten Version.**
Ein Formular braucht ein Backend (PHP, Node oder einen externen Dienst), um E-Mails zu verschicken. Das liegt außerhalb von HTML, CSS und JS. Für den Anfang genügt die Kontaktseite mit E-Mail-Link und Profil-Links.
