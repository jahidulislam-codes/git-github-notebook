# 🚀 Mastering Git & GitHub in 10 Days: From Basics to Advanced Workflows

Welcome to the ultimate **Git & GitHub Master Reference Guide**. Whether you are a total beginner making your first commit or an experienced developer looking to recover from a complex merge conflict, this repository is designed as both a step-by-step learning course and an instant emergency lookup manual.

---

## 📑 Table of Contents

- [🧠 Core Mental Model](#-day-01-basics-intro)
- [📁 Repository Architecture & Roadmap]()
- [⚙️ Initial Setup & Configuration]()
- [🔁 Daily Core Workflow]()
- [🌿 Branching & Merging Strategies]()
- [🚨 Emergency Undo & Recovery Guide]()
- [🤝 GitHub & Collaboration Workflows]()
- [🛠️ Power Tools & Advanced Techniques]()
- [💡 Common Pitfalls & Troubleshooting]()

---

## 🧠 Core Mental Model

Before running commands, it is critical to understand **where** your code lives in Git's architectural pipeline. Every file in a project moves through four primary areas:

```
+------------------+         git add          +------------------+
|                  | -----------------------> |                  |
| Working Directory|                          |   Staging Area   |
| (Modified Files) | <----------------------- |     (Index)      |
+------------------+       git restore        +------------------+
         |                                             |
         |                                             | git commit
         |                                             v
+------------------+         git push         +------------------+
|  Remote Repos    | <----------------------- | Local Repository |
| (GitHub/GitLab)  | -----------------------> |     (.git/)      |
+------------------+         git fetch        +------------------+
```

### The 4 File States in Git:

1. **Untracked:** Files that Git is not watching yet (newly created).
2. **Modified:** Files with changes in your working directory that are not yet staged.
3. **Staged:** Changes marked for inclusion in your next commit snapshot.
4. **Committed:** Permanently saved snapshots inside the local `.git` history database.

---

## 📁 Repository Architecture & Roadmap

This repository is structured into modular sections. Browse the deep-dive guides linked below for comprehensive tutorials on each topic:

```

```

---

## ⚙️ Initial Setup & Configuration

Configure Git globally on your system before working on projects:

### Set User Identity

```bash
# Set your name and email globally (recorded in every commit)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Essential Quality-of-Life Configurations

```bash
# Set default main branch name
git config --global init.defaultBranch main

# Set default text editor (VS Code)
git config --global core.editor "code --wait"

# Enable auto-coloring of CLI outputs
git config --global color.ui auto

# Configure line endings (Windows: true | macOS/Linux: input)
git config --global core.autocrlf input

# Verify current configuration settings
git config --list --show-origin
```

### SSH Key Setup for GitHub

```bash
# 1. Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# 2. Start SSH agent & add key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# 3. Print key (Copy and paste this into GitHub Settings -> SSH and GPG keys)
cat ~/.ssh/id_ed25519.pub

# 4. Test SSH connection
ssh -T git@github.com
```

---

## 🔁 Daily Core Workflow

The basic cycle for 90% of daily Git interactions:

```bash
# 1. Create a new local repository (or clone existing)
git init

# 2. Check current status of working directory & staging area
git status

# 3. Stage changes
git add index.html               # Stage specific file
git add .                        # Stage all modified and untracked files
git add -p                       # Interactively stage chunks/hunks of code

# 4. Commit staged changes with a descriptive message
git commit -m "feat: add user authentication form"

# 5. Connect local repo to GitHub (first time only)
git remote add origin git@github.com:username/repository-name.git
git branch -M main

# 6. Push changes to GitHub
git push -u origin main          # -u sets tracking branch for future 'git push'

# 7. Pull latest changes from remote
git pull origin main             # Fetches and merges remote changes
```

---

## 🌿 Branching & Merging Strategies

Branching allows you to isolate development work without affecting main production code.

### Branch Management

```bash
# List branches
git branch                       # List local branches
git branch -a                    # List local and remote branches

# Create and Switch
git branch feature/login         # Create branch
git checkout feature/login       # Switch to branch
git checkout -b feature/login    # Shortcut: Create and switch instantly
git switch -c feature/login      # Modern alternative to checkout -b

# Delete Branch
git branch -d feature/login      # Safe delete (fails if unmerged)
git branch -D feature/login      # Force delete
```

### Merging vs. Rebasing

- **Merging (`git merge <branch>`):** Preserves complete commit history including merge nodes.
- **Rebasing (`git rebase <branch>`):** Reapplies commits on top of another branch for a clean, linear history.

```bash
# Standard Merge (from main branch)
git checkout main
git merge feature/login

# Interactive Rebase (clean up last 3 commits before merging)
git rebase -i HEAD~3
```

---

## 🚨 Emergency Undo & Recovery Guide

When things go wrong, use this quick reference matrix:

| Problem / Intent                                        | Command                                   | Risk Level                   |
| :------------------------------------------------------ | :---------------------------------------- | :--------------------------- |
| Discard uncommitted changes in a file                   | `git restore <file>`                      | ⚠️ High (Permanent loss)     |
| Move file out of staging area back to working directory | `git restore --staged <file>`             | 🟢 Safe                      |
| Change message of the most recent commit                | `git commit --amend -m "Updated message"` | 🟡 Medium (Rewrites history) |
| Undo last commit, **keep changes in staging**           | `git reset --soft HEAD~1`                 | 🟢 Safe                      |
| Undo last commit, **keep changes in working tree**      | `git reset --mixed HEAD~1`                | 🟢 Safe                      |
| Undo last commit, **PERMANENTLY DELETE changes**        | `git reset --hard HEAD~1`                 | 🚨 Critical (Destructive)    |
| Undo a public/pushed commit safely                      | `git revert <commit-hash>`                | 🟢 Safe (Creates new commit) |
| Recover lost commits or deleted branches                | `git reflog` then `git checkout <hash>`   | 🟢 Safe                      |

### Emergency Recovery with `git reflog`

`git reflog` tracks every movement of `HEAD` in your local repository. Even if you run `git reset --hard` or delete a branch, your work is stored here for up to 90 days.

```bash
# 1. Inspect recent activity history
git reflog

# 2. Locate the SHA commit hash right before the mistake occurred (e.g., e4f2a1b)
# 3. Restore your branch to that exact state:
git reset --hard e4f2a1b
```

---

## 🤝 GitHub & Collaboration Workflows

### Standard Feature-Branch / Pull Request Workflow

1. **Fork** the target repository on GitHub (for open source) or **Clone** directly (for team repos).
2. Create a topic branch (`git checkout -b feature/amazing-feature`).
3. Make atomic commits with clear messages.
4. Push branch to GitHub (`git push origin feature/amazing-feature`).
5. Open a **Pull Request (PR)** on GitHub targeting the main repo's `main` branch.
6. Address code review feedback with additional commits.
7. **Squash and Merge** PR after approvals and automated checks pass.

### Syncing a Forked Repository

```bash
# Add upstream repository reference
git remote add upstream https://github.com/original-owner/repo.git

# Fetch upstream changes
git fetch upstream

# Merge into your local main branch
git checkout main
git merge upstream/main

# Push updated main branch to your GitHub fork
git push origin main
```

---

## 🛠️ Power Tools & Advanced Techniques

### 1. Stash (Temporary Shelf)

Save uncommitted work without committing so you can switch contexts quickly:

```bash
git stash save "WIP: login page formatting" # Save current uncommitted changes
git stash list                             # View all stashed snapshots
git stash apply                            # Apply latest stash (keeps in stash list)
git stash pop                              # Apply latest stash and remove from list
git stash drop                             # Delete latest stash
```

### 2. Cherry-Picking

Pick a specific commit from another branch and apply it to your current branch:

```bash
git cherry-pick <commit-hash>
```

### 3. Git Bisect (Debugging / Finding Bug-introducing Commit)

Uses binary search to isolate the exact commit that introduced a bug:

```bash
git bisect start
git bisect bad                 # Current HEAD is broken
git bisect good v1.0.0         # Version 1.0.0 was known to be working
# Git checks out intermediate commits for testing...
git bisect good                # (or git bisect bad)
git bisect reset               # End bisecting once identified
```

---

## 💡 Common Pitfalls & Troubleshooting

### 1. Accidentally Committed Large / Sensitive Files

If you committed a secret key or file larger than 100MB:

```bash
# Remove from Git tracking without deleting local file
git rm --cached sensitive_config.env

# Add to .gitignore
echo "sensitive_config.env" >> .gitignore

# Commit the removal
git commit -m "fix: untrack sensitive configuration file"
```

### 2. "Fatal: Refusing to merge unrelated histories"

Occurs when trying to pull from a remote repo that was initialized independently:

```bash
git pull origin main --allow-unrelated-histories
```

### 3. How to Writing Great Commit Messages

Follow standard **Conventional Commits**:

- `feat:` A new feature for the user
- `fix:` A bug fix
- `docs:` Documentation-only changes
- `style:` Formatting, missing semi-colons, no production code change
- `refactor:` Code change that neither fixes a bug nor adds a feature
- `test:` Adding missing tests or correcting existing tests
- `chore:` Updating build tasks, package manager configs, etc.

---

## 📜 License

This guide is released under the [MIT License](LICENSE). Feel free to clone, fork, modify, and distribute!
