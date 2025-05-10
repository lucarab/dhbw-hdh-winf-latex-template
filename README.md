# DHBW Heidenheim – LaTeX Thesis Template (Wirtschaftsinformatik)

Dieses Repository enthält eine LaTeX-Vorlage für wissenschaftliche Arbeiten im Studiengang **Wirtschaftsinformatik** an der **DHBW Heidenheim**.  
Die Vorlage orientiert sich an den formalen Anforderungen der Hochschule und ist geeignet für Projektarbeiten, Bachelorarbeiten oder Seminararbeiten.

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

## ⚙️ Visual Studio Code Setup

Für die komfortable Bearbeitung mit **Visual Studio Code** wird die Verwendung der Erweiterung [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) empfohlen.

### `.vscode/settings.json`

Erstelle im Projektordner einen Ordner `.vscode` und füge folgende `settings.json`-Datei hinzu:

```json
{
  "ltex.language": "de",
  "latex-workshop.latex.outDir": "./OUTPUT",
  "latex-workshop.latex.recipe.default": "lastUsed",
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
### 📦 Erweiterungsempfehlung (`.vscode/extensions.json`)

Um sicherzustellen, dass alle notwendigen VS Code-Erweiterungen installiert sind, kannst du folgende Datei anlegen:

```json
{
  "recommendations": [
    "james-yu.latex-workshop",    // Für LaTeX-Kompilierung & PDF-Preview
    "valentjn.vscode-ltex"        // Für Grammatik- und Rechtschreibprüfung in Deutsch
  ]
}
```
