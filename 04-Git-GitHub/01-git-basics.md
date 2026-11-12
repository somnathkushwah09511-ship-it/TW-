# Git Basics — Version Control Concepts & Commands

## 1. What is Version Control?

> **Definition**: A system that records changes to files over time so previous versions can be inspected, compared, and recovered.

### Key Capabilities
- Track modifications to files
- Identify **who** made a change and **when**
- Restore earlier versions
- Support multiple contributors

### Without Version Control (The Problem)
```
project.py
project_final.py
project_final_new.py
project_final_latest.py
project_final_latest_fixed.py    ← Which is correct?
```

---

## 2. Types of Version Control Systems

| Type | Description | Example |
|------|-------------|---------|
| **Local VCS** | Versions on one computer | RCS |
| **Centralized VCS** | Central server stores history | Subversion (SVN) |
| **Distributed VCS** | Each clone has full history | **Git** ✓ |

---

## 3. What is Git?

> **Definition**: Git is a **distributed version control system** used to track changes in files and coordinate development.

### Important Features
- Maintains project history through **commits**
- Supports parallel development using **branches**
- Enables local version control **without a network**
- Supports merging contributions from different branches

---

## 4. Installing & Configuring Git

### Installation
```bash
# Windows: Download from https://git-scm.com/downloads
# Ubuntu/Debian:
sudo apt update && sudo apt install git
# macOS:
brew install git

# Verify:
git --version
```

### Configuration (Do this first!)
```bash
git config --global user.name "Student Name"
git config --global user.email "student@example.com"
git config --global --list     # Verify settings
```

> These values identify **who made the commit** — they don't authenticate you to GitHub.

---

## 5. Git Architecture

```
Working Directory  →  Staging Area  →  Local Repository  →  Remote (GitHub)
  (edit files)         (git add)         (git commit)         (git push)
```

| Area | Description |
|------|-------------|
| **Working Directory** | Files being edited on your computer |
| **Staging Area (Index)** | Selected changes ready for next commit |
| **Local Repository** | Committed history stored in `.git/` folder |
| **Remote Repository** | Shared repo on GitHub/GitLab/etc. |

---

## 6. Creating a Repository

```bash
# Method 1: Initialize new repo
mkdir my-project
cd my-project
git init                     # Creates hidden .git/ folder

# Method 2: Clone existing repo
git clone https://github.com/USERNAME/repo.git
```

> Git stores all metadata in the hidden `.git/` directory.

---

## 7. Basic Git Workflow

```
Edit Files → Stage Changes → Commit → Push to GitHub
```

```bash
# Step 1: See what changed
git status

# Step 2: Stage changes
git add main.py              # Stage specific file
git add .                    # Stage ALL changes
git add *.py                 # Stage all Python files
git add file1.py file2.py    # Stage multiple specific files

# Step 3: Commit staged changes
git commit -m "Add input validation"

# Step 4: Push to remote
git push
```

---

## 8. Understanding Commits

A commit records:
- A **unique hash** (identifier)
- **Author** and **timestamp**
- A **commit message**
- Reference to the project snapshot

### Good Commit Messages ✅
```
Add login validation
Fix division by zero error
Update README instructions
Remove unused functions
```

### Bad Commit Messages ❌
```
changes
update
final code
bug fixed
```

> **Best Practice**: Write concise, specific messages that explain *what* and *why*, not just *what*.

---

## 9. Checking Status & History

```bash
# Check current state:
git status               # Shows untracked, modified, staged files

# View history:
git log                  # Full commit history
git log --oneline        # Compact one-line per commit

# Example output of git log --oneline:
# a1b2c3d Add input validation
# d4e5f6a Fix calculation bug
# b7c8d9e Initial project commit

# Compare changes:
git diff                 # Unstaged changes (working dir vs index)
git diff --staged        # Staged changes (index vs last commit)
git diff HEAD            # All changes since last commit

# List tracked files:
git ls-files
```

---

## 10. Staging & Unstaging

```bash
# Stage:
git add file.py

# Unstage (keeps working dir changes):
git restore --staged file.py

# Discard all unstaged changes (DANGEROUS — can't undo):
git restore file.py

# Move/rename tracked file:
git mv old.py new.py

# Remove tracked file:
git rm old.py
```

---

## 11. .gitignore — Excluding Files

Create a file named `.gitignore` in root:

```gitignore
# Python cache:
__pycache__/
*.pyc
*.pyo

# Environment:
.env
venv/

# Logs:
*.log

# Data files:
data/
*.csv

# OS files:
.DS_Store
Thumbs.db

# IDE:
.vscode/
.idea/
```

> ⚠️ Adding a file to `.gitignore` does **NOT** remove it from history if already committed!

---

## 12. Undoing Changes

```bash
# Revert a commit safely (creates a new "undo" commit):
git log --oneline
git revert a1b2c3d        # Reverts that specific commit

# This is SAFE — it doesn't delete history
# Existing commits are preserved
# A new commit records the reversal
```

---

## 13. Complete Local Workflow Example

```bash
# Create project:
mkdir calculator
cd calculator
git init

# Create file:
echo "print(2 + 3)" > main.py

# Check status:
git status                    # Shows main.py as untracked

# Stage:
git add main.py

# Commit:
git commit -m "Add calculator program"

# View history:
git log --oneline
```

---

## 14. Git Best Practices

1. ✅ **Commit frequently** and logically (one feature = one commit)
2. ✅ **Write clear commit messages**
3. ✅ **Review changes** before committing (`git diff`)
4. ✅ **Never commit** passwords, API keys, or tokens
5. ✅ **Use `.gitignore`** for generated files and secrets
6. ✅ **Pull/fetch** updates regularly
7. ✅ **Test** changes before committing
8. ✅ **Document** projects with a README

---

## 15. Common Errors & Solutions

| Problem | Possible Solution |
|---------|------------------|
| Untracked files | `git add` the required files |
| Push rejected | `git pull` first, then push |
| Merge conflict | Edit conflicting files, then `git add` + `git commit` |
| Wrong branch | Check with `git branch` |
| Nothing to commit | Check `git status` and staged files |
| Authentication failed | Check credentials and permissions |

> **Diagnostic command**: `git status` — always start here!
