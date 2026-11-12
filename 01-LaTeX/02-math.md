# LaTeX Math — Equations, Symbols & Matrices

> Package required: `\usepackage{amsmath, amssymb}`

## 1. Inline vs Display Math

```latex
% Inline math (stays within text line):
The area of a circle is $A = \pi r^2$.
% OR:
The area is \( A = \pi r^2 \).

% Display math (centered on its own line):
\[ E = mc^2 \]
% OR:
\begin{displaymath}
  E = mc^2
\end{displaymath}
```

## 2. Numbered Equations

```latex
\begin{equation}
  \int_0^1 x^2 \, dx = \frac{1}{3}
\end{equation}
% Auto-numbered as (1), (2), etc.

% Unnumbered (requires amsmath):
\begin{equation*}
  a^2 + b^2 = c^2
\end{equation*}
```

## 3. Superscripts & Subscripts

```latex
$x^2$          % x squared
$x^{10}$       % x to the 10th (braces needed for >1 char)
$a_i$          % subscript i
$a_{ij}$       % subscript ij
$a_i^2 + b_j^3$   % combined
```

## 4. Greek Letters

```latex
% Lowercase:
$\alpha, \beta, \gamma, \delta, \epsilon, \theta, \lambda, \mu, \pi, \sigma, \rho$

% Uppercase:
$\Alpha, \Beta, \Gamma, \Delta, \Theta, \Lambda, \Pi, \Sigma$
```

## 5. Common Math Symbols

### Fractions & Roots
```latex
$\frac{a}{b}$          % fraction
$\frac{a+b}{c}$        % complex fraction
$\sqrt{x}$             % square root
$\sqrt[3]{y}$          % cube root (nth root)
```

### Sums, Products, Integrals
```latex
$\sum_{i=1}^{n} x_i$          % Summation
$\prod_{k=1}^{m} k$           % Product
$\int_0^{\infty} e^{-x} dx$   % Integral
$\int_0^1 x^2 \, dx$          % \, adds small space
$\oint$                        % Contour integral
```

### Relations
```latex
$a \leq b$       % ≤
$a \geq b$       % ≥
$a \neq b$       % ≠
$a \approx b$    % ≈
$\infty$         % ∞
$a \in B$        % ∈
$a \notin B$     % ∉
```

### Set Theory
```latex
$A \cap B$       % Intersection ∩
$A \cup B$       % Union ∪
$A \subseteq B$  % Subset ⊆
$A \supseteq B$  % Superset ⊇
$\emptyset$      % Empty set ∅
```

### Binary Operators
```latex
$a \times b$     % ×
$a \otimes b$    % ⊗
$a \oplus b$     % ⊕
$a \cdot b$      % · (dot product)
```

## 6. Mathematical Fonts

```latex
$\mathcal{RQSZ}$    % Calligraphic (script)
$\mathfrak{RQSZ}$   % Fraktur
$\mathbb{R}$        % Blackboard bold (ℝ for Real numbers)
$\mathbb{Z}$        % ℤ integers
$\mathbb{N}$        % ℕ naturals
$\mathrm{text}$     % Roman (upright)
$\mathit{text}$     % Italic
$\mathbf{text}$     % Bold
$\mathsf{text}$     % Sans-serif
$\mathtt{text}$     % Typewriter
```

## 7. Array Environment

```latex
\[
\begin{array}{lcr}
  \text{Left} & \text{Center} & \text{Right} \\
  a & b & c \\
  1 & 2 & 3 \\
\end{array}
\]
```

### Piecewise Functions
```latex
\[
f(x) = \left\{
\begin{array}{ll}
  -x, & x < 0 \\
  0,  & x = 0 \\
  x^2, & x > 0
\end{array}
\right.
\]
```

## 8. Matrices

> Require `\usepackage{amsmath}`

| Environment | Delimiter |
|-------------|-----------|
| `matrix` | None |
| `pmatrix` | Parentheses `()` |
| `bmatrix` | Square brackets `[]` |
| `Bmatrix` | Curly braces `{}` |
| `vmatrix` | Single bars `\|` (determinant) |
| `Vmatrix` | Double bars `‖` (norm) |

```latex
% Basic matrix (no delimiters)
\[
\begin{matrix}
  1 & 2 \\
  3 & 4 \\
\end{matrix}
\]

% With parentheses
\[
\begin{pmatrix}
  1 & 0 \\
  0 & 1 \\
\end{pmatrix}
\]

% With square brackets
\[
\begin{bmatrix}
  a & b \\
  c & d \\
\end{bmatrix}
\]

% 3×3 matrix with extra row spacing
\[ A = \begin{bmatrix}
  1 & 2 & 3 \\[6pt]
  4 & 5 & 6 \\[6pt]
  7 & 8 & 9 \\
\end{bmatrix} \]

% Inline small matrix
\( \left( \begin{smallmatrix} a & b \\ c & d \end{smallmatrix} \right) \)
```

## 9. Aligned Equations (amsmath)

```latex
\begin{align}
  x &= a + b \\
  y &= c + d \\
  z &= e + f
\end{align}
% Each & marks the alignment point

% Unnumbered aligned:
\begin{align*}
  2x + 3y &= 10 \\
  x - y   &= 2
\end{align*}
```

## 10. Quick Symbol Reference

```latex
% Arrows:
$\rightarrow$  $\leftarrow$  $\Rightarrow$  $\Leftrightarrow$
$\to$  $\gets$  $\implies$  $\iff$

% Dots:
$\ldots$  % ...  (low dots)
$\cdots$  % ···  (centered dots)
$\vdots$  % vertical dots
$\ddots$  % diagonal dots

% Brackets:
$\left( \frac{a}{b} \right)$   % Auto-sized parentheses
$\left[ x \right]$              % Auto-sized brackets
$\left| x \right|$              % Auto-sized absolute value
```
