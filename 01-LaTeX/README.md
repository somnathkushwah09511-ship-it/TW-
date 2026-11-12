# LaTeX — Quick Review & Cheatsheet

> **Mindset**: LaTeX treats your document like code. You write logical content, and the compiler handles perfect typography, cross-referencing, and mathematical layout.

---

## ⚡ The 30-Second Mental Model

```latex
\documentclass{article}          % 1. Preamble: declare doc type (article, report, book, beamer)
\usepackage{amsmath, graphicx}   % 2. Import tools (math, images, colors, etc.)

\begin{document}                 % 3. Document Body
  \title{My Technical Paper}
  \author{Somnath Kushwah}
  \maketitle

  \section{Introduction}
  Hello world! My equation is $E = mc^2$.
\end{document}
```

---

## 📚 Topics & Fast Navigation

| File | What you'll learn |
|---|---|
| [01-basics.md](./01-basics.md) | Document structure, text styles, sections, itemized lists |
| [02-math.md](./02-math.md) | Inline vs display formulas, Greek symbols, matrices, multi-line equations |
| [03-tables.md](./03-tables.md) | Tabular syntax, row/col spans, border formatting, colored tables |
| [04-figures.md](./04-figures.md) | Image embedding, subfigures, color boxes, BibTeX citations |
| [05-advanced.md](./05-advanced.md) | Custom environments, counters, indexing (`makeidx`), page layouts |

---

## 🛠️ Essential Packages Cheat Sheet

| Need | Package | Most Used Command |
|---|---|---|
| **Formulas & Symbols** | `\usepackage{amsmath, amssymb}` | `\begin{align}`, `\begin{pmatrix}` |
| **Images & Figures** | `\usepackage{graphicx}` | `\includegraphics[width=0.8\linewidth]{...}` |
| **Colored Text/Tables** | `\usepackage{xcolor, colortbl}` | `\textcolor{blue}{...}`, `\rowcolor{gray!20}` |
| **Multi-row Cells** | `\usepackage{multirow}` | `\multirow{2}{*}{Merged}` |
| **Margins & Page size**| `\usepackage{geometry}` | `\geometry{a4paper, margin=1in}` |
| **Interactive Links** | `\usepackage{hyperref}` | `\url{...}`, `\href{url}{label}` |
