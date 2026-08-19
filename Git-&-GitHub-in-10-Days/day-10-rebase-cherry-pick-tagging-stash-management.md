# Git Documentation: Day 10 - Advanced Concepts

## Core Concepts

- **Rebase**: Reapplies commits on top of another base tip to create a clean, linear commit history.
- **Cherry-pick**: Applies the changes introduced by specific existing commits into the current working branch.
- **Tagging**: Creates named pointers to specific commits in history, typically used to mark release points (e.g., v1.0).

## Advanced Commands

- **Rebase Branch**: `git rebase main`
- **Cherry-pick Commit**: `git cherry-pick <commit-hash>`
- **Create Tag**: `git tag -a <tag-name> -m "<message>"`
- **Push Tag to Remote**: `git push origin <tag-name>`
- **List All Tags**: `git tag`
