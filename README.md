# Git Learning

A practical Git and GitHub learning repository created to understand and practice **version control, commits, branches, merging, rebasing, remote repositories, collaboration workflows, and common Git operations**.

The repository also contains simple JavaScript examples that simulate real software-development updates such as adding a button, login page, footer, payment integration, UPI integration, and bug fixes.

---

## 🎯 Purpose

This repository is mainly created for learning and practicing:

* Git fundamentals
* GitHub workflow
* Repository management
* Staging and commits
* Branching
* Merging
* Rebasing
* Remote repositories
* Push / Pull / Fetch
* Stashing changes
* Undoing changes
* Reset and Revert
* Merge conflicts
* Tags
* Git history
* Feature-development workflow
* Bug-fixing workflow

---

# 🧰 Git & GitHub

## What is Git?

**Git** is a distributed version-control system used to track changes in source code and collaborate with other developers.

## What is GitHub?

**GitHub** is a cloud-based platform for hosting Git repositories and collaborating with other developers.

### Simple Relationship

```text
Git
 │
 ├── Track changes
 ├── Create commits
 ├── Create branches
 ├── Merge changes
 └── Manage project history
          │
          ▼
       GitHub
          │
          ├── Remote repository
          ├── Collaboration
          ├── Pull Requests
          ├── Issues
          └── Code hosting
```

---

# 🚀 Getting Started

## 1. Check Git Installation

```bash
git --version
```

---

# 📁 Repository Operations

## Initialize a Repository

Create a new local Git repository:

```bash
git init
```

This creates the `.git` directory.

## Clone an Existing Repository

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/VaibhavDubey95u/Git-Learning-.git
```

## Check Repository Status

```bash
git status
```

Shows:

* Modified files
* Untracked files
* Staged files
* Current branch

---

# 👤 Git Configuration

## Set Username

```bash
git config --global user.name "Your Name"
```

## Set Email

```bash
git config --global user.email "your@email.com"
```

## View Configuration

```bash
git config --list
```

## View a Specific Configuration

```bash
git config user.name
git config user.email
```

---

# 📝 Basic Git Workflow

The most important Git workflow is:

```text
Modify Files
     ↓
git status
     ↓
git add
     ↓
Staging Area
     ↓
git commit
     ↓
Local Repository
     ↓
git push
     ↓
GitHub
```

---

# ➕ Add Changes

## Add One File

```bash
git add app.js
```

## Add Multiple Files

```bash
git add file1.js file2.js
```

## Add All Changes

```bash
git add .
```

---

# 💾 Commit Changes

## Create a Commit

```bash
git commit -m "Add login page"
```

A commit creates a snapshot of the staged changes.

### Good Commit Messages

```bash
git commit -m "Add login page"
git commit -m "Add payment gateway"
git commit -m "Fix login validation bug"
git commit -m "Update footer"
```

### View Last Commit

```bash
git show
```

---

# 📜 Git History

## View Commit History

```bash
git log
```

## Compact History

```bash
git log --oneline
```

## Graphical History

```bash
git log --oneline --graph --all
```

## View a Specific Commit

```bash
git show <commit-id>
```

---

# 🌿 Branches

Branches allow developers to work on features independently without directly modifying the main branch.

## List Branches

```bash
git branch
```

## Create a Branch

```bash
git branch feature-login
```

## Switch to a Branch

```bash
git switch feature-login
```

## Create and Switch

```bash
git switch -c feature-login
```

Older Git syntax:

```bash
git checkout -b feature-login
```

## Delete a Branch

```bash
git branch -d feature-login
```

Force delete:

```bash
git branch -D feature-login
```

---

# 🔀 Merge

Merge combines changes from one branch into another.

Example:

```text
main
 │
 ├───────────────●
 │                \
 │                 ● feature-login
 │                 ●
 │                /
 └───────────────●
```

## Merge a Branch

First switch to the target branch:

```bash
git switch main
```

Then:

```bash
git merge feature-login
```

---

# ♻️ Rebase

Rebase moves your branch commits on top of another branch.

```bash
git switch feature-login
git rebase main
```

### Merge vs Rebase

```text
Merge:

A---B---C main
     \
      D---E feature
           \
            M


Rebase:

A---B---C---D'---E' feature
```

### Important

Rebase rewrites commit history, so avoid rebasing shared/public branches unless you understand the consequences.

---

# ☁️ Remote Repository

## View Remote

```bash
git remote -v
```

## Add Remote

```bash
git remote add origin <repository-url>
```

Example:

```bash
git remote add origin https://github.com/username/project.git
```

## Change Remote URL

```bash
git remote set-url origin <new-url>
```

## Remove Remote

```bash
git remote remove origin
```

---

# ⬆️ Push

## Push Current Branch

```bash
git push
```

## Push to Specific Remote and Branch

```bash
git push origin main
```

## Push a New Branch

```bash
git push -u origin feature-login
```

The `-u` option establishes the upstream relationship.

---

# ⬇️ Pull

`git pull` downloads changes from the remote repository and integrates them into the current branch.

```bash
git pull
```

Specific branch:

```bash
git pull origin main
```

### Pull Workflow

```text
GitHub
   │
   ▼
Fetch Changes
   │
   ▼
Merge Changes
   │
   ▼
Local Branch
```

---

# 📥 Fetch

`git fetch` downloads changes from the remote repository without automatically merging them.

```bash
git fetch
```

Fetch a specific remote:

```bash
git fetch origin
```

### Pull vs Fetch

| Command     | Downloads Changes | Automatically Integrates |
| ----------- | ----------------: | -----------------------: |
| `git fetch` |                 ✅ |                        ❌ |
| `git pull`  |                 ✅ |                        ✅ |

---

# 🧳 Git Stash

Git stash temporarily stores uncommitted changes.

## Stash Changes

```bash
git stash
```

## View Stashes

```bash
git stash list
```

## Apply Latest Stash

```bash
git stash apply
```

## Apply and Remove Stash

```bash
git stash pop
```

## Delete a Stash

```bash
git stash drop
```

## Delete All Stashes

```bash
git stash clear
```

### Example Use Case

You are working on a feature but need to quickly switch branches:

```text
Uncommitted Work
       ↓
   git stash
       ↓
Clean Working Tree
       ↓
Switch Branch
       ↓
Complete Other Work
       ↓
git stash pop
       ↓
Continue Feature
```

---

# ↩️ Undo Changes

## Discard Changes in a File

```bash
git restore app.js
```

This restores the file to its last committed state.

## Unstage a File

```bash
git restore --staged app.js
```

The changes remain in the working directory but are removed from staging.

---

# 🔄 Reset

Git reset moves the current branch's `HEAD` to another commit.

## Soft Reset

```bash
git reset --soft HEAD~1
```

Removes the latest commit but keeps changes staged.

## Mixed Reset

```bash
git reset HEAD~1
```

Removes the latest commit and unstages the changes while keeping the files modified.

## Hard Reset

```bash
git reset --hard HEAD~1
```

Removes the latest commit and its changes from the working tree.

⚠️ Be careful with `--hard` because uncommitted changes can be permanently lost.

---

# ↩️ Revert

`git revert` creates a **new commit** that reverses the changes introduced by an earlier commit.

```bash
git revert <commit-id>
```

### Reset vs Revert

| Reset                    | Revert                    |
| ------------------------ | ------------------------- |
| Moves branch history     | Creates a new commit      |
| Can rewrite history      | Preserves history         |
| Useful for local commits | Safer for shared branches |
| Can remove commits       | Reverses commits          |

---

# ⚔️ Merge Conflicts

A merge conflict happens when Git cannot automatically combine changes.

Example:

```text
main
 │
 ├── Change A
 │
 └── Change B

feature
 │
 ├── Different Change A
 │
 └── Different Change B
```

Git may show:

```text
<<<<<<< HEAD
Current branch code
=======
Incoming branch code
>>>>>>> feature-login
```

## Resolve a Conflict

1. Open the conflicted file.
2. Decide which code should remain.
3. Remove conflict markers.
4. Save the file.
5. Stage the resolved file.

```bash
git add .
```

6. Complete the merge:

```bash
git commit
```

For a rebase conflict:

```bash
git add .
git rebase --continue
```

---

# 🏷️ Git Tags

Tags are commonly used to mark important versions/releases.

## Create a Tag

```bash
git tag v1.0.0
```

## List Tags

```bash
git tag
```

## Create an Annotated Tag

```bash
git tag -a v1.0.0 -m "Version 1.0.0"
```

## Push Tag

```bash
git push origin v1.0.0
```

## Push All Tags

```bash
git push origin --tags
```

---

# 🔎 Compare Changes

## View Unstaged Changes

```bash
git diff
```

## View Staged Changes

```bash
git diff --staged
```

## Compare Two Commits

```bash
git diff <commit1> <commit2>
```

---

# 🔍 Find Information

## Find a Commit by Message

```bash
git log --grep="login"
```

## Find Who Changed a Line

```bash
git blame app.js
```

## Show Remote Information

```bash
git remote -v
```

---

# 🗑️ Remove Files

## Remove File and Stage Removal

```bash
git rm app.js
```

## Remove File from Git but Keep Locally

```bash
git rm --cached app.js
```

---

# 📦 `.gitignore`

`.gitignore` tells Git which files/folders should not be tracked.

Example:

```gitignore
node_modules/
.env
dist/
*.log
```

Common files to ignore:

* Dependencies
* Environment variables
* Build output
* Logs
* IDE-specific files

---

# 🔄 Rename Files

```bash
git mv old-file.js new-file.js
```

Then commit:

```bash
git commit -m "Rename file"
```

---

# 🧹 Clean Untracked Files

Preview files that would be removed:

```bash
git clean -n
```

Remove untracked files:

```bash
git clean -f
```

⚠️ Use this carefully because untracked files can be permanently deleted.

---

# 🔗 GitHub Collaboration Workflow

A typical team workflow:

```text
Clone Repository
       ↓
Create Feature Branch
       ↓
Make Changes
       ↓
git add
       ↓
git commit
       ↓
git push
       ↓
Create Pull Request
       ↓
Code Review
       ↓
Merge
       ↓
Delete Feature Branch
```

Example:

```bash
git clone <repository-url>

git switch -c feature-payment

# Make changes

git add .
git commit -m "Add payment feature"

git push -u origin feature-payment
```

Then create a Pull Request on GitHub.

---

# 🔥 Common Git Commands Cheat Sheet

| Operation             | Command                       |
| --------------------- | ----------------------------- |
| Initialize repository | `git init`                    |
| Clone repository      | `git clone <url>`             |
| Check status          | `git status`                  |
| Add file              | `git add <file>`              |
| Add everything        | `git add .`                   |
| Commit                | `git commit -m "message"`     |
| View history          | `git log`                     |
| Short history         | `git log --oneline`           |
| Create branch         | `git branch <name>`           |
| Switch branch         | `git switch <name>`           |
| Create + switch       | `git switch -c <name>`        |
| Merge                 | `git merge <branch>`          |
| Rebase                | `git rebase <branch>`         |
| Push                  | `git push`                    |
| Pull                  | `git pull`                    |
| Fetch                 | `git fetch`                   |
| Stash                 | `git stash`                   |
| Apply stash           | `git stash pop`               |
| Show changes          | `git diff`                    |
| Undo working change   | `git restore <file>`          |
| Unstage file          | `git restore --staged <file>` |
| Reset commit          | `git reset`                   |
| Revert commit         | `git revert <commit>`         |
| Create tag            | `git tag <name>`              |
| Show remotes          | `git remote -v`               |
| Remove tracked file   | `git rm <file>`               |
| Rename file           | `git mv <old> <new>`          |
| Find line changes     | `git blame <file>`            |

---

# 🧪 Development Updates in This Repository

The JavaScript code represents a simple development timeline.

### Button

```javascript
const button = "added a button";
console.log(button);
```

### Login Page

```javascript
const login = "login page added";
console.log(login);
```

### Footer

```javascript
const footer = "footer added in our website";
console.log(footer);
```

### Payment Gateway

```javascript
const payment = "integrated the payment gateway";
```

### UPI

```javascript
const upi = "integrated th upi";
console.log(upi);
```

### Latest Update

```javascript
console.log("latest update");
```

### Bug Fix

```javascript
// i am fixing some bug
console.log("bug fix");
```

These examples represent the type of incremental changes that can be tracked using Git commits.

---

# 🧠 Important Git Concepts

```text
Working Directory
       │
       │ git add
       ▼
Staging Area
       │
       │ git commit
       ▼
Local Repository
       │
       │ git push
       ▼
Remote Repository
      GitHub
```

### Four Important Areas

| Area              | Meaning                              |
| ----------------- | ------------------------------------ |
| Working Directory | Files you are currently editing      |
| Staging Area      | Changes selected for the next commit |
| Local Repository  | Your local Git history               |
| Remote Repository | Repository hosted on GitHub          |

---

# 🎯 Learning Objectives

After practicing this repository, you should understand:

* How Git tracks changes
* How repositories work
* Working directory vs staging area
* Creating commits
* Reading commit history
* Creating and managing branches
* Merging branches
* Rebasing branches
* Handling merge conflicts
* Working with remote repositories
* Fetching and pulling changes
* Pushing changes
* Temporarily storing changes with stash
* Undoing changes
* Resetting commits
* Reverting commits safely
* Creating releases with tags
* Using `.gitignore`
* Collaborating through GitHub

---

# 🚀 Recommended Git Learning Path

```text
Git Basics
    ↓
init / clone
    ↓
status
    ↓
add
    ↓
commit
    ↓
log
    ↓
GitHub
    ↓
push / pull / fetch
    ↓
Branches
    ↓
merge
    ↓
Merge Conflicts
    ↓
rebase
    ↓
stash
    ↓
reset / revert
    ↓
tags
    ↓
Pull Requests
    ↓
Team Collaboration
```

---

# 👨‍💻 Author

**Vaibhav Dubey**

Software Engineering Student | Full-Stack Development | AI/ML Enthusiast

GitHub: [@VaibhavDubey95u](https://github.com/VaibhavDubey95u)

---

# 📄 License

No explicit open-source license is currently specified for this learning repository.

---

⭐ This repository is part of my learning journey with **Git, GitHub, and modern software-development workflows**.
