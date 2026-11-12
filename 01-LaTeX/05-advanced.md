# LaTeX Advanced — Environments, Boxes & Indexing

## 1. Custom Environments

```latex
% Define a custom environment:
\newenvironment{myenv}
  {\begin{trivlist}\item[]}   % Begin code
  {\end{trivlist}}             % End code

\begin{myenv}
  This is inside a custom environment.
\end{myenv}
```

## 2. Trivlist — Unlabeled Vertical List

```latex
\begin{trivlist}
  \item First item without label
  \item Second item
\end{trivlist}
```
> No bullet points or numbers — useful as base for custom environments.

## 3. Lengths & Spacing

```latex
\setlength{\parindent}{2em}    % Paragraph indent
\setlength{\parskip}{1em}      % Space between paragraphs

% Horizontal space:
This is\hspace{1cm}spaced text.

% Vertical space:
Above paragraph.\vspace{0.5cm}
Below paragraph.
```

## 4. Advanced Box Usage

### LR Box (Horizontal content)
```latex
\newsavebox{\mybox}
\savebox{\mybox}{Some saved content}
\usebox{\mybox}
```

### Combining Parbox and Framebox
```latex
\newsavebox{\mybox}
\savebox{\mybox}{
  \parbox{4cm}{
    \framebox[4cm][c]{Framed paragraph box}
  }
}
\usebox{\mybox}
\usebox{\mybox}    % Reuse multiple times
```

## 5. Section Numbering Control

```latex
% Custom numbering start:
\setcounter{section}{3}        % Next \section = 4
\section{Next Section}         % Numbered as "4"

% Roman numerals for sections:
\renewcommand{\thesection}{\Roman{section}}

% Unnumbered sections:
\section*{Acknowledgments}
```

## 6. Equation Numbering

```latex
% Numbered equation:
\begin{equation}
  E = mc^2
\end{equation}

% Unnumbered (needs amsmath):
\begin{equation*}
  a^2 + b^2 = c^2
\end{equation*}

% Reference an equation:
\begin{equation}
  \label{eq:einstein}
  E = mc^2
\end{equation}
See equation~\ref{eq:einstein}.
```

## 7. Document Style Customization

```latex
% Section headings:
\usepackage{sectsty}
\sectionfont{\Large\bfseries\color{blue}}
\subsectionfont{\itshape\color{red}}

% Page colors:
\usepackage{xcolor}
\pagecolor{yellow!10}

% Custom headers:
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}
\fancyhead[L]{My Document}
\fancyhead[R]{\today}
\fancyfoot[C]{Page \thepage}
```

## 8. Summary Table: Common Packages

| Area | Package | Key Command |
|------|---------|-------------|
| Math | `amsmath` | `\begin{align}`, `\begin{equation*}` |
| Images | `graphicx` | `\includegraphics` |
| Colors | `xcolor` | `\textcolor`, `\pagecolor` |
| Margins | `geometry` | `\geometry{...}` |
| Headers | `fancyhdr` | `\fancyhead`, `\fancyfoot` |
| Tables | `multirow` | `\multirow` |
| Tables | `colortbl` | `\rowcolor`, `\cellcolor` |
| Lists | `enumitem` | `\setlist` |
| Fonts | `fontspec` | `\setmainfont` |
| Sections | `sectsty` | `\sectionfont` |
| Index | `makeidx` | `\index`, `\printindex` |
| Links | `hyperref` | `\href`, `\url` |

## 9. Complete Workflow Summary

```
Document Types:
article → \section (no chapters)
report  → \chapter + \section
book    → \frontmatter + \chapter + \backmatter
beamer  → \begin{frame}...\end{frame}

Compilation:
pdflatex file.tex              → Basic PDF
bibtex + pdflatex (×2)         → With references
makeindex + pdflatex (×2)      → With index

Key Rule:
\documentclass and \usepackage → ONLY in preamble
```
