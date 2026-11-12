# Git Collaboration — Branches, Merging & Pull Requests

## 1. What is a Branch?

> **Definition**: A branch is an independent line of development that allows changes to be made without directly modifying another branch.

```
main ─────●────────────────────●── (stable code)
           \                  /
feature     ●────●────●──────   (isolated development)
```

### Without Branches ❌
- Experimental changes affect main
- Incomplete features mix with stable code
- Reviewing individual changes is harder

### With Branches ✅
- Features develop independently
- Bugs can be fixed separately
- Changes can be reviewed before merging

---

## 2. Branch Commands

```bash
# List local branches (current marked with *):
git branch

# Create a new branch:
git branch feature-login

# Switch to a branch:
git switch feature-login
git switch main              # Return to main

# Create AND switch in one step:
git switch -c feature-login

# Delete a branch (after merging):
git branch -d feature-login

# List all branches (including remote):
git branch -a
```

> 💡 Use descriptive branch names: `feature-login`, `fix-navbar`, `docs-update`

---

## 3. Typical Feature Branch Workflow

```bash
# 1. Start from the base branch:
git switch main
git pull                      # Get latest updates

# 2. Create feature branch:
git switch -c feature-subtraction

# 3. Work on the feature:
# ... edit files ...
git add main.py
git commit -m "Add subtraction feature"
git add test_main.py
git commit -m "Add tests for subtraction"

# 4. Push branch to GitHub:
git push -u origin feature-subtraction
```

---

## 4. Merging Branches

```bash
# Switch to the target branch (branch receiving changes):
git switch main

# Merge the source branch:
git merge feature-login

# If fast-forward merge (linear history):
# No merge commit created

# If merge commit needed (diverged histories):
# Git creates a merge commit automatically
```

> ⚠️ **Important**: The target branch is the one **currently checked out**.

---

## 5. Merge Conflicts

A merge conflict occurs when Git cannot automatically combine competing changes.

### When Conflicts Happen
- Two people edit the **same line** differently
- One person edits a file, another deletes it
- Other incompatible file changes

### Conflict Markers
```
<<<<<<< HEAD
result = 10          ← Your version (current branch)
=======
result = 20          ← Their version (branch being merged)
>>>>>>> feature-login
```

### Resolving a Conflict
```bash
# 1. Open the conflicting file
# 2. Decide which change to keep (or combine both)
# 3. Remove ALL conflict markers (<<<<<<<, =======, >>>>>>>)
# 4. Stage the resolved file:
git add main.py
# 5. Complete the merge:
git commit
```

> 💡 Conflicts are **not an error** — they're just a request for human judgment!

---

## 6. Merge vs Rebase

Both integrate changes, but handle history differently:

### Merge
```bash
git switch main
git merge feature
```
- Combines branch histories
- May create a merge commit
- Preserves all existing commits
- Non-destructive

### Rebase
```bash
git switch feature
git rebase main
```
- Replays commits on a new base
- Creates rewritten commit identities
- Produces **linear history**
- Rewrites history

> ⚠️ **Caution**: Avoid rebasing **shared/published** commits — it rewrites history and can cause problems for others!

---

## 7. What is a Pull Request (PR)?

> A pull request **proposes changes** for review and integration into another branch on GitHub.

### Pull Request Process
1. Push a feature branch to GitHub
2. Open a pull request against the target branch
3. Explain the changes and their purpose
4. Request reviews and run checks (CI/CD)
5. Address reviewer feedback
6. Merge when approved

> 🔑 **Key Point**: A PR is a **review mechanism** on GitHub — not the same as the local `git pull` command!

---

## 8. Forking

> A **fork** is a separate repository copy under your own account.

```
Original Repo (owner)
    ↓
Your Fork (your account) ← git clone → Local copy
    ↓ (after changes)
Pull Request → Original Repo
```

### Fork vs Clone

| Feature | Fork | Clone |
|---------|------|-------|
| Creates | Separate repo on GitHub | Local copy |
| Location | GitHub (remote) | Your computer |
| Purpose | Contribute to others' projects | Work locally |
| Typical use | Open source contribution | Personal/team project |

### Contributing via Fork
```bash
# 1. Fork on GitHub (click Fork button)
# 2. Clone your fork:
git clone https://github.com/YOUR_USERNAME/repo.git
# 3. Add upstream remote:
git remote add upstream https://github.com/ORIGINAL/repo.git
# 4. Create branch, make changes, push
# 5. Open Pull Request from your fork to original
```

---

## 9. Code Review Best Practices

### For Reviewers
- ✅ Check correctness
- ✅ Identify potential bugs
- ✅ Suggest improvements
- ✅ Verify tests and readability

### For Contributors
- ✅ Explain the changes clearly
- ✅ Respond to all feedback
- ✅ Update the branch with fixes
- ✅ Keep PRs **small and focused**

---

## 10. Complete Developer Workflow

```
Create Branch → Commit Changes → Push → Open PR → Review → Merge
```

```bash
# Full example:
git switch -c feature-subtraction
# ... edit files ...
git add .
git commit -m "Add subtraction feature"
git push -u origin feature-subtraction

# On GitHub: Open PR → Review → Merge

# After merge, clean up:
git switch main
git pull origin main
git branch -d feature-subtraction
```

---

## 11. Collaborative GitHub Workflow Summary

```
Edit → Stage → Commit → Push Branch → Open PR → Review → Merge
```

```bash
# --- EDIT PHASE ---
# Edit files in your IDE

# --- STAGE PHASE ---
git status
git diff
git add .

# --- COMMIT PHASE ---
git commit -m "Descriptive message"
git log --oneline

# --- PUSH PHASE ---
git push -u origin feature-name

# --- PR PHASE (on GitHub) ---
# Create PR, add description, request reviewers

# --- MERGE PHASE (after approval) ---
# Merge on GitHub, then locally:
git switch main
git pull origin main
```

---

## 12. Mini Project: Version-Controlled Calculator

```bash
# Step 1: Initialize
mkdir calculator && cd calculator
git init

# Step 2: Create file and first commit
echo 'print("Calculator")' > main.py
echo 'a, b = 10, 5'       >> main.py
echo 'print("Sum:", a+b)'  >> main.py
git status
git add main.py
git commit -m "Add initial calculator"
git log --oneline

# Step 3: Publish to GitHub
git branch -M main
git remote add origin https://github.com/USERNAME/calculator.git
git push -u origin main

# Step 4: Feature branch
git switch -c feature-subtraction
echo 'print("Difference:", a-b)' >> main.py
git add main.py
git commit -m "Add subtraction feature"
git push -u origin feature-subtraction

# Step 5: Create PR on GitHub
# → Open PR, review, merge

# Step 6: Pull merged changes locally
git switch main
git pull origin main
```
