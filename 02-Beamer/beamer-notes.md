# Part 2: Beamer — Presentations in LaTeX

> **Source**: Lecture slides by Prof. Neeta Nain, MNIT Jaipur

## What is Beamer?

**Beamer** is a LaTeX document class for creating professional presentations (slides). It is the LaTeX equivalent of PowerPoint.

---

## 1. Basic Structure

```latex
\documentclass{beamer}
\usepackage{graphicx}

% Title slide info:
\title{My Presentation}
\author{Neeta Nain}
\institute{MNIT Jaipur}
\date{\today}

\begin{document}

% Title slide:
\begin{frame}
  \titlepage
\end{frame}

% Table of Contents:
\begin{frame}{Outline}
  \tableofcontents
\end{frame}

% Content slide:
\begin{frame}{My First Slide}
  This is the content of the slide.
\end{frame}

\end{document}
```

---

## 2. Themes

```latex
\usetheme{Warsaw}      % Common themes:
% Madrid, Copenhagen, Berlin, Singapore, CambridgeUS,
% AnnArbor, Boadilla, boxes, default, etc.

\usecolortheme{default}   % Color themes:
% albatross, crane, beaver, whale, etc.
```

---

## 3. Frames (Slides)

```latex
% Basic frame:
\begin{frame}{Frame Title}
  Content here
\end{frame}

% Frame with subtitle:
\begin{frame}{Title}{Subtitle}
  Content
\end{frame}

% Frame with options:
\begin{frame}[allowframebreaks]{Long Content}
  Very long content that spans multiple slides
\end{frame}

% Fragile frame (needed for verbatim/code):
\begin{frame}[fragile]{Code Example}
  \begin{verbatim}
    print("Hello World")
  \end{verbatim}
\end{frame}
```

> ⚠️ Always use `[fragile]` for frames with `verbatim` or code blocks!

---

## 4. Bullet Points & Lists

```latex
\begin{frame}{Key Points}
  \begin{itemize}
    \item First point
    \item Second point
    \begin{itemize}
      \item Sub-point
    \end{itemize}
  \end{itemize}
\end{frame}

\begin{frame}{Numbered List}
  \begin{enumerate}
    \item Step 1
    \item Step 2
    \item Step 3
  \end{enumerate}
\end{frame}
```

---

## 5. Overlays & Animations

```latex
% Reveal items one by one:
\begin{itemize}
  \item<1-> First (shown from slide 1)
  \item<2-> Second (shown from slide 2)
  \item<3-> Third (shown from slide 3)
\end{itemize}

% Pause between items:
\begin{itemize}
  \item First item
  \pause
  \item Second item (appears after pause)
  \pause
  \item Third item
\end{itemize}

% Show only on specific slides:
\only<2>{This text appears only on overlay 2}
\visible<3->{Visible from overlay 3 onwards}
\uncover<2-4>{Visible overlays 2 through 4}
```

---

## 6. Blocks

```latex
% Standard block (blue):
\begin{block}{Block Title}
  Content of the block.
\end{block}

% Alert block (red):
\begin{alertblock}{Warning!}
  This is an important warning.
\end{alertblock}

% Example block (green):
\begin{exampleblock}{Example}
  This is an example.
\end{exampleblock}
```

---

## 7. Columns Layout

```latex
\begin{frame}{Two Columns}
  \begin{columns}
    \column{0.5\textwidth}
      Left column content here.
      \includegraphics[width=\textwidth]{image1}

    \column{0.5\textwidth}
      Right column content here.
      \begin{itemize}
        \item Point 1
        \item Point 2
      \end{itemize}
  \end{columns}
\end{frame}
```

---

## 8. Mathematical Content

```latex
\begin{frame}{Math Slide}
  Einstein's equation:
  \[ E = mc^2 \]

  And the quadratic formula:
  \[ x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a} \]
\end{frame}
```

---

## 9. Navigation & Structure

```latex
% Sections (create navigation bar):
\section{Introduction}
\subsection{Background}

% Table of contents (auto from sections):
\begin{frame}{Outline}
  \tableofcontents[currentsection]
\end{frame}
```

---

## 10. Abstract in Beamer

```latex
% Use a frame instead of abstract environment:
\begin{frame}{Abstract}
  This presentation covers the basics of LaTeX
  document structure, including title pages
  and abstract environments.
\end{frame}
```

---

## 11. Useful Commands Summary

| Task | Command |
|------|---------|
| New slide | `\begin{frame}{Title}...\end{frame}` |
| Theme | `\usetheme{Warsaw}` |
| Color theme | `\usecolortheme{whale}` |
| Pause | `\pause` |
| Overlay | `\item<2->` |
| Block | `\begin{block}{Title}` |
| Alert block | `\begin{alertblock}{Title}` |
| Example block | `\begin{exampleblock}{Title}` |
| Columns | `\begin{columns}\column{0.5\textwidth}` |
| Title page | `\titlepage` |
| TOC | `\tableofcontents` |

---

## 12. Complete Minimal Example

```latex
\documentclass{beamer}
\usetheme{Madrid}

\title{Technical Writing}
\author{Neeta Nain}
\institute{MNIT Jaipur}
\date{\today}

\begin{document}

\begin{frame}
  \titlepage
\end{frame}

\begin{frame}{Introduction}
  \begin{itemize}
    \item LaTeX for professional documents
    \pause
    \item Beamer for presentations
    \pause
    \item Git for version control
  \end{itemize}
\end{frame}

\begin{frame}{Important Formula}
  \begin{block}{Einstein's Equation}
    \[ E = mc^2 \]
  \end{block}
\end{frame}

\end{document}
```

---

> 💡 **Tip**: Beamer supports overlays for step-by-step reveals, but avoid using too many — keep slides simple and clear.
