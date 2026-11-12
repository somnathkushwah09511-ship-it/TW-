# Git & GitHub — Modern Version Control & Collaboration

> **Mindset**: Git is your local time machine and safety net. GitHub is the cloud collaborative hub where teams share code, review improvements, and ship software together.

---

## ⚡ The 60-Second Daily Routine

```bash
# 1. Pull latest upstream updates
git pull

# 2. Check what you changed
git status
git diff

# 3. Stage & commit with a crisp message
git add .
git commit -m "Add Doxygen documentation & update README"

# 4. Push your commits to GitHub
git push
```

---

## 📚 Study Modules

| Module | What's Covered |
|---|---|
| [01-git-basics.md](./01-git-basics.md) | The 3 areas (Working tree, Staging, Repo), commits, history, and `.gitignore` |
| [02-github.md](./02-github.md) | Remote repositories, SSH/CLI authentication, Issues, and Releases |
| [03-collaboration.md](./03-collaboration.md) | Branching strategy, Pull Requests (PRs), and resolving merge conflicts |

---

## 🎯 High-Yield Command Cheat Sheet

### Setup & Inspection
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git status                # What changed?
git log --oneline -n 5    # Last 5 commits summarized
```

### Branching & Safe Experimentation
```bash
git switch -c feature/login    # Create & switch to feature branch
# ... write code, add, commit ...
git switch main                # Switch back to main
git merge feature/login        # Merge changes into main
git branch -d feature/login    # Clean up local branch
```

### Undoing Mistakes Safely
```bash
git restore <file>             # Discard local unstaged changes
git restore --staged <file>    # Unstage file (keep your edits)
git revert <commit_hash>       # Safely revert a published commit with a new commit
```

---

## 💡 Best Practices
1. **Commit Small & Often**: One logical fix/feature per commit.
2. **Clear Commit Messages**: Use imperative mood (`"Fix calculation bug"` instead of `"fixed stuff"`).
3. **Never Commit Secrets**: Use `.gitignore` for passwords, `.env`, binaries, and build artifacts.
