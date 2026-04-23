# Git & GitHub Quick Reference Cheat Sheet

## ⚡ Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global --list              # Verify configuration
```

---

## 📁 Repository Basics

```bash
git init                                # Initialize a new repository
git clone <url>                         # Clone an existing repository
git status                              # Show status of working directory
git log                                 # Show commit history
git log --oneline                       # Show commits in short format
git log -p                              # Show commits with changes
git log --graph --all --decorate --oneline  # Visual commit graph
```

---

## 📝 Working with Changes

```bash
git add <file>                          # Stage a specific file
git add .                               # Stage all changes
git add -p                              # Interactively stage changes
git diff                                # Show unstaged changes
git diff --staged                       # Show staged changes
git diff <branch1> <branch2>            # Compare branches
```

---

## 💾 Committing

```bash
git commit -m "message"                 # Create a commit
git commit -am "message"                # Stage tracked files and commit
git commit --amend                      # Modify the last commit
git commit --amend --no-edit            # Add to last commit without changing message
```

---

## 🌿 Branches

```bash
git branch                              # List local branches
git branch -a                           # List all branches (local + remote)
git branch <name>                       # Create a new branch
git checkout <branch>                   # Switch to a branch
git checkout -b <branch>                # Create and switch to new branch
git switch <branch>                     # Switch to branch (newer syntax)
git switch -c <branch>                  # Create and switch (newer syntax)
git merge <branch>                      # Merge a branch into current branch
git branch -d <branch>                  # Delete a branch (safe)
git branch -D <branch>                  # Force delete a branch
git branch -m <old-name> <new-name>     # Rename a branch
git branch -v                           # Show last commit on each branch
```

---

## 🔄 Undoing Changes

```bash
git restore <file>                      # Discard changes in working directory
git restore --staged <file>             # Unstage a file
git reset HEAD <file>                   # Unstage a file (older syntax)
git reset --soft HEAD~1                 # Undo last commit, keep changes staged
git reset --mixed HEAD~1                # Undo last commit, keep changes unstaged
git reset --hard HEAD~1                 # Undo last commit, discard changes
git revert HEAD                         # Create new commit that undoes last
git clean -fd                           # Remove untracked files and directories
```

---

## 🔀 Stashing (Temporary Storage)

```bash
git stash                               # Temporarily save changes
git stash list                          # List all stashes
git stash pop                           # Apply last stash and remove it
git stash apply                         # Apply last stash (keep it)
git stash drop                          # Delete a stash
git stash show -p                       # View a stash's contents
```

---

## 🌐 Remote Repositories (GitHub)

```bash
git remote -v                           # View remote repositories
git remote add origin <url>             # Add a new remote
git remote remove origin                # Remove a remote
git remote set-url origin <url>         # Change remote URL
git clone <url>                         # Clone a repository
git fetch                               # Download changes from remote
git pull                                # Fetch and merge from remote
git pull --rebase                       # Fetch and rebase instead of merge
git push                                # Push commits to remote
git push origin <branch>                # Push a specific branch
git push -u origin <branch>             # Push and set upstream
git push origin --all                   # Push all branches
git push --tags                         # Push all tags
```

---

## 🏷️ Tags (Releases)

```bash
git tag                                 # List all tags
git tag <tag-name>                      # Create a lightweight tag
git tag -a <tag-name> -m "message"      # Create an annotated tag
git show <tag-name>                     # Show tag details
git push origin <tag-name>              # Push a specific tag
git push origin --tags                  # Push all tags
git delete <tag-name>                   # Delete a local tag
git push origin --delete <tag-name>     # Delete remote tag
```

---

## 🔍 Inspecting Code

```bash
git show <commit>                       # Show a specific commit
git blame <file>                        # Show who changed each line
git grep "search-term"                  # Search code content
git diff HEAD~1 HEAD                    # Show changes in last commit
git diff <branch1>..<branch2>           # Compare branches
```

---

## 🐛 Debugging

```bash
git bisect start                        # Start binary search for bad commit
git bisect bad                          # Mark current commit as bad
git bisect good <commit>                # Mark a known good commit
git bisect reset                        # End bisect session
git log --oneline --all --graph         # Visual history
git reflog                              # Show reference logs
```

---

## 🚀 Common Workflows

### Feature Branch Workflow

```bash
# Create feature branch
git checkout -b feature/my-feature

# Make changes and commits
echo "new code" >> file.js
git add file.js
git commit -m "feat: Add new feature"

# Push to GitHub
git push origin feature/my-feature

# Go to GitHub and create a Pull Request
# After approval, merge on GitHub

# Back on local, update main
git checkout main
git pull origin main
```

### Fix a Mistake

```bash
# Undo last commit but keep changes
git reset --soft HEAD~1

# Fix the code
echo "fixed" >> file.js

# Re-commit with better message
git add file.js
git commit -m "fix: Corrected issue"
```

### Sync with Main

```bash
git fetch origin                        # Get latest from GitHub
git merge origin/main                   # Merge latest main into current branch
# Or use rebase for cleaner history:
git rebase origin/main
```

---

## 📊 Useful Aliases (Add to Config)

```bash
# View commits more clearly
git config --global alias.hist 'log --oneline --all --graph --decorate'

# Quick status
git config --global alias.st 'status'

# Unstage alias
git config --global alias.unstage 'restore --staged'

# Last commit
git config --global alias.last 'log -1 HEAD'
```

Then use:

```bash
git hist          # Instead of git log --oneline --all --graph --decorate
git st            # Instead of git status
git unstage file  # Instead of git restore --staged file
```

---

## ⚠️ Dangerous Commands

**Be careful with these:**

```bash
git reset --hard                        # Loses uncommitted changes permanently
git push --force                        # Overwrites remote history
git clean -fd                           # Permanently deletes untracked files
git rebase <branch>                     # Rewrites history (don't do on shared branches)
```

---

## 💡 Pro Tips

1. **Commit often**: Small, focused commits are easier to understand
2. **Pull before push**: Always sync before pushing to avoid conflicts
3. **Use branches**: Never commit directly to main
4. **Write good messages**: Help future you understand what you changed
5. **Review before merge**: Always check diffs before committing
6. **Use .gitignore**: Prevent committing files you shouldn't track
7. **Backup before reset**: Use `git reflog` to recover "lost" commits

---

## 🔗 Resources

- [Official Git Book](https://git-scm.com/book)
- [GitHub Docs](https://docs.github.com)
- [Git Visual Cheat Sheet](https://marklodato.github.io/visual-git-guide/)
- [Pro Git (Free Book)](https://git-scm.com/book/en/v2)

---

## 📌 Remember

- `.git` folder = Repository data (hidden folder)
- `main` or `master` = Default branch
- `origin` = Remote repository name
- `HEAD` = Current commit reference
- `commits` = Snapshots of your code

Good luck with Git! 🚀
