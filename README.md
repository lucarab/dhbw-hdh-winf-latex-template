# DHBW Heidenheim – LaTeX Thesis Template (Wirtschaftsinformatik)

Dieses Repository enthält eine LaTeX-Vorlage für wissenschaftliche Arbeiten im Studiengang **Wirtschaftsinformatik** an der **DHBW Heidenheim**.  
Die Vorlage orientiert sich an den formalen Anforderungen der Hochschule und ist geeignet für Projektarbeiten, Bachelorarbeiten oder Seminararbeiten.



## 📚 Formatierung nach DHBW-Vorgaben

Dieses LaTeX-Template basiert auf den offiziellen Vorgaben der DHBW Heidenheim für den Studiengang Wirtschaftsinformatik.  
Alle wichtigen Formatierungsrichtlinien wie Seitenränder, Schriftgrößen, Gliederungsebenen, Zitierweise und Layout sind berücksichtigt.

📄 **Offizielle Richtlinien (PDF):**  
[Richtlinien zur Erstellung von Projektarbeiten (Stand Juni 2024)](https://www.heidenheim.dhbw.de/fileadmin/Heidenheim/Studienangebot/Bachelor_Wirtschaft/Wirtschaftsinformatik/Informationen_fuer_Studierende/Jg._2023/Richtlinien_zur_Erstellung_von_Projektarbeiten_ab_Jg._2018_Stand_Juni_2024_Wirtschaftsinformatik.pdf)

> Bitte beachte: Die Hochschule kann ihre Anforderungen gelegentlich aktualisieren. Prüfe daher regelmäßig die offizielle Website der DHBW Heidenheim für die aktuellsten Versionen.



## Features

- Formatierung nach DHBW-Vorgaben
- Unterstützung für:
  - Deckblatt mit Firmenlogo
  - Sperrvermerk
  - Abkürzungsverzeichnis & Glossar
  - Literaturverzeichnis mit `biblatex` + `biber`
- Getestet mit MikTeX & TeX Live



## Voraussetzungen

- LaTeX-Distribution (z. B. MiKTeX)



## 🧠 Eigene Zitierbefehle: `\vglcite` und `\directcite`

Dieses Template definiert zwei benutzerfreundliche LaTeX-Befehle für Fußnotenzitate nach dem deutschen Zitierstil (mit `biblatex`):

### 🔹 `\vglcite`
```latex
\vglcite[Seitenzahl]{quellenkey}
```
▶ Fügt eine Fußnote mit "Vgl." ein, z. B.:
```latex
\vglcite[15\psq]{meier2025}
```
🔎 Ausgabe im PDF:
> Vgl. Meier et al. (2025, S. 15 f.). <
📌 Verwendung: Für indirekte Zitate (sinngemäße Wiedergaben).


### 🔹 \directcite
```latex
\directcite[Seitenzahl]{quellenkey}
```
▶ Fügt eine Fußnote ohne "Vgl." ein, z. B.:
```latex
\directcite[45]{schmidt2019}
```
🔎 Ausgabe im PDF:
> Vgl. Schmidt (2025, S. 45). <
📌 Verwendung: Für direkte Zitate (wortwörtliche Übernahmen).



## ⚙️ Visual Studio Code Setup

### 💡 Versionskontrolle & Sicherung
Für Versionskontrolle, Zusammenarbeit und Sicherung wird die Nutzung von Git und GitHub empfohlen:
- Änderungen lassen sich nachvollziehen und bei Bedarf zurücksetzen
- Sicherung durch Remote-Repository (z. B. auf GitHub) vor Datenverlust.
- Ideal für Teamarbeit oder Studienprojekte

### 📦 Erweiterungsempfehlung (`.vscode/extensions.json`)
Um sicherzustellen, dass alle notwendigen VS Code-Erweiterungen installiert sind, kannst du folgende Datei anlegen:

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

Erstelle im Projektordner einen Ordner `.vscode` und füge folgende `settings.json`-Datei hinzu:

```json
{
    "ltex.language": "de",
    "latex-workshop.latex.outDir": "./OUTPUT",
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
