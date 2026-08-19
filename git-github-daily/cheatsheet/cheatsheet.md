# Git & GitHub Complete Reference Manual

A comprehensive step-by-step documentation containing all essential Git and GitHub commands.

---

## 1. System Setup & Configuration

Configure identity and global options before creating repositories.

| Command                                                   | Description                                            |
| :-------------------------------------------------------- | :----------------------------------------------------- |
| `git config --global user.name "Your Name"`               | Set global author name for all commits                 |
| `git config --global user.email "your.email@example.com"` | Set global email address for all commits               |
| `git config --global init.defaultBranch main`             | Set default branch name to `main` for new repositories |
| `git config --global core.editor "code --wait"`           | Set Visual Studio Code as default editor               |
| `git config --global core.autocrlf true`                  | Handle line endings automatically (Windows)            |
| `git config --global core.autocrlf input`                 | Handle line endings automatically (macOS/Linux)        |
| `git config --list`                                       | Display all configured Git global/local settings       |
| `git config user.name`                                    | Display current configured user name                   |
| `git config user.email`                                   | Display current configured user email                  |

---

## 2. Repository Initialization & Cloning

Set up local projects or retrieve remote repositories.

| Command                                       | Description                                                 |
| :-------------------------------------------- | :---------------------------------------------------------- |
| `git init`                                    | Initialize a new local Git repository in current folder     |
| `git init <folder-name>`                      | Create a new directory and initialize Git inside it         |
| `git clone <repository-url>`                  | Clone a remote GitHub repository to local machine           |
| `git clone <repository-url> <directory-name>` | Clone a repository into a custom named directory            |
| `git clone --branch <branch-name> <url>`      | Clone a specific branch from a remote repository            |
| `git clone --depth 1 <url>`                   | Perform a shallow clone with only the latest commit history |

---

## 3. File Tracking & Committing

Track modifications, stage files, and record version snapshots.

| Command                               | Description                                                            |
| :------------------------------------ | :--------------------------------------------------------------------- |
| `git status`                          | Show current working tree and staging area status                      |
| `git status -s`                       | Show status in compact short format                                    |
| `git add <filename>`                  | Stage a specific file for the next commit                              |
| `git add <file1> <file2>`             | Stage multiple specific files                                          |
| `git add .`                           | Stage all modified and new untracked files                             |
| `git add -A`                          | Stage all changes including deleted files across repository            |
| `git add -p`                          | Interactively select specific hunks of changes to stage                |
| `git commit -m "Commit message"`      | Record staged changes into commit history                              |
| `git commit -am "Commit message"`     | Stage all tracked modified files and commit in one step                |
| `git commit --amend -m "New message"` | Modify the last commit message without creating a new commit           |
| `git commit --amend --no-edit`        | Add newly staged files to the previous commit without changing message |

---

## 4. History, Logs & Diffs

Examine commit history, differences, and specific changes.

| Command                           | Description                                                      |
| :-------------------------------- | :--------------------------------------------------------------- |
| `git log`                         | Show full chronological commit history                           |
| `git log --oneline`               | Display commit history in single line format                     |
| `git log -n 5`                    | Show details for the last 5 commits                              |
| `git log --graph --oneline --all` | Draw ASCII graph showing branch structure and commits            |
| `git log --author="Name"`         | Filter commit logs by specific author                            |
| `git log --grep="keyword"`        | Search commit messages containing specific keywords              |
| `git log -p`                      | Display patch changes (diffs) introduced in each commit          |
| `git diff`                        | Show unstaged changes between working directory and staging area |
| `git diff --staged`               | Show staged changes relative to the last commit                  |
| `git diff <branch1> <branch2>`    | Show line differences between two branches                       |
| `git show <commit-hash>`          | Display commit metadata and detailed patch output                |
| `git blam <filename>`             | Show line-by-line commit history and author attribution          |

---

## 5. Ignoring Unwanted Files (`.gitignore`)

Examine `.gitignore` rules to prevent tracking unnecessary files.

```gitignore
# Ignore node_modules directory
node_modules/

# Ignore log files
*.log

# Ignore environment file
.env

# Ignore build output folder
dist/
build/

# Do not ignore a specific file inside ignored directory
!important.log
```

| Command                          | Description                                         |
| :------------------------------- | :-------------------------------------------------- |
| `git check-ignore -v <filename>` | Check which rule in `.gitignore` is ignoring a file |

---

## 6. Undoing Changes & Commit Restoration

Revert modifications, reset commits, or clean working environment.

| Command                           | Description                                                |
| :-------------------------------- | :--------------------------------------------------------- |
| `git restore <filename>`          | Discard uncommitted changes in working directory           |
| `git restore .`                   | Discard all local uncommitted changes in current directory |
| `git restore --staged <filename>` | Remove file from staging area back to working directory    |
| `git reset HEAD <filename>`       | Unstage file (legacy alternative to restore)               |
| `git reset --soft HEAD~1`         | Undo last commit but keep changes staged                   |
| `git reset --mixed HEAD~1`        | Undo last commit and unstage changes                       |
| `git reset --hard HEAD~1`         | Completely discard last commit and all modifications       |
| `git revert <commit-hash>`        | Create a new commit that safely undoes specified commit    |
| `git clean -n`                    | Show dry-run of untracked files to be removed              |
| `git clean -fd`                   | Force removal of all untracked files and directories       |

---

## 7. Branching & Merging

Manage isolated development lines and integrate code changes.

| Command                               | Description                                                |
| :------------------------------------ | :--------------------------------------------------------- |
| `git branch`                          | List all local branches (highlights current active branch) |
| `git branch -r`                       | List all remote tracking branches                          |
| `git branch -a`                       | List all local and remote branches                         |
| `git branch <branch-name>`            | Create a new local branch                                  |
| `git checkout <branch-name>`          | Switch working directory to specified branch               |
| `git switch <branch-name>`            | Modern command to switch branches                          |
| `git checkout -b <branch-name>`       | Create a new branch and switch to it immediately           |
| `git switch -c <branch-name>`         | Modern syntax to create and switch branch                  |
| `git merge <branch-name>`             | Merge specified branch changes into active branch          |
| `git merge --no-ff <branch-name>`     | Merge branch and force creation of a merge commit          |
| `git branch -d <branch-name>`         | Delete a merged local branch                               |
| `git branch -D <branch-name>`         | Force delete an unmerged local branch                      |
| `git branch -m <old-name> <new-name>` | Rename current local branch                                |

---

## 8. Stashing (Temporary Work Storage)

Save working directory state without committing unfinished code.

| Command                             | Description                                       |
| :---------------------------------- | :------------------------------------------------ |
| `git stash`                         | Save modified tracked files to stash stack        |
| `git stash -u`                      | Stash modified and untracked files                |
| `git stash save "work description"` | Save stash with a custom identification label     |
| `git stash list`                    | Display list of all stored stash entries          |
| `git stash pop`                     | Apply latest stash and remove it from stash list  |
| `git stash apply`                   | Apply latest stash while keeping it in stash list |
| `git stash apply stash@{1}`         | Apply specific stash entry                        |
| `git stash drop stash@{0}`          | Delete specific stash entry                       |
| `git stash clear`                   | Delete all stash entries permanently              |

---

## 9. Remote Repositories & GitHub Operations

Link local projects to GitHub, push commits, and pull updates.

| Command                                  | Description                                                       |
| :--------------------------------------- | :---------------------------------------------------------------- |
| `git remote add origin <url>`            | Link local repository to remote GitHub URL as `origin`            |
| `git remote -v`                          | View list of configured remote repository URLs                    |
| `git remote set-url origin <new-url>`    | Update URL for existing remote origin                             |
| `git remote rename <old> <new>`          | Rename remote server alias                                        |
| `git remote remove origin`               | Disconnect remote server connection                               |
| `git push -u origin main`                | Push commits to remote branch and set upstream tracking           |
| `git push`                               | Push committed changes to default tracked remote branch           |
| `git push origin <branch-name>`          | Push specific branch to GitHub                                    |
| `git push origin --delete <branch-name>` | Delete a branch on remote GitHub repository                       |
| `git fetch`                              | Download latest metadata from remote without merging              |
| `git fetch --all`                        | Download metadata from all configured remote servers              |
| `git pull`                               | Download latest remote commits and auto-merge into current branch |
| `git pull --rebase`                      | Fetch and rebase local commits on top of remote branch            |

---

## 10. Forking, Pull Requests & Open-Source Workflow

Collaborate on open-source or team projects via GitHub.

1. **Fork Repository**: Click `Fork` on GitHub project page to create a personal copy.
2. **Clone Forked Repo**: `git clone <forked-url>`
3. **Add Upstream Remote**: `git remote add upstream <original-project-url>`
4. **Sync Fork with Upstream**:
   ```bash
   git fetch upstream
   git checkout main
   git merge upstream/main
   ```
5. **Create Feature Branch**: `git checkout -b feature-branch`
6. **Push Changes**: `git push origin feature-branch`
7. **Create Pull Request**: Go to original GitHub repository and click `Compare & pull request`.

---

## 11. Advanced Git Operations

Maintain clean history, cherry-pick commits, and tag releases.

| Command                                 | Description                                                         |
| :-------------------------------------- | :------------------------------------------------------------------ |
| `git rebase main`                       | Reapply commits from current branch on top of `main` branch         |
| `git rebase -i HEAD~3`                  | Start interactive rebase to squash, edit, or reorder last 3 commits |
| `git rebase --continue`                 | Continue rebase process after resolving merge conflicts             |
| `git rebase --abort`                    | Cancel rebase operation and restore previous branch state           |
| `git cherry-pick <commit-hash>`         | Apply changes introduced by specific commit to active branch        |
| `git tag`                               | List all tags in repository                                         |
| `git tag v1.0.0`                        | Create lightweight tag at current commit                            |
| `git tag -a v1.0.0 -m "Release v1.0.0"` | Create annotated tag with release message                           |
| `git push origin v1.0.0`                | Push specific tag to remote repository                              |
| `git push origin --tags`                | Push all local tags to remote repository                            |
| `git tag -d v1.0.0`                     | Delete a local tag                                                  |
| `git push origin --delete v1.0.0`       | Delete tag from remote GitHub repository                            |
| `git reflog`                            | Display chronological history of all reference HEAD movements       |
| `git bisect start`                      | Start binary search session to locate commit that introduced bug    |
| `git bisect bad`                        | Mark current commit as containing bug                               |
| `git bisect good <commit-hash>`         | Mark known working commit without bug                               |
| `git bisect reset`                      | End bisecting session and return to original state                  |
