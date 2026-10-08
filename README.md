# Diplomarbeit mit LuaLaTeX und Biber

## Start in 5 Schritten
1. ZIP vollständig entpacken. Den Ordner `Diplomarbeit_LuaLaTeX` in VS Code über **Datei → Ordner öffnen** öffnen.
2. TeX installieren: Windows → MiKTeX; macOS → vollständiges MacTeX. Details in `ANLEITUNG.md`.
3. VS-Code-Erweiterung **LaTeX Workshop (James Yu)** installieren.
4. Angaben in `metadaten.tex` ändern, `main.tex` öffnen und speichern.
5. Befehlspalette öffnen (Windows Strg+Umschalt+P; Mac Cmd+Umschalt+P), **LaTeX Workshop: Build with recipe** auswählen, dann **LuaLaTeX + Biber**. PDF über **LaTeX Workshop: View LaTeX PDF file** anzeigen.

Die Konfiguration startet den Build bewusst manuell: So wird nicht bei jedem Speichern während des Tippens eine vollständige Biber-Kette gestartet.

## Dateien
- `main.tex`: setzt die Arbeit zusammen; Paket- und Zitierkonfiguration.
- `metadaten.tex`: Titel, Namen und Abgabetermin.
- `kapitel/`: Inhalte; getrennte Dateien für drei Teammitglieder.
- `literatur.bib`: gemeinsame Literaturdaten im BibTeX-Format, verarbeitet durch Biber.
- `bilder/`: Grafiken.
- `.vscode/`: gemeinsame VS-Code-Konfiguration.
- `.github/workflows/latex.yml`: automatische PDF-Kompilierung bei Push und Pull Request.
- `ANLEITUNG.md`: Installation, Git, Fehlersuche.
- `LATEX_SCHNELLSTART.md`: erste Schreibübungen.

Dies ist eine allgemeine Arbeitsvorlage, keine offiziell freigegebene Schulvorlage. Deckblatt, Zitierstil, Eigenständigkeitserklärung und weitere formale Vorgaben mit der Schule abgleichen. Voreingestellt sind nummerierte Zitate mit `style=numeric`; für IEEE nach Vorgabe auf `style=ieee` umstellen und das Paket biblatex-ieee installieren.
