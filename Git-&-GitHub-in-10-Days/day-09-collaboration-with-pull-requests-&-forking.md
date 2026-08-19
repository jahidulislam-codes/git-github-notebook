# Git Documentation: Day 9 - Collaboration with PR & Forking

## Core Concepts

- **Fork**: A personal copy of another user's repository stored on your GitHub account.
- **Pull Request (PR)**: A proposal to merge your branch's changes into someone else's main repository.

## Collaboration Workflow

1. **Fork** the original repository on GitHub.
2. **Clone** your forked repository locally:
   `git clone <forked-repo-url>`
3. Create a **feature branch**:
   `git checkout -b <branch-name>`
4. Make changes, **stage**, and **commit**:
   `git commit -m "Add new feature"`
5. **Push** changes to your remote fork:
   `git push origin <branch-name>`
6. Open GitHub and click **"Create Pull Request"** to propose changes.
