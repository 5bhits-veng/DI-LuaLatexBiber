# LaTeX in 60 Minuten kennenlernen

LaTeX ist ein System zum Setzen von Dokumenten. Ihr schreibt Inhalt und Struktur in Textdateien; LuaLaTeX erzeugt daraus ein PDF. Kapitel, Nummerierungen, Verweise und Literaturverzeichnis werden automatisch gesetzt.

## 0–15 Minuten: Projekt starten
Metadaten ändern, PDF erzeugen und ansehen. In einem eigenen Kapitel einen Absatz ändern und neu kompilieren.

## 15–30 Minuten: Struktur und Text
```latex
\section{Zielsetzung}
Das ist ein Absatz mit \textbf{fett} und \emph{hervorgehoben}.

Eine Leerzeile beginnt einen neuen Absatz.
\begin{itemize}
  \item Erste Anforderung
  \item Zweite Anforderung
\end{itemize}
```

## 30–45 Minuten: Quellen und Verweise
In `literatur.bib` eigene, überprüfte Quellen erfassen (z. B. BibTeX-Export aus Zotero). Jede Quelle braucht einen eindeutigen Schlüssel.
```latex
Eine belegte Aussage steht hier \autocite{latexproject}.
Wie in Kapitel~\ref{chap:grundlagen} beschrieben, ...
```
Die Beispieldatei zeigt die Syntax. Für eigene Aussagen passende Fachquellen verwenden. Quellen nicht erfinden; Metadaten und Seitenangaben prüfen. Mit `\autocite[23]{schluessel}` eine Seite angeben.

## 45–60 Minuten: Bild einsetzen und committen
Bild als `bilder/aufbau.png` speichern:
```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.8\textwidth]{bilder/aufbau.png}
  \caption{Aufbau des Prototyps (eigene Aufnahme)}
  \label{fig:aufbau}
\end{figure}
Abbildung~\ref{fig:aufbau} zeigt den Aufbau.
```
`htbp` erlaubt LaTeX, einen passenden Platz zu wählen. Fremde Bilder benötigen einen Quellenbeleg in der Bildunterschrift.
Anschließend kompilieren, PDF lesen und nur die geänderten Quelldateien committen.

Für den Anfang reichen Kapitel, Absätze, Listen, Bilder, Tabellen, Quellen und Verweise. Inhalt zuerst schreiben; Layoutänderungen zentral und gemeinsam abstimmen.
