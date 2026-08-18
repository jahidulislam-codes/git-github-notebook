# Day 05 — Amend, Reset, Revert and Clean

## `git commit --amend`

```bash
git commit --amend -m "New commit message"
```

Modifies the latest commit instead of creating a separate new commit.

Useful for correcting the latest commit message or adding forgotten staged changes.

```bash
git commit --amend --no-edit
```

Adds staged changes to the latest commit while keeping the existing commit message.

Avoid amending commits that have already been shared unless you understand the consequences of rewriting history.

## `git reset`

`git reset` moves the current branch/HEAD to another commit and can also affect the staging area and working tree depending on the mode.

### Soft Reset

```bash
git reset --soft HEAD~1
```

Moves HEAD back while keeping the changes staged.

### Mixed Reset

```bash
git reset --mixed HEAD~1
```

Moves HEAD back and keeps the changes in the working directory as unstaged changes.

`--mixed` is the default reset mode.

### Hard Reset

```bash
git reset --hard HEAD~1
```

Moves HEAD back and discards corresponding working-tree and staging changes.

Use with extreme caution.

## `HEAD~n`

```text
HEAD~1 → one commit before HEAD
HEAD~2 → two commits before HEAD
HEAD~3 → three commits before HEAD
```

## `git revert`

```bash
git revert <commit-hash>
```

Creates a new commit that reverses the changes introduced by an earlier commit.

The original commit remains in history.

This is generally safer than rewriting shared history.

## Reset vs Revert

```text
reset
→ Moves history backward.

revert
→ Creates a new commit that undoes an earlier commit.
```

For shared/public history, prefer a non-history-rewriting approach such as `git revert` when appropriate.

## `git clean`

Preview untracked files that could be removed:

```bash
git clean -n
```

Remove untracked files:

```bash
git clean -f
```

Remove untracked files and directories:

```bash
git clean -fd
```

Be careful because `git clean` permanently removes files from the working tree.

## Important Safety Rule

Always inspect destructive commands before executing them.

For example:

```bash
git clean -n
```

before:

```bash
git clean -f
```

## Command Selection

```text
Wrong latest commit/message
        ↓
git commit --amend

Need to rewrite local history
        ↓
git reset

Need to undo an existing shared commit
        ↓
git revert

Need to remove untracked files
        ↓
git clean
```

## Key Takeaways

1. `git commit --amend` modifies the latest commit.
2. `git reset --soft` keeps changes staged.
3. `git reset --mixed` keeps changes but unstages them.
4. `git reset --hard` can discard local changes and should be used carefully.
5. `git revert` creates a new commit that reverses an earlier commit.
6. Reset rewrites the current history position; revert preserves the original commit.
7. `git clean -n` previews files that would be removed.
8. `git clean -f` removes untracked files.
9. Avoid rewriting history that has already been shared unless you understand the consequences.
10. Always inspect destructive operations before running them.
