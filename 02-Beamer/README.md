# Beamer — Presentations in LaTeX

> **Mindset**: Beamer is presentation software driven by code. Instead of manually aligning slide boxes in PowerPoint, you declare frames and let Beamer structure slides, bullet sequences, and layout consistency.

---

## ⚡ The 30-Second Minimal Slide Deck

```latex
\documentclass{beamer}
\usetheme{Madrid}          % Try also: Warsaw, Copenhagen, Berlin, CambridgeUS
\usecolortheme{default}    % Try also: dolphin, crane, whale

\title{Technical Writing Workshop}
\author{Somnath Kushwah}
\institute{MNIT Jaipur}
\date{\today}

\begin{document}

\begin{frame}
  \titlepage             % Auto-generates clean title slide
\end{frame}

\begin{frame}{Roadmap}
  \tableofcontents       % Auto-built from \section tags
\end{frame}

\section{Core Concepts}
\begin{frame}{Why LaTeX for Slides?}
  \begin{itemize}
    \item Typeset formulas cleanly without screenshot pixelation
    \pause               % Pauses here until next click!
    \item Consistent themes across multi-author research decks
  \end{itemize}
\end{frame}

\end{document}
```

---

## 🎯 Key Ingredients Every Slide Needs

### 1. Step-by-Step Reveals (Overlays)
- Use `\pause` for a simple wait:
  ```latex
  Point 1
  \pause
  Point 2 (revealed on next click)
  ```
- Use `<range>` modifiers on items:
  ```latex
  \item<1-> Visible from slide 1 onwards
  \item<2-> Appears on slide 2
  \item<3>  Visible ONLY on slide 3
  ```

### 2. Highlighting with Blocks
```latex
% Normal Info Box (Blue)
\begin{block}{Note}
  Standard informative point.
\end{block}

% Alert Box (Red)
\begin{alertblock}{Warning}
  Overfitting occurs with high parameter counts.
\end{alertblock}

% Example Box (Green)
\begin{exampleblock}{Sample Calculation}
  $x^2 + y^2 = 1$ defines a unit circle.
\end{exampleblock}
```

### 3. Side-by-Side Columns
```latex
\begin{columns}
  \column{0.48\textwidth}
    \includegraphics[width=\linewidth]{diagram.png}
    
  \column{0.48\textwidth}
    \begin{itemize}
      \item Observation 1
      \item Observation 2
    \end{itemize}
\end{columns}
```

### 4. Code Blocks Require `[fragile]`
Whenever a frame contains `verbatim` or code listings, you **must** add `[fragile]`:
```latex
\begin{frame}[fragile]{Code Example}
\begin{verbatim}
  # Python code inside frame
  print("Hello MNIT")
\end{verbatim}
\end{frame}
```

---

## 🧭 Fast Reference Table

| Goal | Command |
|---|---|
| New Slide | `\begin{frame}{Title}{Subtitle} ... \end{frame}` |
| Reveal click-by-click | `\pause` or `\item<1->` |
| Split layout | `\begin{columns} \column{0.5\textwidth} ... \end{columns}` |
| Code block on slide | `\begin{frame}[fragile]` |
| Slide numbering / footer | Defined automatically by `\usetheme{...}` |
