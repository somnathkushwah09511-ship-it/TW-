# LaTeX Tables — Complete Guide

## 1. Basic Table (tabular environment)

```latex
\begin{tabular}{|c|c|}
  \hline
  Name  & Marks \\
  \hline
  Alice & 90 \\
  Bob   & 85 \\
  \hline
\end{tabular}
```

### Column Alignment Options
| Specifier | Alignment |
|-----------|-----------|
| `l` | Left |
| `c` | Center |
| `r` | Right |
| `p{width}` | Fixed width, wraps text |
| `\|` | Vertical line |
| `\|\|` | Double vertical line |

## 2. Horizontal Lines
```latex
\hline          % Single horizontal line
\hline\hline    % Double horizontal line
```

## 3. Floating Table with Caption

```latex
\begin{table}[h!]       % Placement: h=here, t=top, b=bottom, p=separate page
  \centering
  \begin{tabular}{||c c c c||}
    \hline
    Col1 & Col2 & Col2 & Col3 \\[0.5ex]
    \hline\hline
    1 & 6 & 87837 & 787 \\
    2 & 545 & 18744 & 7560 \\
    3 & 88 & 788 & 6344 \\[1ex]
    \hline
  \end{tabular}
  \caption{Table to test captions and labels.}
  \label{table:1}
\end{table}

% Reference it:
Table~\ref{table:1} is an example of a referenced element.
```

### Table Placement Options
| Option | Meaning |
|--------|---------|
| `h` | Here (approximately) |
| `t` | Top of page |
| `b` | Bottom of page |
| `p` | Special float page |
| `!` | Override LaTeX parameters |
| `H` | Exactly here (like `h!`) |

## 4. Multi-Column Span

```latex
\usepackage{multirow}  % needed for multirow

\begin{tabular}{|p{1.5cm}|p{1.5cm}|p{1.5cm}|}
  \hline
  \multicolumn{3}{|c|}{Books} \\  % spans 3 cols
  \hline
  Food name & Author & Publication \\\hline
  Book1 & Author1 & P1 \\
  Book1 & Author2 & P2 \\\hline
\end{tabular}
```

## 5. Multi-Row Span

```latex
\usepackage{multirow}

\begin{tabular}{|c|c|c|}
  \hline
  col1 & col2 & col3 \\
  \hline
  \multirow{3}{4em}{Multiple row} & cell2 & cell3 \\
                                  & cell5 & cell6 \\
                                  & cell8 & cell9 \\
  \hline
\end{tabular}
```

## 6. Sizing: Row Height & Column Width

```latex
\setlength{\arrayrulewidth}{0.5mm}   % Border thickness
\setlength{\tabcolsep}{18pt}         % Space between text and border
\renewcommand{\arraystretch}{1.5}    % Row height (1.5x default)
```

## 7. Colored Tables

```latex
\usepackage{colortbl}
\usepackage{xcolor}

\begin{table}[h]
  \begin{tabular}{|>{\columncolor{red}}p{1.5cm}|p{1.5cm}|p{1.5cm}|}
    \hline
    \rowcolor{green}\multicolumn{3}{|c|}{Country List} \\\hline
    Country & ALPHA & BETA \\\hline
    Afghanistan & AF & \cellcolor{yellow}AFG \\
    \rowcolor{blue}Albania & AL & ALB \\\hline
  \end{tabular}
\end{table}
```

Color commands:
- `\rowcolor{color}` — entire row
- `\columncolor{color}` — entire column (in column spec)
- `\cellcolor{color}` — single cell

## 8. Fixed-Width Columns with p{}

```latex
\begin{tabular}{|p{3cm}|p{5cm}|}
  \hline
  Short & This is a longer text that will wrap automatically \\
  \hline
\end{tabular}
```

## 9. Summary Cheatsheet

```latex
% Basic table
\begin{tabular}{|l|c|r|}

% Floating table
\begin{table}[h!]
  \centering
  \begin{tabular}{...}
  \end{tabular}
  \caption{Title}
  \label{tab:name}
\end{table}

% Multi-column
\multicolumn{n}{alignment}{content}

% Multi-row
\multirow{n}{width}{content}

% Colors
\rowcolor{color}
\cellcolor{color}
\columncolor{color}  % in column spec
```
