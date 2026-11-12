# Doxygen — Automated Code Documentation

> **Key Idea**: Write formatted comments directly alongside your functions, classes, and structs. Doxygen automatically extracts them into an interactive HTML documentation site or printable PDF manual.

---

## 1. Quick Installation & 4-Step Workflow

### Installation
- **Windows**: Download installer from [doxygen.nl/download.html](https://www.doxygen.nl/download.html)
- **Linux**: `sudo apt install doxygen graphviz`
- **macOS**: `brew install doxygen graphviz`

### Standard 4-Step Pipeline
```bash
# Step 1: Write Doxygen comments in your source code (.cpp, .py, .h, .java)

# Step 2: Generate default configuration template
doxygen -g Doxyfile

# Step 3: Run Doxygen engine
doxygen Doxyfile

# Step 4: Open and browse documentation
# Open html/index.html in your browser!
```

---

## 2. Comment Syntax & Common Tags

### C / C++ / Java Syntax (`/** ... */`)
```cpp
/**
 * \brief Computes the Euclidean distance between two points.
 *
 * Detailed explanation: calculates sqrt((x2-x1)^2 + (y2-y1)^2).
 * 
 * \param x1 Starting X coordinate.
 * \param y1 Starting Y coordinate.
 * \param x2 Target X coordinate.
 * \param y2 Target Y coordinate.
 * \return Floating point distance value.
 * \note Returns 0.0 if both points coincide.
 * \see manhattanDistance()
 */
double euclideanDistance(double x1, double y1, double x2, double y2);
```

### Documenting Classes (C++)
```cpp
/**
 * \class RobotController
 * \brief Manages motor hardware and path navigation.
 * \author Neeta Nain
 * \version 1.2
 */
class RobotController {
public:
    /**
     * \brief Initializes motor pins.
     * \return true if motors respond, false otherwise.
     */
    bool initialize();
};
```

### Python Syntax (Docstrings)
```python
def calculate_grade(marks):
    """
    Brief description: Maps numeric marks to letter grades.

    Detailed explanation: Applies MNIT relative grading scheme.
    
    :param marks: Total numeric marks obtained.
    :type marks: float
    :return: Letter grade string (e.g., 'A', 'B+').
    :rtype: str
    """
    if marks >= 90:
        return 'A'
    return 'B'
```

---

## 3. Most Essential Doxygen Tags Cheat Sheet

| Tag | Purpose | Example |
|---|---|---|
| `\brief` | One-sentence summary | `\brief Checks user validity.` |
| `\param` | Documents an input parameter | `\param id Unique student ID.` |
| `\return` | Documents return value | `\return Status code (0 on success).` |
| `\author` | Identifies author | `\author Dr. Neeta Nain` |
| `\version` | Semantic version indicator | `\version 2.0.1` |
| `\see` | Creates hyperlinked reference | `\see validateEmail()` |
| `\note` | Highlights important caveat | `\note Thread-safe function.` |
| `\warning` | Critical danger warning | `\warning Overwrites existing files.` |

---

## 4. Key Configuration in `Doxyfile`

Edit your `Doxyfile` to control documentation outputs:

```ini
PROJECT_NAME           = "My Project"
PROJECT_NUMBER         = "1.0"
OUTPUT_DIRECTORY       = "docs"

# Output formats
GENERATE_HTML          = YES     # Creates interactive HTML browser
GENERATE_LATEX         = YES     # Generates LaTeX sources (can compile to PDF)
GENERATE_RTF           = NO
GENERATE_XML           = NO

# Visual Diagrams (Requires Graphviz dot installed)
HAVE_DOT               = YES     # Set to YES for inheritance & call graphs
CALL_GRAPH             = YES     # Visual function call hierarchy
CALLER_GRAPH           = YES
```

---

## 5. Best Practices for Developers

1. **Document the "Contract"**: State clearly what input is assumed, what output is guaranteed, and any edge-case exceptions.
2. **Keep `Doxyfile` in Git**: Store `Doxyfile` alongside code so any developer (or CI/CD runner) can regenerate identical docs.
3. **Automate with CI/CD**: Hook `doxygen Doxyfile` into GitHub Actions to deploy updated docs to **GitHub Pages** on every push.
