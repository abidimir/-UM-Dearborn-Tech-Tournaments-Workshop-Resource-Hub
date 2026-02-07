# Git Cheatsheet

A quick reference for the most commonly used Git commands.

---

## Setup & Configuration

```bash
# Set your name (used in commits)
git config --global user.name "Your Name"

# Set your email (use the same email as your GitHub account)
git config --global user.email "your.email@example.com"

# Check your configuration
git config --list

# Set default branch name to 'main'
git config --global init.defaultBranch main
```

---

## Creating & Cloning Repositories

```bash
# Initialize a new Git repository in the current folder
git init

# Clone an existing repository from GitHub
git clone https://github.com/username/repository.git

# Clone into a specific folder
git clone https://github.com/username/repository.git folder-name
```

---

## Basic Workflow

The typical Git workflow: **modify → stage → commit → push**

```bash
# Check the status of your files (what's changed, what's staged)
git status

# Stage a specific file for commit
git add filename.py

# Stage all changed files
git add .

# Commit staged changes with a message
git commit -m "Add login functionality"

# Push commits to GitHub (remote)
git push

# Pull latest changes from GitHub
git pull
```

---

## Viewing History & Changes

```bash
# View commit history
git log

# View commit history (compact, one line per commit)
git log --oneline

# View commit history with a graph (useful for branches)
git log --oneline --graph --all

# See what changed in a file (unstaged changes)
git diff filename.py

# See what's staged for commit
git diff --staged
```

---

## Branching

Branches let you work on features without affecting the main codebase.

```bash
# List all branches (* marks the current branch)
git branch

# Create a new branch
git branch feature-name

# Switch to a branch
git checkout feature-name

# Create AND switch to a new branch (shortcut)
git checkout -b feature-name

# Newer alternative to checkout for switching branches
git switch feature-name

# Create AND switch (newer syntax)
git switch -c feature-name
```

---

## Merging

```bash
# Merge a branch into your current branch
# (First, switch to the branch you want to merge INTO)
git checkout main
git merge feature-name

# Delete a branch after merging (local)
git branch -d feature-name

# Delete a branch (force, even if not merged)
git branch -D feature-name
```

---

## Working with Remotes (GitHub)

```bash
# View remote repositories
git remote -v

# Add a remote repository
git remote add origin https://github.com/username/repository.git

# Push a branch to GitHub (first time, sets up tracking)
git push -u origin branch-name

# Push to GitHub (after tracking is set up)
git push

# Pull changes from GitHub
git pull

# Fetch changes without merging (see what changed)
git fetch
```

---

## Undoing Things

```bash
# Unstage a file (keep the changes, just remove from staging)
git restore --staged filename.py

# Discard changes to a file (revert to last commit) ⚠️ DESTRUCTIVE
git restore filename.py

# Amend the last commit message
git commit --amend -m "New commit message"

# Undo the last commit but keep changes staged
git reset --soft HEAD~1

# Undo the last commit and unstage changes (keep files)
git reset HEAD~1

# Undo the last commit completely ⚠️ DESTRUCTIVE
git reset --hard HEAD~1
```

---

## .gitignore

Create a `.gitignore` file to tell Git which files to ignore:

```
# Example .gitignore

# Python
__pycache__/
*.pyc
venv/
.env

# IDE
.vscode/
.idea/

# OS files
.DS_Store
Thumbs.db

# Secrets (NEVER commit these)
*.pem
*.key
secrets.json
```

---

## Common Workflows

### Starting a New Project

```bash
mkdir my-project
cd my-project
git init
# ... create some files ...
git add .
git commit -m "Initial commit"
# Create repo on GitHub, then:
git remote add origin https://github.com/username/my-project.git
git push -u origin main
```

### Working on a Feature

```bash
git checkout main
git pull                          # Get latest changes
git checkout -b feature-login     # Create feature branch
# ... make changes ...
git add .
git commit -m "Add login form"
git push -u origin feature-login  # Push branch to GitHub
# Create Pull Request on GitHub
```

### Syncing with Team Changes

```bash
git checkout main
git pull
git checkout your-branch
git merge main                    # Bring main's changes into your branch
# Resolve any conflicts, then:
git add .
git commit -m "Merge main into feature branch"
```

---

## Quick Reference Table

| Command | What it does |
|---------|--------------|
| `git status` | See what's changed |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Save staged changes |
| `git push` | Upload to GitHub |
| `git pull` | Download from GitHub |
| `git checkout -b name` | Create & switch branch |
| `git merge branch` | Merge branch into current |
| `git log --oneline` | View history |

---

## Tips

- **Commit often** — Small, focused commits are easier to understand and revert
- **Write clear messages** — "Fix login bug" is better than "fixed stuff"
- **Pull before you push** — Avoid conflicts by staying up to date
- **Don't commit secrets** — API keys, passwords, and .env files should be in .gitignore
- **When in doubt, `git status`** — It tells you what to do next