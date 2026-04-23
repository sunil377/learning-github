# Git & GitHub Learning Guide for Beginners

## Table of Contents

1. [What is Git?](#what-is-git)
2. [Core Concepts](#core-concepts)
3. [Setting Up Git](#setting-up-git)
4. [Basic Git Workflow](#basic-git-workflow)
5. [Branching & Merging](#branching--merging)
6. [Collaboration](#collaboration)
7. [GitHub Features](#github-features)
8. [Practice Exercises](#practice-exercises)

---

## What is Git?

**Git** is a version control system that tracks changes to your files over time. Think of it as:

- A **time machine** for your code (you can go back to any previous version)
- A **notebook** that records who changed what and when
- A **collaboration tool** that lets multiple people work on the same project safely

**GitHub** is a cloud platform built on top of Git that makes collaboration even easier. It's where you upload your Git repositories online.

### Why use Git?

- **Track history**: See every change made to your project
- **Backup**: Your code is safely stored online
- **Collaboration**: Multiple developers can work together
- **Branching**: Experiment with new features without breaking the main code
- **Code review**: Others can review your changes before they're merged

---

## Core Concepts

### 1. **Repository (Repo)**

A folder that contains your project and a hidden `.git` folder. This `.git` folder stores all the history and metadata.

```
my-project/
├── .git/                 ← Git stores everything here
├── src/
├── index.html
└── README.md
```

### 2. **Commits**

A "snapshot" of your code at a specific point in time. Each commit includes:

- The changes made
- Who made them
- When it was made
- A message describing the change

Think of commits as checkpoints in a video game.

```
Commit A: "Added login feature"
↓
Commit B: "Fixed bug in password validation"
↓
Commit C: "Added email confirmation"
```

### 3. **Branches**

Independent lines of development. The default branch is `main` (or `master` in older repos).

```
main:    A ──→ B ──→ C ──→ D
                    ↓
feature: ──────────→ E ──→ F
```

You can create branches to:

- Work on features without affecting main code
- Experiment safely
- Collaborate on different features simultaneously

### 4. **Working Directory, Staging Area, and Repository**

```
┌──────────────────┐
│  Working Dir     │  Your actual files
│  (Modified)      │
└────────┬─────────┘
         │ git add
         ↓
┌──────────────────┐
│  Staging Area    │  Files ready to commit
│  (Staged)        │
└────────┬─────────┘
         │ git commit
         ↓
┌──────────────────┐
│  Repository      │  Saved in Git history
│  (Committed)     │
└──────────────────┘
```

### 5. **The Three States of a File**

- **Modified**: You changed the file but haven't staged it
- **Staged**: You've marked the file to be committed
- **Committed**: The change is saved in Git history

---

## Setting Up Git

### Step 1: Check if Git is installed

```bash
git --version
```

### Step 2: Configure your identity

Git needs to know who you are for every commit:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Step 3: Verify configuration

```bash
git config --global --list
```

---

## Basic Git Workflow

### Step 1: Initialize a repository

```bash
git init
```

This creates a new `.git` folder and initializes Git tracking.

### Step 2: Check status

```bash
git status
```

Shows which files are modified, staged, or untracked.

### Step 3: Stage changes

```bash
git add filename.txt        # Stage a specific file
git add .                   # Stage all changes
```

### Step 4: Commit changes

```bash
git commit -m "Descriptive message about what you changed"
```

### Step 5: View history

```bash
git log                     # View all commits
git log --oneline           # View commits in short format
```

### Example Workflow

```bash
# 1. Create/modify a file
echo "Hello World" > hello.txt

# 2. Check status
git status
# Output: hello.txt is untracked

# 3. Stage the file
git add hello.txt

# 4. Commit
git commit -m "Add hello.txt"

# 5. Check history
git log --oneline
# Output: abc1234 Add hello.txt
```

---

## Branching & Merging

### Create a new branch

```bash
git branch feature-login        # Create branch
git checkout feature-login      # Switch to it
# Or do both at once:
git checkout -b feature-login
```

### List branches

```bash
git branch                      # List local branches
git branch -a                   # List all branches (including remote)
```

### Switch branches

```bash
git checkout main               # Switch to main
git checkout feature-login      # Switch back to feature
```

### Merge branches

```bash
git checkout main               # Switch to main first
git merge feature-login         # Merge feature into main
```

### Delete a branch

```bash
git branch -d feature-login     # Delete after merging
git branch -D feature-login     # Force delete
```

### Merge Conflicts

When the same line is changed in different ways, Git can't automatically merge. You'll need to:

1. Open the conflicted file
2. Manually resolve the conflict
3. Stage and commit the resolved file

```
<<<<<<< HEAD (main)
This is from main
=======
This is from feature branch
>>>>>>> feature-login
```

---

## Collaboration

### Clone a repository

```bash
git clone https://github.com/username/repo-name.git
```

### Push your changes to GitHub

```bash
git push origin main            # Push main branch
git push origin feature-login   # Push a feature branch
```

### Pull changes from GitHub

```bash
git pull origin main            # Fetch and merge
```

### Fetch changes (without merging)

```bash
git fetch origin                # Download changes
git merge origin/main           # Merge if satisfied
```

### Key Remote Commands

```bash
git remote -v                   # View remote repositories
git remote add origin URL       # Add a remote
git remote remove origin        # Remove a remote
```

---

## GitHub Features

### 1. **Pull Requests (PRs)**

A way to propose changes for review before merging.

**Workflow:**

1. Create a branch for your feature
2. Push the branch to GitHub
3. Open a Pull Request
4. Others review and discuss your changes
5. Merge when approved

### 2. **Issues**

Used to track bugs, features, and tasks.

**Creating an issue:**

- Click "Issues" tab on GitHub
- Click "New Issue"
- Describe the problem/request
- Assign labels, assignees, and milestones

### 3. **Discussions**

For longer-form conversations and questions.

### 4. **Wiki**

Documentation for your project.

### 5. **Releases**

Mark specific points in your history as releases.

```bash
git tag v1.0.0                  # Create a tag
git push origin v1.0.0          # Push tag to GitHub
```

---

## Practice Exercises

### Exercise 1: Basic Git Setup & First Commit

**Goal:** Initialize a repo, create files, and make your first commit

```bash
# 1. Create a new folder
mkdir my-first-project
cd my-first-project

# 2. Initialize Git
git init

# 3. Create a file
echo "# My First Project" > README.md

# 4. Stage and commit
git add README.md
git commit -m "Initial commit: Add README"

# 5. View history
git log --oneline
```

### Exercise 2: Working with Branches

**Goal:** Create branches, switch between them, and merge

```bash
# 1. Create a feature branch
git checkout -b feature/add-greeting

# 2. Create/modify a file
echo "function greet() { console.log('Hello!'); }" > greeting.js

# 3. Stage and commit
git add greeting.js
git commit -m "Add greeting function"

# 4. Switch back to main
git checkout main

# 5. Verify the file doesn't exist on main
ls greeting.js          # File not here on main

# 6. Switch back to feature branch
git checkout feature/add-greeting

# 7. Merge into main
git checkout main
git merge feature/add-greeting

# 8. Verify file now exists on main
ls greeting.js          # File exists now!
```

### Exercise 3: Simulating Collaboration

**Goal:** Understand pushing and pulling

_On your local machine:_

```bash
# 1. Make changes on a feature branch
git checkout -b feature/improvements
echo "// Some improvement" > file.js
git add file.js
git commit -m "Add improvements"

# 2. Push to GitHub (you'll need a GitHub repo for this)
git push origin feature/improvements
```

_Later (or on another machine):_

```bash
# 1. Pull the changes
git pull origin feature/improvements

# 2. Merge into main
git checkout main
git pull origin main
git merge feature/improvements
git push origin main
```

### Exercise 4: Undo Changes

**Goal:** Practice undoing mistakes

```bash
# If you haven't staged yet:
git restore filename.txt        # Discard changes

# If you've staged but not committed:
git restore --staged filename.txt

# If you've committed:
git revert HEAD                 # Create a new commit that undoes the last commit
git reset --soft HEAD~1         # Undo last commit, keep changes staged
git reset --hard HEAD~1         # Undo last commit, discard changes
```

---

## Common Git Commands Reference

| Command                    | Purpose                     |
| -------------------------- | --------------------------- |
| `git init`                 | Initialize a new repository |
| `git status`               | Show file status            |
| `git add <file>`           | Stage a file                |
| `git commit -m "msg"`      | Create a commit             |
| `git log`                  | View commit history         |
| `git checkout -b <branch>` | Create and switch to branch |
| `git merge <branch>`       | Merge a branch              |
| `git push`                 | Send commits to remote      |
| `git pull`                 | Fetch and merge from remote |
| `git clone <url>`          | Copy a repository           |
| `git diff`                 | Show changes                |
| `git reset`                | Undo commits                |
| `git stash`                | Temporarily save changes    |

---

## Tips for Success

1. **Commit frequently** - Small, logical commits are easier to understand and debug
2. **Write clear commit messages** - Future you will thank present you
3. **Use branches** - Never work directly on main; always create a feature branch
4. **Pull before pushing** - Avoid conflicts by syncing with the remote first
5. **Review before merging** - Use pull requests to catch issues early
6. **Read error messages** - Git's errors are usually quite helpful

---

## Next Steps

1. **Complete the practice exercises** above
2. **Create a GitHub account** at https://github.com
3. **Create your first GitHub repository** and push local code to it
4. **Explore other developers' repos** to learn from real-world usage
5. **Practice collaborating** by contributing to open-source projects

Good luck with your Git and GitHub journey! 🚀
