# Projekt-Tagebuch – Portfolio

Hier halte ich Entscheidungen, Probleme und Lösungen fest, jeweils mit Datum. Daraus entstehen später die Abschnitte „Approach“, „Development log“ und „Challenges & Learnings“ auf der Projektseite (`public/projects/portfolio.html`).

Die neuesten Einträge stehen oben.

**Vorlage für einen Eintrag:**

```
## JJJJ-MM-TT – Thema

**Was:** Was habe ich gemacht oder entschieden?
**Problem:** Was hat nicht funktioniert? (falls zutreffend)
**Lösung:** Wie habe ich es gelöst, und welche Alternativen habe ich verworfen?
**Gelernt:** Was nehme ich mit?
```

---

## 2026-10-20 – Zeilenenden zum zweiten Mal falsch

**Was:** Ich habe WebStorm neu installiert, weil die Code-Vervollständigung nicht mehr funktioniert hat.
**Problem:** Danach hat WebStorm `index.html` wieder mit Windows-Zeilenenden (CRLF) gespeichert. Die Einstellung „Unix (LF)“ vom 12.10. war weg, weil das Projekt nach der Neuinstallation das globale Standard-Schema benutzt hat.
**Lösung:** Die Regel steht jetzt in zwei Dateien im Repository: `.editorconfig` sagt dem Editor, dass er LF speichern soll, und `.gitattributes` sorgt dafür, dass Git nur LF speichert. Die Datei selbst musste ich einmal von Hand auf LF umstellen, denn die Einstellung gilt nicht rückwirkend.
**Gelernt:** Eine Einstellung in der IDE geht bei einer Neuinstallation verloren, eine Datei im Repository nicht. Sie gilt außerdem automatisch auf beiden PCs. Bei Problemen mit WebStorm versuche ich zuerst „Invalidate Caches“ statt einer Neuinstallation.

## 2026-10-20 – Der `<head>` der Startseite

**Was:** Ich habe den Kopfbereich von `index.html` geschrieben: Doctype, Sprache, Zeichenkodierung, Viewport, Titel, Meta-Description und die CSS-Dateien.
**Problem:** Beim ersten Versuch fehlte im Doctype das `!`. Außerdem hatte ich persönliche Notizen als HTML-Kommentare in den Code geschrieben (z. B. „Titel nach der Ausbildung ändern“).
**Lösung:** Den Doctype korrigiert. Die Notizen stehen jetzt in `AUFGABEN.md` im Abschnitt „Später anpassen“.
**Gelernt:** HTML-Kommentare sind nicht privat. Jeder Besucher kann sie mit Strg + U im Quelltext lesen.

**Entscheidungen dazu:**
- **Titel:** „Florian Heine – Apprentice Software Developer“. Auf der Startseite ist mein Name der Seitenname. Auf den anderen Seiten steht der Seitenname vorne, damit Screenreader-Nutzer die Seiten sofort unterscheiden können. Ich verwende den Halbgeviertstrich (–), weil er typografisch richtig ist.
- **Rolle:** „Apprentice Software Developer“ statt „Web Developer“, weil ich nicht nur Websites baue, sondern zum Beispiel auch eine Bücherverwaltung in Python.
- **Description:** Barrierefreiheit steht als mein Schwerpunkt drin, weil sie mich von anderen Portfolios unterscheidet. Demos erwähne ich erst, wenn es welche gibt.

## 2026-10-20 – Eine Projektvorlage für alle Projektarten

**Was:** Ich habe die Vorlage für Projektseiten geplant.
**Problem:** Die erste Planung ging davon aus, dass jedes Projekt eine interaktive Demo im Browser hat. Das passt zu Websites, aber nicht zu einem Python-Programm.
**Lösung:** Die Vorlage hat jetzt einen Status („In progress“ / „Completed“), ein Development log für laufende Projekte und eine optionale Demo. Die Form der Demo wähle ich pro Projekt: Bild-Rundgang, Video, Terminal-Protokoll, Code-Rundgang, interaktive Nachbildung oder Live-Version. Animierte GIFs verwende ich nicht. Videos hoste ich selbst und nicht bei YouTube, aus demselben Datenschutzgrund wie bei den Schriften. Jede Demo hat eine Textalternative.
**Gelernt:** Eine Vorlage muss auch zu Projekten passen, die es noch nicht gibt.

## 2026-10-12 – Lokaler Server statt nginx

**Was:** Ich habe die lokale Entwicklungsumgebung eingerichtet (Aufgabe 1.0).
**Problem:** Auf meinem Rechner läuft bereits nginx mit dem Wurzelverzeichnis `/srv/http`. Darüber wäre die Seite unter `/Portfolio/public/` erreichbar. Damit funktionieren wurzel-relative Pfade wie `/assets/css/base.css` nicht. Dasselbe Problem hat die Vorschau von WebStorm.
**Lösung:** Ich starte für die Entwicklung den Python-Server mit `public/` als Wurzel (`python -m http.server 8000 --directory public`). nginx bleibt unverändert. Ich habe es nicht umkonfiguriert, weil es Netlifys `_redirects` sowieso nicht versteht und ich die anderen Projekte unter `/srv/http` nicht gefährden wollte.
**Gelernt:** Eine Seite muss lokal von derselben Wurzel aus laufen wie online, sonst testet man etwas anderes als das, was veröffentlicht wird.

## 2026-10-12 – Zeilenenden: CRLF und LF

**Was:** Ich habe WebStorm auf LF als Zeilenende eingestellt.
**Problem:** Ich arbeite mit WebStorm unter Windows an Dateien in WSL (Linux). Windows speichert Zeilenenden als CRLF, Linux als LF. `.gitignore` hatte CRLF.
**Lösung:** In WebStorm den Zeilentrenner „Unix (LF)“ eingestellt und `.gitignore` umgewandelt.
**Gelernt:** Unterschiedliche Zeilenenden sind unsichtbar, aber Git zeigt dann jede Zeile als geändert an. (Fortsetzung am 20.10.)

## 2026-10-09 – Planung und Projektstruktur

**Was:** Ich habe das Projekt geplant (`DATEISTRUKTUR.md`, `AUFGABEN.md`), Git und GitHub eingerichtet und die Ordnerstruktur angelegt.

**Entscheidungen:**
- **Kein Framework, kein Build-Schritt, nur HTML, CSS und JavaScript.** Ich will die Grundlagen lernen, bevor ich Werkzeuge benutze, die sie verstecken.
- **Zwei Sprachen als getrennte HTML-Dateien statt einer Umschaltung mit JavaScript.** So stimmt das `lang`-Attribut für Screenreader, jede Sprache hat eine eigene URL, und die Übersetzung funktioniert auch ohne JavaScript. Der Nachteil: Jede Textänderung muss ich zweimal machen.
- **Wurzel-relative Pfade (`/assets/...`).** Sie funktionieren in jeder Ordnertiefe, auch in `de/` und auf der 404-Seite.
- **Ordner `public/`.** Netlify veröffentlicht nur diesen Ordner. Planungsdateien und Dokumentation bleiben im Repository, landen aber nicht online.
- **Kein PHP.** Netlify Forms nimmt das Kontaktformular entgegen. Gegen Spam schützt ein verstecktes Lockfeld (Honeypot) statt eines CAPTCHAs, weil CAPTCHAs eine große Barriere sind.
- **Farben mit AAA-Kontrast.** Meine ersten Farben für gedämpften Text und Links erreichten im hellen Modus nur etwa 6 : 1. Ich habe sie auf über 7 : 1 angepasst und für den dunklen Modus eine eigene Hover-Farbe ergänzt.
- **Schriften lokal gehostet** statt über Google Fonts (Datenschutz, LG München 2022).

**Probleme:**
- Ich hatte die Platzhalter-Dateien als root angelegt und konnte sie danach nicht bearbeiten. Lösung: Besitzer rekursiv mit `chown` auf meinen Benutzer geändert.
- Die Adresse des GitHub-Remotes war doppelt eingetragen. Lösung: mit `git remote set-url` korrigiert.

**Gelernt:** Vor dem ersten Code zu planen kostet Zeit, aber viele Entscheidungen (Sprachen, Pfade, Hosting) wären später nur mit viel Aufwand zu ändern gewesen.
