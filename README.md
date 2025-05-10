
# 🎓 DHBW Heidenheim – LaTeX Template (Wirtschaftsinformatik)

Dieses Repository enthält eine LaTeX-Vorlage für wissenschaftliche Arbeiten im Studiengang **Wirtschaftsinformatik** an der **DHBW Heidenheim**. Die Vorlage orientiert sich an den formalen Anforderungen der Hochschule und ist geeignet für Projektarbeiten, Bachelorarbeiten oder Seminararbeiten.

## 📚 Formatierung nach DHBW-Vorgaben

Dieses LaTeX-Template basiert auf den offiziellen Vorgaben der DHBW Heidenheim für den Studiengang Wirtschaftsinformatik.  
Alle wichtigen Formatierungsrichtlinien wie Seitenränder, Schriftgrößen, Gliederungsebenen, Zitierweise und Layout sind berücksichtigt.

📄 **Offizielle Richtlinien (PDF):**  
[Richtlinien zur Erstellung von Projektarbeiten (Stand Juni 2024)](https://www.heidenheim.dhbw.de/fileadmin/Heidenheim/Studienangebot/Bachelor_Wirtschaft/Wirtschaftsinformatik/Informationen_fuer_Studierende/Jg._2023/Richtlinien_zur_Erstellung_von_Projektarbeiten_ab_Jg._2018_Stand_Juni_2024_Wirtschaftsinformatik.pdf)

> Bitte beachte: Die Hochschule kann ihre Anforderungen gelegentlich aktualisieren. Prüfe daher regelmäßig die offizielle Website der DHBW Heidenheim für die aktuellsten Versionen.

## ✨ Features

- Formatierung gemäß den offiziellen **DHBW-Vorgaben**
- Unterstützung für:
  - Deckblatt mit Firmen- und DHBW-Logo
  - Inhaltsverzeichnis
  - Vorwort
  - Abbildungsverzeichnis, Tabellenverzeichnis
  - Sperrvermerk
  - Ehrenwörtliche Erklärung
  - Abkürzungsverzeichnis & Glossar (via `glossaries`)
  - Literaturverzeichnis mit `biblatex` und `biber`
- Kompatibel und getestet mit:
  - [MiKTeX](https://miktex.org/)
- Bei Bedarf lassen sich einzelne Elemente durch Auskommentieren gezielt deaktivieren

## 📋 Voraussetzungen

- Eine LaTeX-Distribution (z. B. [MiKTeX](https://miktex.org/))  
  - MiKTeX lädt und installiert fehlende Pakete bei Bedarf automatisch
- Ein Editor wie [Visual Studio Code](https://code.visualstudio.com/) mit den [empfohlenen Erweiterungen](#-visual-studio-code-setup)
- Grundkenntnisse im Umgang mit LaTeX (z. B. Struktur, Kompilierung, Pakete, Ziterbefehle - besonders `footcites`)
- Optional: Git & GitHub für Versionskontrolle und Sicherung

## 🔧 Konfiguration

Die wichtigsten Einstellungen für Titelblatt, Dokumentart und weitere Metadaten werden zentral in der Datei `config.tex` vorgenommen. 
Neben inhaltlichen Angaben wie Titel, Name, Unternehmen usw. können hier auch grundlegende Formatierungen wie Schriftart, Zeilenabstand, Schriftgröße oder Ränder angepasst werden.

```latex
% Dokumentart auswählen: pa1, pa2, ba
\newcommand{\dokumentart}{pa1}

% Titelblatt-Konfiguration
\newcommand{\projecttitle}{Lorem ipsum dolor sit amet, ...}
\newcommand{\degreeprogram}{Studiengang Wirtschaftsinformatik}
\newcommand{\faculty}{in der Fakultät Wirtschaft}
\newcommand{\university}{an der Duale Hochschule Baden-Württemberg}
\newcommand{\universitycity}{Standort Heidenheim}

\newcommand{\studentname}{Max Mustermann}
\newcommand{\studentaddress}{Musterstraße 1}
\newcommand{\studentcity}{99999 Musterstadt}

\newcommand{\companyname}{Beispiel GmbH}
\newcommand{\companyaddress}{Musterstraße 1}
\newcommand{\companycity}{99999 Musterstadt}

\newcommand{\semester}{2. Semester}
\newcommand{\submissiondate}{01.01.25}
\newcommand{\tutorcompany}{Max Mustermann}
\newcommand{\tutoruniversity}{Erika Müller}

% Relevant für die Bachelorarbeit
\newcommand{\degree}{Bachelor of Science}

% Ehrenwörtliche Erklärung (optional)
\newcommand{\wordcount}{4217}
```

> Hinweis: Die Datei config.tex wird automatisch vom Hauptdokument eingebunden. Änderungen werden beim nächsten Kompilieren übernommen.

### 📚 Literaturverzeichnis (`literatur.bib`)

Alle Quellen werden in der Datei `literatur.bib` gepflegt und automatisch mit `biblatex` + `biber` eingebunden.  
Jede Quelle benötigt einen eindeutigen `@Key`, der in den Zitierbefehlen verwendet wird.

> Tipp: Verwende ein Literaturverwaltungsprogramm wie [Zotero](https://www.zotero.org/), um deine Quellen bequem zu verwalten und als `.bib`-Datei zu exportieren.

## ⚙️ Visual Studio Code Setup

### 📦 Erweiterungsempfehlung (`.vscode/extensions.json`)

```json
{
  "recommendations": [
    "james-yu.latex-workshop",
    "tecosaur.latex-utilities",
    "ltex-plus.vscode-ltex-plus"
  ]
}
```

### 🧩 Build-Rezept und LaTeX-Konfiguration (`.vscode/settings.json`)

```json
{
  "ltex.language": "de",
  "latex-workshop.latex.outDir": "./OUTPUT",
  "latex-workshop.view.pdf.viewer": "tab",
  "latex-workshop.synctex.afterBuild.enabled": true,
  "latex-workshop.latex.recipe.default": "xelatex -> biber -> makeglossaries -> xelatex",
  "latex-workshop.latex.recipes": [
    {
      "name": "xelatex -> biber -> makeglossaries -> xelatex",
      "tools": [
        "xelatex",
        "biber",
        "makeglossaries",
        "xelatex",
        "xelatex"
      ]
    }
  ],
  "latex-workshop.latex.tools": [
    {
      "name": "xelatex",
      "command": "xelatex",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "-output-directory=./OUTPUT",
        "%DOC%"
      ]
    },
    {
      "name": "biber",
      "command": "biber",
      "args": [
        "--input-directory=./OUTPUT",
        "%DOCFILE%"
      ]
    },
    {
      "name": "makeglossaries",
      "command": "makeglossaries",
      "args": [
        "-d",
        "./OUTPUT",
        "%DOCFILE%"
      ]
    }
  ]
}
```

### 🧭 Quelltext–PDF-Synchronisation (SyncTeX)

- **Strg + Linksklick** im PDF → springt zur entsprechenden Zeile im `.tex`-Code  
- **Ctrl + Alt + J** im Code → öffnet die passende Stelle im PDF

### 💡 Versionskontrolle & Sicherung

- Git und GitHub ermöglichen Nachverfolgung, Sicherung und Zusammenarbeit
- Remote-Repositories schützen vor Datenverlust
- Ideal für Teamarbeit und Studienprojekte
