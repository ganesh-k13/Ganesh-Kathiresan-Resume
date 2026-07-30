# AltaCV LaTeX CV/Résumé - VS Code Compilation Guide

**📄 [Open Resume (PDF)](https://ganesh-k13.github.io/Ganesh-Kathiresan-Resume/)**

A modern LaTeX CV template with VS Code integration for easy PDF compilation.

## Quick Start with VS Code

### 1. Install Required Software

**Install LaTeX Distribution:**
- **macOS**: Install [MacTeX](https://www.tug.org/mactex/)
- **Windows**: Install [MiKTeX](https://miktex.org/) or [TeX Live](https://www.tug.org/texlive/)
- **Linux**: Install TeX Live via package manager

**Install VS Code Extension:**
- Open VS Code
- Go to Extensions (Cmd+Shift+X / Ctrl+Shift+X)
- Search for "LaTeX Workshop" by James Yu
- Install the extension

### 2. Compile Your CV

**Method 1: Keyboard Shortcut**
- Open your `.tex` file in VS Code
- Press `Cmd+Alt+B` (macOS) or `Ctrl+Alt+B` (Windows/Linux)

**Method 2: Command Palette**
- Press `Cmd+Shift+P` (macOS) or `Ctrl+Shift+P` (Windows/Linux)
- Type "LaTeX Workshop: Build LaTeX project"
- Press Enter

**Method 3: Right-click Menu**
- Right-click on your `.tex` file in the editor
- Select "Build LaTeX project"

The extension automatically handles the required compilation sequence: `pdflatex + biber + pdflatex`

### Bibliography (Publications / Patents)

`ganeshk.bbl` is committed to the repo, so a plain `pdflatex ganeshk.tex` renders
the full CV — including Publications and Patents — without needing `biber`.

If you edit `sample.bib` or `pubs-num.tex`, regenerate it:

```bash
pdflatex ganeshk.tex && biber ganeshk && pdflatex ganeshk.tex
```

Skipping `biber` after a `.bib` change is quiet, not loud: `pdflatex` still exits
0 and just logs `Empty bibliography` / stale entries. Commit the refreshed
`ganeshk.bbl` alongside your `.bib` edits.

### 3. View Your PDF
- The compiled PDF appears in the same directory
- Use `Cmd+Alt+V` (macOS) or `Ctrl+Alt+V` (Windows/Linux) to preview in VS Code

## AltaCV Features

### Template Layout
Uses the `paracol` package for two-column layout that breaks across pages:

```latex
\columnratio{0.6}  % 60:40 left/right ratio

\begin{paracol}{2}
\cvsection{Experience}
% Left column content

\switchcolumn
\cvsection{Education}
% Right column content
\end{paracol}
```

### Personal Information Fields
```latex
\personalinfo{
  \email{your.email@example.com}
  \phone{000-00-0000}
  \location{City, Country}
  \linkedin{your-linkedin}
  \github{your-github}
}
```

### Custom Information Fields
```latex
% Define new field
\NewInfoField{gitlab}{\faGitlab}[https://gitlab.com/]
\gitlab{your-handle}

% Or use directly
\printinfo{\faPaw}{Custom info}[https://example.com/]
```

### Clickable Hyperlinks
Use the `withhyper` document class option for clickable links:

```latex
\documentclass[10pt,a4paper,withhyper]{altacv}
```

### Document Class Options
- `normalphoto`: Non-circular photos
- `ragged2e`: Better text justification
- `withhyper`: Clickable hyperlinks

### Skills and Charts
```latex
% Skill bars
\cvskill{Python}{5}
\cvskill{JavaScript}{4}

% Wheel chart
\wheelchart{1.5cm}{0.5cm}{
  6/8em/accent!30/Sleeping \& dreaming about work,
  3/8em/accent!40/Public speaking \& training,
  8/8em/accent!60/Spending time with family,
  2/10em/accent/Writing \& blogging,
  5/6em/accent!20/Programming
}
```

## Customization

### Colors
```latex
\colorlet{accent}{blue!70!black}
\colorlet{emphasis}{black}
\colorlet{heading}{black}
\colorlet{headingrule}{black}
\colorlet{subheading}{emphasis}
\colorlet{body}{black!80!white}
\colorlet{name}{heading}
\colorlet{tagline}{accent}
```

### Fonts
```latex
\renewcommand{\namefont}{\Huge\rmfamily\bfseries}
\renewcommand{\taglinefont}{\large\bfseries}
\renewcommand{\personalinfofont}{\footnotesize}
\renewcommand{\cvsectionfont}{\LARGE\rmfamily\bfseries}
\renewcommand{\cvsubsectionfont}{\large\bfseries}
```

## Troubleshooting

### Common Issues
- **Missing fonts**: Install required font packages or use different fonts
- **Bibliography errors**: Ensure `sample.bib` file exists and is properly formatted
- **Image errors**: Check that logo files exist in the correct directory
- **Compilation fails**: Check LaTeX Workshop output panel for detailed error messages

### VS Code LaTeX Workshop Settings
Add to your VS Code `settings.json`:
```json
{
  "latex-workshop.latex.autoBuild.run": "never",
  "latex-workshop.showContextMenu": true,
  "latex-workshop.intellisense.package.enabled": true
}
```

---

**Credit**: AltaCV template v1.7.4 (30 Jul 2025), by LianTze Lim (liantze@gmail.com)
