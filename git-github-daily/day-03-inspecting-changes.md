# Day 03 — Inspecting and Restoring Changes

## `git status`

```bash
git status
```

Shows the current state of the working directory and staging area.

It can show:

- Current branch
- Untracked files
- Modified files
- Staged files
- Whether there are changes to commit

## `git diff`

```bash
git diff
```

Shows unstaged changes in the working directory.

Use it to review changes before staging them.

## `git diff --staged`

```bash
git diff --staged
```

Shows changes currently staged for the next commit.

`git diff --cached` is an alternative form.

## `git log`

```bash
git log
```

Shows the commit history.

## `git log --oneline`

```bash
git log --oneline
```

Shows commit history in a compact format.

## Commit Hash

Every Git commit has a unique hash that identifies the commit.

Example:

```text
a82f31c
```

The short hash is commonly used when referring to a commit.

## `git show`

```bash
git show <commit>
```

Shows detailed information and changes for a specific commit.

Example:

```bash
git show HEAD
```

Shows the current `HEAD` commit and its changes.

## `git restore`

```bash
git restore <file>
```

Discards unstaged changes in a file and restores it to the state of the last commit.

Be careful: discarded uncommitted changes may be lost.

## `git restore --staged`

```bash
git restore --staged <file>
```

Removes a file from the staging area without discarding its working-directory changes.

## Important Difference

```text
git diff
    → Unstaged changes

git diff --staged

    → Staged changes

git restore <file>
    → Discard unstaged changes

git restore --staged <file>
    → Unstage changes
```

## Recommended Commit Workflow

```bash
git status
git diff
git add <file>
git diff --staged
git commit -m "Meaningful message"
git log --oneline
```

## Key Takeaways

1. `git status` tells you what is happening in the repository.
2. `git diff` helps review unstaged changes.
3. `git diff --staged` reviews changes prepared for commit.
4. `git log` displays project history.
5. Every commit has a unique hash.
6. `git show` displays the details of a commit.
7. `git restore` can discard unstaged changes.
8. `git restore --staged` removes changes from the staging area without discarding them.
9. Reviewing changes before committing is an important professional Git habit.
