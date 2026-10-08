# Installation und Teamarbeit

## Windows: MiKTeX
1. MiKTeX von https://miktex.org/download installieren (für den eigenen Benutzer reicht üblicherweise).
2. MiKTeX Console öffnen und Updates installieren. Unter Packages nach `biber` und `biblatex` suchen und installieren, wenn sie fehlen. Fehlende weitere Pakete bei der ersten Kompilierung installieren lassen; Schulnetz/Internet muss dies ermöglichen.
3. VS Code installieren und LaTeX Workshop hinzufügen. VS Code nach der TeX-Installation vollständig neu starten.
4. In einem neuen VS-Code-Terminal prüfen:
```powershell
lualatex --version
biber --version
git --version
```
Wenn ein Befehl fehlt: Installation/PATH prüfen und Terminal neu öffnen. Biber und biblatex gemeinsam aktualisieren, falls die Versionen nicht kompatibel sind.

## Mac: MacTeX
1. Vollständiges MacTeX von https://www.tug.org/mactex/ installieren.
2. VS Code und LaTeX Workshop installieren; VS Code neu starten.
3. Die gleichen Versionsbefehle wie oben ausführen. Wenn TeX nicht gefunden wird, `/Library/TeX/texbin` im PATH prüfen.

## Kompilieren ohne VS-Code-Erweiterung
Terminal im Projektordner öffnen. Jeden Befehl einzeln ausführen; bei einem Fehler zuerst stoppen und diesen beheben:
```text
lualatex -interaction=nonstopmode -halt-on-error main.tex
biber main
lualatex -interaction=nonstopmode -halt-on-error main.tex
lualatex -interaction=nonstopmode -halt-on-error main.tex
```
`main.pdf` liegt danach im Projektordner. Biber wird mit `main` ohne Dateiendung aufgerufen. Es ist ein Programm; biblatex ist das LaTeX-Paket. Beide verwenden eure `.bib`-Datei.
Die direkte VS-Code-Rezeptfolge benötigt kein Perl. Wer später `latexmk` verwendet, braucht unter Windows mit MiKTeX zusätzlich eine Perl-Installation.

## Einmalig GitHub einrichten (eine Person)
Privates, leeres Repository auf GitHub erstellen, ohne automatisch angelegtes README. Im entpackten Projektordner:
```text
git init -b main
git add .
git commit -m "Add diploma thesis template"
git remote add origin https://github.com/DEIN-ACCOUNT/DEIN-REPOSITORY.git
git push -u origin main
```
URL ersetzen. Teammitglieder in den Repository-Einstellungen einladen. Die anderen klonen anschließend das Repository, statt eigene ZIP-Kopien weiterzuführen:
```text
git clone https://github.com/DEIN-ACCOUNT/DEIN-REPOSITORY.git
```
Falls Git nach Name/E-Mail fragt, die eigene Identität konfigurieren. Keine gemeinsamen Konten verwenden.

## Täglicher Workflow
Arbeit aufteilen: jede Person eigene Kapiteldateien; Änderungen an main.tex und Literaturdatei kurz abstimmen.
```text
git switch main
git pull --ff-only
git switch -c kapitel/anforderungen
```
Schreiben, kompilieren und PDF kontrollieren. Dann:
```text
git status
git add kapitel/03-anforderungen.tex
git commit -m "Describe requirements and acceptance criteria"
git push -u origin kapitel/anforderungen
```
Auf GitHub Pull Request öffnen. Eine andere Person prüft Verständlichkeit, Quellen und Inhalt. Die automatische Prüfung überprüft nur die Kompilierung und unaufgelöste Zitate/Verweise, nicht die fachliche Richtigkeit. Nach erfolgreicher Prüfung und Rückmeldung zusammenführen. `main` in GitHub nach Möglichkeit schützen und den Check `build` verpflichtend machen (Verfügbarkeit hängt vom GitHub-Tarif ab).

## Automatische Prüfung
Unter **Actions** läuft nach Push/PR der Workflow **LaTeX build**. Beim ersten Lauf werden TeX und Biber installiert. Nach einem erfolgreichen Lauf steht **Diplomarbeit-PDF** als Download unter Artifacts bereit. Bei Fehlern den Schritt Compile document öffnen und nach der ersten Fehlermeldung suchen. GitHub Actions muss im Repository aktiviert sein.

## Konflikte
Bei einem Konflikt beide Textversionen lesen und gemeinsam sinnvoll zusammenführen. Konfliktmarkierungen entfernen, kompilieren, Änderungen committen. Nicht blind eine Seite übernehmen. Kurze Zeilen und kleine Commits helfen beim Vergleichen. PDFs und automatisch erzeugte Hilfsdateien werden nicht versioniert.

## Häufige Fehler
- `Undefined control sequence`: Tippfehler im Befehl oder fehlendes Paket.
- `File ... not found`: Dateiname/Pfad prüfen; GitHub unter Linux unterscheidet Groß-/Kleinschreibung.
- Quellenverweis bleibt als Schlüssel sichtbar: Schlüssel in literatur.bib prüfen und vollständige Build-Folge starten.
- `biber` nicht gefunden: Paket installieren, PATH prüfen, VS Code neu starten.
- fehlender Font: Die Vorlage verwendet Latin Modern aus der TeX-Distribution, keine Windows-exklusive Schrift.
- unerwartete LaTeX-Zeichen: `%`, `&`, `_`, `#` im normalen Text als `\%`, `\&`, `\_`, `\#` schreiben.

## Offizielle Dokumentation
- https://miktex.org/howto/install-miktex
- https://www.tug.org/mactex/
- https://github.com/James-Yu/LaTeX-Workshop/wiki/Install
- https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile
- https://ctan.org/pkg/biblatex
- https://ctan.org/pkg/biber
