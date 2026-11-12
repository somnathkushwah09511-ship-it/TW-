# Technical Writing & Documentation Notes

Comprehensive, simplified, and practical reference notes compiled from the **Technical Writing (TW)** lecture series by **Dr. Neeta Nain (MNIT Jaipur)**.

Designed for quick review, university exams, and practical engineering documentation workflows.

---

## 🗂️ Four Core Modules

```
TW-Notes-Repo/
├── 01-LaTeX/              → Professional typeset papers, reports & math
├── 02-Beamer/             → Code-driven academic & conference slide decks
├── 03-Google-Docs-Doxygen/ → Team collaboration (Docs) + Code API docs (Doxygen)
└── 04-Git-GitHub/         → Version control, branching workflows & GitHub PRs
```

---

## 📖 Module Overviews & Quick Links

### [01. LaTeX: Scientific Document Typesetting](./01-LaTeX/)
- **[01-basics.md](./01-LaTeX/01-basics.md)**: Document classes (`article`, `report`), font styles, sectioning, itemized & enumerated lists.
- **[02-math.md](./01-LaTeX/02-math.md)**: Inline math `$ ... $`, display formulas `\[ ... \]`, Greek symbols, piecewise functions, matrices (`pmatrix`, `bmatrix`).
- **[03-tables.md](./01-LaTeX/03-tables.md)**: `tabular` syntax, column alignments (`l`, `c`, `r`, `p{width}`), row/col spans (`\multirow`, `\multicolumn`), colored cells.
- **[04-figures.md](./01-LaTeX/04-figures.md)**: Image scaling & placement floats (`[h]`, `[t]`, `[H]`), color packages, BibTeX bibliography management (`.bib`), and index generation.
- **[05-advanced.md](./01-LaTeX/05-advanced.md)**: Custom environments, paragraph geometry, boxes (`parbox`, `framebox`), counters, and heading customization.

### [02. Beamer: Presentations in Code](./02-Beamer/)
- **[README.md](./02-Beamer/README.md)** & **[beamer-notes.md](./02-Beamer/beamer-notes.md)**:
  - Slide frames (`\begin{frame}`) and presentation themes (`Madrid`, `Warsaw`).
  - Overlay sequencing: click-by-click item reveals (`\pause`, `\item<1->`).
  - Colored focus containers: `block`, `alertblock`, `exampleblock`.
  - Multi-column slides (`\begin{columns}`) and syntax-highlighted code with `[fragile]`.

### [03. Collaborative & Code Documentation (Google Docs & Doxygen)](./03-Google-Docs-Doxygen/)
- **[01-google-docs.md](./03-Google-Docs-Doxygen/01-google-docs.md)**:
  - Real-time team collaboration, Suggesting mode (track changes), and comment assignments (`@teammate`).
  - Document outline hierarchy, auto-generated Tables of Contents, and citation manager integration.
- **[02-doxygen.md](./03-Google-Docs-Doxygen/02-doxygen.md)**:
  - Automated code documentation engine from source code comments (`/** ... */` in C++/Java, docstrings in Python).
  - Common tags: `\brief`, `\param`, `\return`, `\author`, `\see`, `\note`.
  - 4-step build workflow: `doxygen -g Doxyfile` → configure → compile → explore `html/index.html`.
  - Visual inheritance trees and call graphs with Graphviz (`HAVE_DOT = YES`).

### [04. Git & GitHub: Version Control](./04-Git-GitHub/)
- **[01-git-basics.md](./04-Git-GitHub/01-git-basics.md)**: Working directory vs. Staging vs. Repository, basic commit cycles, inspection (`git status`, `git log --oneline`, `git diff`), and `.gitignore`.
- **[02-github.md](./04-Git-GitHub/02-github.md)**: Remote repository setup (`git remote add origin`), SSH vs. GitHub CLI browser authentication, Issues, Projects, and Releases.
- **[03-collaboration.md](./04-Git-GitHub/03-collaboration.md)**: Feature branch development (`git switch -c`), pull requests (PRs), code review etiquette, and resolving merge conflicts step-by-step.

---

## ⚡ Quick Start: Daily Development Cheatsheet

```bash
# 1. LaTeX build
pdflatex document.tex
bibtex document
pdflatex document.tex

# 2. Doxygen build
doxygen Doxyfile
# Output generated in ./html/index.html

# 3. Git routine
git status
git add .
git commit -m "Your crisp summary message"
git push
```
