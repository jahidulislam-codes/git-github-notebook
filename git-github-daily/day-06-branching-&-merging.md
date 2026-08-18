# Git Documentation: Day 6 - Branching & Merging

## Core Concepts

- **Branch**: An independent line of development. Allows isolated workspace without affecting the main code.
- **Merge**: Combining changes from one branch into another (e.g., merging a feature branch into `main`).

## Key Commands

- **Create a Branch**: `git branch <branch-name>`
- **Switch Branch**: `git checkout <branch-name>` or `git switch <branch-name>`
- **Create & Switch (Combined)**: `git checkout -b <branch-name>`
- **List Branches**: `git branch`
- **Merge Branch**:
  1. `git checkout main`
  2. `git merge <feature-branch-name>`
- **Delete Branch**: `git branch -d <branch-name>`
