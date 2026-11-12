# GitHub — Remote Repositories & Collaboration Platform

## 1. What is GitHub?

> **Definition**: GitHub is an **online platform** for hosting Git repositories and collaborating on software projects.

### Git vs GitHub

| Feature | Git | GitHub |
|---------|-----|--------|
| Type | Version control system | Hosting + collaboration platform |
| Main purpose | Track file changes | Share and collaborate on projects |
| Location | Runs locally | Provides remote hosting |
| History | Maintains commits | Displays repository history |
| Collaboration | Branches and merges | Pull requests, reviews, Issues |
| Network | Works offline | Online features require connection |

> 🔑 **Remember**: Git is the tool; GitHub is the platform hosting Git repositories.

---

## 2. Creating a GitHub Account

1. Visit [https://github.com/](https://github.com/)
2. Create account with email
3. Verify email
4. Enable **two-factor authentication** (security best practice)
5. Sign in and open profile

> 🔐 **Security Tip**: Never share passwords, personal access tokens, or private SSH keys!

---

## 3. GitHub Repository Interface

A GitHub repository page provides:
- **Code** — Project files and directories
- **Issues** — Bug reports and task discussions
- **Pull Requests** — Proposed changes and reviews
- **Actions** — Automated workflows and testing (CI/CD)
- **Settings** — Repository permissions and configuration
- **Insights** — Traffic, contributors, commits graph

---

## 4. Creating a GitHub Repository

1. Sign in to GitHub
2. Click **New repository** (+ icon or Repositories tab)
3. Enter repository name (e.g., `calculator`)
4. Choose **Public** or **Private**
5. Optionally add README and `.gitignore`
6. Click **Create repository**

| Visibility | Description |
|-----------|-------------|
| **Public** | Anyone can view the repository |
| **Private** | Access limited to authorized users |

---

## 5. README File

```markdown
# Calculator

A simple Python calculator.

## Features
- Addition
- Subtraction
- Multiplication
- Division

## Installation
```bash
git clone https://github.com/USERNAME/calculator.git
cd calculator
```

## Usage
```bash
python main.py
```

## Contributors
- Jane Doe
```

> A good README includes: purpose, features, installation, usage, contributors, license.

---

## 6. Connecting Local Repo to GitHub

```bash
# Step 1: Add remote (GitHub repo URL)
git remote add origin https://github.com/USERNAME/calculator.git

# Step 2: Rename branch to main (if needed)
git branch -M main

# Step 3: Push and set upstream
git push -u origin main

# Check configured remotes:
git remote -v
# Output:
# origin  https://github.com/USERNAME/calculator.git (fetch)
# origin  https://github.com/USERNAME/calculator.git (push)
```

> Replace `USERNAME` with your actual GitHub username.

---

## 7. Complete GitHub Workflow

```bash
# 1. Initialize local repo:
git init
git add .
git commit -m "Initial commit"

# 2. Create repo on GitHub (via browser)

# 3. Connect and push:
git branch -M main
git remote add origin https://github.com/USERNAME/repo.git
git push -u origin main
```

---

## 8. Cloning a Repository

```bash
# Clone creates local copy with full Git history:
git clone https://github.com/USERNAME/calculator.git

# After cloning:
# - Files are downloaded
# - Local repo is created
# - Remote 'origin' is configured
# - Local references to remote branches are set up
```

---

## 9. Fetching & Pulling Updates

```bash
# Fetch (download without merging):
git fetch origin
# Shows remote updates but doesn't change local branch

# Pull (fetch + merge/rebase):
git pull
# Downloads and integrates changes into current branch

# Difference:
# fetch = look at changes
# pull  = look + apply changes
```

---

## 10. Git Tags & Releases

```bash
# List tags:
git tag

# Create annotated tag:
git tag -a v1.0.0 -m "Version 1.0.0"

# View tag details:
git show v1.0.0

# Push tag to GitHub:
git push origin v1.0.0

# Push all tags:
git push origin --tags
```

> **Semantic Versioning**: `MAJOR.MINOR.PATCH`
> - MAJOR: Breaking changes
> - MINOR: New features (backward compatible)
> - PATCH: Bug fixes

GitHub Releases can attach release notes and downloadable files to version tags.

---

## 11. GitHub Issues

Track bugs, features, and tasks:

```
Example Issue:
Title: Calculator crashes for zero division
Description: Handle division by zero and display an appropriate error message.
Labels: bug, priority-high
Assignee: @username
```

**Common Uses**:
- 🐛 Report a software bug
- 💡 Suggest a new feature
- 📋 Assign tasks to contributors
- 💬 Discuss requirements and solutions

---

## 12. GitHub Projects

Organize work with Kanban-style boards:

| Status | Example Task |
|--------|-------------|
| **Todo** | Design calculator interface |
| **In Progress** | Implement division operation |
| **In Review** | Review input validation |
| **Done** | Write project README |

- Track progress across tasks
- Link tasks to Issues and pull requests
- Table or board view

---

## 13. Authentication

### HTTPS Authentication
- Use **Personal Access Token** (PAT) instead of password
- Generate: GitHub Settings → Developer Settings → Personal Access Tokens

### SSH Authentication
```bash
# Generate SSH key:
ssh-keygen -t ed25519 -C "your@email.com"

# Add to SSH agent:
ssh-add ~/.ssh/id_ed25519

# Copy public key (add to GitHub Settings → SSH keys):
cat ~/.ssh/id_ed25519.pub

# Test connection:
ssh -T git@github.com
```

---

## 14. Security Best Practices

- ❌ Never commit passwords, API keys, tokens
- ❌ Never share private SSH keys
- ✅ Use `.gitignore` for sensitive config files
- ✅ Review repository visibility and permissions
- ✅ Enable 2FA on GitHub account

> ⚠️ Adding secrets to `.gitignore` does NOT remove them from Git history if already committed!
