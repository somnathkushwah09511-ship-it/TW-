# LaTeX Figures, Colors & Picture Environment

## 1. Including Images

```latex
% Preamble:
\usepackage{graphicx}

% In document:
\begin{figure}[h]
  \centering
  \includegraphics[width=0.5\textwidth]{example-image}
  \caption{Sample Figure}
  \label{fig:sample}
\end{figure}
```

### includegraphics Options
```latex
\includegraphics[width=5cm]{img}           % Fixed width
\includegraphics[height=3cm]{img}          % Fixed height
\includegraphics[width=0.5\textwidth]{img} % Half text width
\includegraphics[scale=0.7]{img}           % Scale factor
\includegraphics[angle=90]{img}            % Rotate 90°
```

### Supported Formats
- PDFLaTeX: **PNG, JPG, PDF**
- LaTeX (DVI): **EPS**

## 2. Figure Placement

| Option | Meaning |
|--------|---------|
| `[h]` | Here |
| `[t]` | Top of page |
| `[b]` | Bottom of page |
| `[p]` | Float page |
| `[H]` | Exactly here (`\usepackage{float}` required) |

## 3. Colors in LaTeX

```latex
\usepackage{xcolor}

% Text color:
\textcolor{red}{Red text}
\textcolor{blue!50}{50% blue}

% Background color:
\colorbox{yellow}{highlighted text}

% Page background:
\pagecolor{yellow!10}    % 10% yellow tint

% Custom color definition:
\definecolor{myblue}{RGB}{0, 102, 204}
\textcolor{myblue}{Custom blue text}
```

### Predefined Colors
`black`, `white`, `red`, `green`, `blue`, `yellow`, `cyan`, `magenta`, `gray`, `orange`, `violet`

### Color Mixing
```latex
blue!50          % 50% blue
blue!50!red      % 50% blue + 50% red
blue!50!white    % 50% blue + 50% white
```

## 4. Boxes

### framed box
```latex
\framebox[5cm][c]{Centered text in a box}
\framebox[5cm][l]{Left-aligned text}
\framebox[5cm][r]{Right-aligned text}
% [width][alignment]{content}
```

### unframed box
```latex
\makebox[4cm][c]{Unframed centered text}
```

### paragraph box (multiline)
```latex
\parbox{5cm}{
  This text wraps inside a fixed-width box.
}
```

### raise/lower content
```latex
Normal text \raisebox{1ex}{Raised} \raisebox{-1ex}{Lowered}
```

### horizontal/vertical rules
```latex
\rule{3cm}{1pt}    % Horizontal rule: 3cm wide, 1pt thick
\rule{1pt}{2cm}    % Vertical rule: 2cm high, 1pt wide
```

### save & reuse boxes
```latex
\newsavebox{\mybox}
\savebox{\mybox}{Content to save}
\usebox{\mybox}    % Use anywhere, any number of times
```

## 5. Picture Environment

```latex
\begin{picture}(width,height)(offset-x,offset-y)
  % Drawing commands here
\end{picture}
```

### Drawing Commands
```latex
\put(x,y){object}             % Place object at (x,y)
\put(10,20){\circle{5}}       % Circle: radius 5
\put(10,20){\circle*{5}}      % Filled circle
\put(0,0){\line(1,0){50}}     % Horizontal line, length 50
\put(0,0){\line(0,1){30}}     % Vertical line, length 30
\put(0,0){\line(1,1){20}}     % Diagonal line (slope 1,1)
\put(10,10){\vector(1,0){40}} % Arrow (horizontal)
\put(0,0){\framebox(60,30){}} % Rectangle
\put(5,5){Text at (5,5)}      % Text
```

## 6. MakeIndex — Creating an Index

```latex
% Preamble:
\usepackage{makeidx}
\makeindex

% In document:
\index{gnats}          % Simple entry
\index{gnat!size of}   % Subentry: "gnat, size of"
\index{gnus!good|(}    % Begin page range
\index{gnus!good|)}    % End page range
\index{bat|see{bat}}   % Cross-reference

% At end of document:
\printindex
```

### Compilation Order
```
latex file.tex
makeindex file
latex file.tex    (again)
```

## 7. BibTeX — Bibliography

```latex
% In document:
\bibliography{refs}            % refs.bib file
\bibliographystyle{plain}      % Style: plain, ieeetr, alpha, etc.

% Cite:
\cite{knuth1984}
```

### .bib File Format
```bibtex
@BOOK{lamport1994,
  AUTHOR    = "Leslie Lamport",
  TITLE     = "LaTeX: A Document Preparation System",
  PUBLISHER = {Addison-Wesley},
  ADDRESS   = {Reading, MA},
  YEAR      = 1994
}

@ARTICLE{einstein1905,
  AUTHOR  = "Albert Einstein",
  TITLE   = "On the Electrodynamics of Moving Bodies",
  JOURNAL = "Annalen der Physik",
  YEAR    = 1905,
  VOLUME  = 17
}

@INPROCEEDINGS{doe2024,
  AUTHOR    = "Jane Doe",
  TITLE     = "New Methods",
  BOOKTITLE = "Proc. of the Conference",
  YEAR      = 2024
}
```

### BibTeX Entry Types

| Type | Required Fields |
|------|----------------|
| `@article` | author, title, journal, year |
| `@book` | author/editor, title, publisher, year |
| `@inproceedings` | author, title, booktitle, year |
| `@techreport` | author, title, institution, year |
| `@misc` | none required |

### Compilation Order
```
latex file.tex
bibtex file
latex file.tex
latex file.tex    (3rd pass resolves all references)
```

### Name Formatting in BibTeX
```bibtex
AUTHOR = "Doe, Jane"           % Last, First
AUTHOR = "Jane Doe"            % First Last
AUTHOR = "Jane Doe and John Smith"   % Multiple authors
AUTHOR = "Jane Doe and others"       % et al.
```
