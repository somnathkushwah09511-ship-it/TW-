# LaTeX Basics — Document Structure & Formatting

## 1. What is LaTeX?

- **LaTeX** is a document preparation system based on the **TeX** typesetting system.
- Portable, free, and professional quality.
- Perfect for mathematical formulae, tables of contents, footnotes, and bibliographies.
- **LaTeX vs MS Word**: As complexity increases, LaTeX stays manageable while Word becomes difficult.

## 2. Tools

### Offline
| OS | Tools |
|----|-------|
| Windows | MiKTeX, TeXnicCenter, TeXstudio |
| Linux | TeX Live, Kile, TeXstudio |

### Online
- **Overleaf** (most popular), Papeeria, CoCalc

## 3. Input & Output

- Source file: `.tex` (plain text)
- Output formats: **PDF** (.pdf), DVI (.dvi), PostScript (.ps), RTF (.rtf)

## 4. Document Structure

```latex
\documentclass{article}   % MUST be first line
% Preamble: packages and settings go here
\usepackage{graphicx}

\begin{document}           % Document body starts
  Your content here
\end{document}             % Document ends
```

> ⚠️ Only `\documentclass` and `\usepackage` go in the preamble!

## 5. Document Classes

| Class | Use Case |
|-------|----------|
| `article` | Papers, short documents (sections, no chapters) |
| `report` | Reports, theses (chapters available) |
| `book` | Books, dissertations (front/back matter) |
| `letter` | Formal correspondence |
| `beamer` | Presentations/slides |
| `exam` | Tests and quizzes |
| `IEEEtran` | IEEE papers |
| `ACM` | ACM conference papers |

```latex
\documentclass[12pt]{article}         % 12pt font
\documentclass[twocolumn]{article}    % Two-column layout
\documentclass[a4paper]{article}      % A4 paper
\documentclass[11pt,letterpaper]{report}
```

## 6. Title, Author, Date

```latex
\title{Hello, World! In LaTeX}
\author{Neeta Nain}
\date{28/07/2026}      % or \date{\today}
\maketitle             % Must be after \begin{document}
```

## 7. Abstract

```latex
\begin{abstract}
  Abstract text goes here.
\end{abstract}
```
> Usually appears after `\maketitle`.

## 8. Sections & Hierarchy

```latex
\section{Section Title}
\subsection{Subsection Title}
\subsubsection{Subsubsection Title}
```

- Auto-numbered: 1, 1.1, 1.1.1 ...
- Use `\section*{Title}` for **unnumbered** sections (e.g., Acknowledgements)
- Control numbering: `\setcounter{section}{3}` → next section = 4
- Roman numerals: `\renewcommand{\thesection}{\Roman{section}}`

## 9. Text Formatting

### Font Sizes
```latex
{\tiny Tiny}  {\scriptsize Script}  {\footnotesize Footnote}
{\small Small}  {\normalsize Normal}  {\large Large}
{\Large Larger}  {\LARGE Very Large}  {\huge Huge}  {\Huge Largest}
```

### Text Alignment
```latex
\begin{flushleft} Left-aligned text \end{flushleft}
\begin{center}    Centered text     \end{center}
\begin{flushright} Right-aligned   \end{flushright}
```

### Font Styles
```latex
\textbf{Bold}     \textit{Italic}    \emph{Emphasized}
\texttt{Typewriter}  \textsf{Sans-serif}  \underline{Underline}
```

## 10. Special Characters

Reserved characters in LaTeX: `$ & % # _ { } ~ ^ \`

```latex
\$  \&  \%  \#  \_  \{  \}   % Print these literally
```

## 11. Comments
```latex
% This is a comment — not shown in output
```

## 12. Spaces & Paragraphs

```latex
% Empty line = new paragraph
% Multiple spaces = one space (LaTeX ignores extras)

\vspace{10mm}     % Vertical space
\hspace{1cm}      % Horizontal space
\noindent         % No indent on this paragraph
\setlength{\parindent}{2em}   % Global paragraph indent
\setlength{\parskip}{1em}     % Space between paragraphs
```

## 13. Page Styles

```latex
\pagestyle{plain}      % Page number at bottom center (default)
\pagestyle{headings}   % Chapter/section in header
\pagestyle{empty}      % No header or footer
```

### Custom Headers/Footers with fancyhdr
```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}
\fancyhead[L]{Left Header}
\fancyhead[C]{Center Header}
\fancyhead[R]{Right Header}
\fancyfoot[C]{\thepage}       % Page number in center footer
```

## 14. Page Layout

```latex
\usepackage{geometry}
\geometry{left=2.5cm, right=2.5cm, top=2.5cm, bottom=2.5cm}
```

Paper sizes: `a4paper`, `letterpaper`

## 15. Page Breaks & Line Breaks

```latex
\\              % Manual line break within paragraph
\newpage        % Force new page
\pagebreak      % Alternative page break
\clearpage      % Page break + flush all floats
\linebreak      % Line break with stretch
\mbox{text}     % Keep words together (no break)

\begin{samepage}
  Paragraph 1   % Prevents page break between these
  Paragraph 2
\end{samepage}
```

## 16. Hyphenation

```latex
manu\-script    % Suggests hyphenation point (only used if needed)
```

## 17. Lists

```latex
% Bulleted list
\begin{itemize}
  \item Apple
  \item Mango
\end{itemize}

% Numbered list
\begin{enumerate}
  \item First
  \item Second
\end{enumerate}

% Description list
\begin{description}
  \item[CPU] Central Processing Unit
  \item[RAM] Random Access Memory
\end{description}
```

### Custom Lists with enumitem
```latex
\usepackage{enumitem}
\setlist[itemize]{label=\textbullet, leftmargin=*}
```

## 18. Cross References

```latex
\label{sec:intro}       % Define label
\ref{sec:intro}         % Reference number
\pageref{sec:intro}     % Reference page number

% Example
\section{Introduction}
\label{sec:intro}
See Section~\ref{sec:intro} on page~\pageref{sec:intro}.
```

## 19. Bibliography

```latex
% In document:
This is explained in \cite{lamport}.

\begin{thebibliography}{9}
  \bibitem{lamport}
    Leslie Lamport,
    \textit{LaTeX: A Document Preparation System.}
\end{thebibliography}
```

## 20. Title Page Customization

```latex
\title{\Huge \bfseries My Custom Title}
\author{\Large John Doe \\ \smallskip Department of CS}
\date{August 21, 2025}
\begin{document}
\maketitle
% Extra info below title:
\begin{center}
  \vspace{1cm}
  \textbf{Supervisor:} Dr. Smith \\
  \textbf{Course:} Technical Writing
\end{center}
```

## 21. Custom Fonts

```latex
% Change section fonts:
\usepackage{sectsty}
\sectionfont{\Large\bfseries\color{blue}}
\subsectionfont{\itshape\color{red}}

% System fonts (XeLaTeX/LuaLaTeX only):
\usepackage{fontspec}
\setmainfont{Georgia}
\setsansfont{Arial}
\setmonofont{Courier New}
```

## 22. Colors

```latex
\usepackage{xcolor}
\pagecolor{yellow!10}         % 10% yellow background
\textcolor{red}{Red text}
```

## 23. Common Errors

| Error | Likely Cause |
|-------|-------------|
| `Undefined control sequence` | Typo in command |
| `Missing \begin{document}` | Preamble issue |
| `Lonely \item` | `\item` outside list environment |
| `Too many columns in tabular` | More `&` than column spec |
| `Option clash for package` | Package loaded twice with diff options |
| `Overfull \hbox` | Text too wide — try `\linebreak` or `\sloppy` |

### Debug Strategy
1. Check log file for error line number
2. Undo recent changes and recompile
3. Compile often while writing
4. Reduce to minimal document if needed
