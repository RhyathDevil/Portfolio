# CLAUDE.md – Portfolio

Persönliche Portfolio-Website, die zukünftige Projekte vorstellt und interaktiv erklärt. Sie ist meine erste vollständige Website und dient später für Bewerbungen. Hauptsprache der Website ist Englisch, Deutsch ist optional umschaltbar.

## Lernmodus – wichtigste Regel

Ich lerne HTML, CSS und JavaScript mit diesem Projekt. Deshalb gilt:

- **Keinen fertigen Code für die Website schreiben** (alles in `public/`), außer ich frage ausdrücklich danach, z. B. „Zeig mir den Code“ oder „Schreib mir das“.
- **Dateien in `public/` nicht selbst bearbeiten**, außer ich bitte ausdrücklich darum.
- Erlaubt und erwünscht sind:
  - Konzepte erklären
  - Begriffe zum Nachschlagen nennen (am besten MDN)
  - Rückfragen stellen, die mich zur Lösung führen
- Wenn ich Code zur Prüfung zeige: Fehler und Schwachstellen benennen und erklären, **warum** sie ein Problem sind. Nicht die korrigierte Fassung liefern.
- Wenn ich doch Code bekomme: jeden Teil erklären.
- Planungsdateien (`AUFGABEN.md`, `DATEISTRUKTUR.md`, `README.md`), Dokumentation in `docs/` und Konfiguration (`netlify.toml`, `.gitignore`) darfst du bearbeiten. `AUFGABEN.md` enthält keinen Code, nur Ziele, Begründungen, Prüfpunkte und Begriffe zum Nachschlagen.

## Sprache

- Antworten auf Deutsch.
- Website-Inhalte auf Englisch, die deutsche Version liegt unter `public/de/`.

## Wo der aktuelle Stand steht

Zu Beginn einer Sitzung lesen:
1. das neueste Protokoll in `docs/sessions/`
2. `AUFGABEN.md`: Plan und Fortschritt (abgehakte Punkte)
3. `DATEISTRUKTUR.md`: Verzeichnisbaum und Begründung jeder Strukturentscheidung
4. `docs/projekt-tagebuch.md` (falls vorhanden): Entscheidungen und Probleme, Grundlage für die Projektseite `public/projects/portfolio.html`

## Feste Entscheidungen

Diese Entscheidungen nicht ohne neuen Grund infrage stellen. Die Begründungen stehen in `DATEISTRUKTUR.md`.

- **Technik:** HTML, CSS, Vanilla-JavaScript. Kein Framework, kein Build-Schritt, kein PHP.
- **Hosting:** Netlify veröffentlicht nur `public/` (siehe `netlify.toml`). Die Domain liegt bei Porkbun. Das Kontaktformular läuft über Netlify Forms.
- **Pfade:** wurzel-relativ (`/assets/...`), nie relativ (`../`).
- **Zwei Sprachen:** getrennte HTML-Dateien. `public/de/` hat exakt dieselben Dateinamen wie die englische Version.
- **Barrierefreiheit:** Ziel ist WCAG 2.2 AA. Die Farbkontraste erreichen AAA. Progressive Enhancement: Alles funktioniert ohne JavaScript.
- **Schriften:** lokal gehostet, keine externen CDNs (Datenschutz).
- **Erstes Projekt auf der Website:** das Portfolio selbst.

## Umgebung

- WSL2 (Arch Linux), WebStorm unter Windows. Zeilenenden sind LF.
- Lokaler Server: `python -m http.server 8000 --directory public`, dann `http://localhost:8000` öffnen.
  - Nicht über nginx (`localhost`, Root `/srv/http`) und nicht über die Vorschau von WebStorm öffnen. Beide liefern die Seite aus einem Unterordner aus, und dann funktionieren die wurzel-relativen Pfade nicht.
  - nginx nicht umkonfigurieren.
- Befehle, die ich mit `!` ausführe, haben kein interaktives Terminal. `sudo` funktioniert dort nicht.

## Git

- Repository: `github.com/RhyathDevil/Portfolio`, Branch `main`.
- Ich arbeite an zwei PCs: zu Beginn einer Sitzung `git pull`, vor dem Wechsel `git push`.
- Nur committen, wenn ich darum bitte.
