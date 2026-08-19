# Day 02 — Working Directory, Staging Area and Commit

## Git's Core Workflow

```text
Working Directory
        ↓ git add
Staging Area
        ↓ git commit
Git Repository
```

## Working Directory

The Working Directory is the part of the project where files are created and modified.

## Staging Area

The Staging Area contains changes that have been selected for the next commit.

It allows developers to choose exactly which changes should be included in a commit.

## Git Repository

The Git Repository stores committed project history and Git metadata.

## Untracked File

An untracked file is a file inside the repository that Git is not currently tracking.

## `git status`

```bash
git status
```

Shows the current state of the working directory and staging area.

## `git add`

```bash
git add README.md
```

Stages changes from a specific file.

```bash
git add .
```

Stages applicable changes from the current directory.

## `git commit`

```bash
git commit -m "Add README"
```

Creates a new commit from the staged changes.

A commit records a specific state of the project.

## `git log`

```bash
git log
```

Shows the commit history.

## `git log --oneline`

```bash
git log --oneline
```

Shows the commit history in a compact format.

## `git diff`

```bash
git diff
```

Shows differences between the working directory and the last committed state for unstaged changes.

## Important Workflow

```bash
git status
git add <file>
git commit -m "Meaningful message"
git log --oneline
```

## Important Distinction

- `git add` → Stage changes
- `git commit` → Record staged changes
- `git push` → Send local commits to a remote repository

## Good Commit Messages

Good:

Follow standard **Conventional Commits**:

- `feat:` A new feature for the user
- `fix:` A bug fix
- `docs:` Documentation-only changes
- `style:` Formatting, missing semi-colons, no production code change
- `refactor:` Code change that neither fixes a bug nor adds a feature
- `test:` Adding missing tests or correcting existing tests
- `chore:` Updating build tasks, package manager configs, etc.

---

Avoid vague messages such as:

```text
update
changes
fix
test
```

## Key Takeaways

1. The Working Directory is where files are modified.
2. The Staging Area prepares selected changes for a commit.
3. A commit records a snapshot of staged changes.
4. `git status` shows the repository state.
5. `git add` stages changes.
6. `git commit` creates a commit.
7. `git log` displays commit history.
8. `git diff` shows changes that have not been staged.
9. Staging allows developers to create focused commits.
10. `git push` is different from `git commit`; pushing sends local commits to a remote repository.
