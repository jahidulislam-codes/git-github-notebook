# Day 01 — Git Basics

## What is Git?

Git is a distributed version control system used to track changes in files and manage the history of a project.

## What is Version Control?

Version control is a system that records changes to files over time so that developers can review history, compare changes, collaborate, and restore previous versions when necessary.

## Git vs GitHub

- **Git** → A version control system that runs locally.
- **GitHub** → A cloud-based platform for hosting Git repositories and collaborating with other developers.

Git and GitHub are related, but they are not the same thing.

## Why Use Git?

Git helps developers:

- Track changes
- Maintain project history
- Create branches
- Merge changes
- Collaborate with other developers
- Recover from mistakes
- Review code
- Work safely on large projects

## Basic Git Commands

```bash
git --version
```

Check the installed Git version.

```bash
git config --global user.name "Your Name"
```

Set the global Git username.

```bash
git config --global user.email "your-email@example.com"
```

Set the global Git email.

```bash
git config --global --list
```

View global Git configuration.

```bash
mkdir notebook
```

Create a new `notebook` directory.

```bash
cd notebook
```

Move into the `notebook` directory.

```bash
git init
```

Initialize the current directory as a Git repository.

```bash
git status
```

Show the current state of the Git repository.

## Important Concept

A Git repository contains a `.git` directory that stores Git's internal repository information, including history and other metadata.

## Mental Model

```text
Git
├── Local version control
├── Tracks changes
├── Creates commits
└── Maintains project history

GitHub
├── Remote repository hosting
├── Collaboration
├── Pull Requests
└── Code sharing
```

## Key Takeaways

1. Git is a version control system.
2. GitHub is a platform for hosting and collaborating on Git repositories.
3. Git works locally on a computer.
4. `git init` initializes a Git repository.
5. `git status` shows the current repository state.
6. Git configuration can be set globally using `--global`.
7. The `.git` directory contains important Git repository data.
