# Git Documentation: Day 7 - Merge Conflicts & Stashing

## Core Concepts

- **Merge Conflict**: Occurs when Git cannot automatically reconcile differences in code between two merging commits.
- **Git Stash**: Temporarily shelves (or stashes) changes made to your working directory so you can work on something else.

## Resolving Merge Conflicts

1. Identify files with conflict flags (`git status`).
2. Open files and manually edit content between `<<<<<<<`, `=======`, and `>>>>>>>`.
3. Save changes, stage, and commit:
   git add <file>
   git commit -m "Resolved merge conflict"

## Stash Commands

- **Save temporary changes**: `git stash`
- **View stashed changes**: `git stash list`
- **Apply and remove latest stash**: `git stash pop`
- **Apply stash without removing**: `git stash apply`
- **Discard specific stash**: `git stash drop`
