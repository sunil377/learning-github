# Git & GitHub Hands-On Practice Exercises

Follow these exercises in order. They progress from basic to more advanced concepts.

---

## Exercise 1: Initialize Your First Repository

### Objective

Set up Git locally and make your first commit.

### Instructions

1. **Open the terminal** in VS Code (Ctrl + `)
2. **Navigate to your project folder:**

   ```bash
   cd "c:\Users\sunil\Desktop\Projects\github"
   ```

3. **Check Git version:**

   ```bash
   git --version
   ```

4. **Configure Git** (if you haven't done this):

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

5. **Create a new folder for practice:**

   ```bash
   mkdir git-practice
   cd git-practice
   ```

6. **Initialize Git:**

   ```bash
   git init
   ```

   You should see: "Initialized empty Git repository in [path]"

7. **Check status:**

   ```bash
   git status
   ```

8. **Create a README file:**

   ```bash
   echo # My First Git Project > README.md
   ```

9. **Check status again:**

   ```bash
   git status
   ```

   Notice `README.md` is shown as untracked.

10. **Stage the file:**

    ```bash
    git add README.md
    ```

11. **Check status:**

    ```bash
    git status
    ```

    Notice the file is now staged (green).

12. **Create your first commit:**

    ```bash
    git commit -m "Initial commit: Add README"
    ```

13. **View your commit history:**
    ```bash
    git log --oneline
    ```

✅ **You've successfully made your first commit!**

---

## Exercise 2: Making Changes and Commits

### Objective

Practice the modify → stage → commit workflow.

### Instructions

1. **Create a new file:**

   ```bash
   echo console.log("Hello Git!") > app.js
   ```

2. **Check status:**

   ```bash
   git status
   ```

3. **Stage it:**

   ```bash
   git add app.js
   ```

4. **Commit it:**

   ```bash
   git commit -m "Add app.js with hello message"
   ```

5. **Create another file:**

   ```bash
   echo body { margin: 0; } > styles.css
   ```

6. **Stage and commit in one check:**

   ```bash
   git add styles.css
   git commit -m "Add CSS styles"
   ```

7. **View all commits:**

   ```bash
   git log --oneline
   ```

   You should see three commits now.

8. **Make a change to an existing file:**
   Open `README.md` in VS Code and add some content:

   ```markdown
   # My First Git Project

   This is a practice project for learning Git!

   ## Files

   - app.js: Main JavaScript file
   - styles.css: Styling
   ```

9. **Check what changed:**

   ```bash
   git diff README.md
   ```

10. **Stage and commit the change:**
    ```bash
    git add README.md
    git commit -m "Update README with project description"
    ```

✅ **You've practiced the full Git workflow!**

---

## Exercise 3: Working with Branches

### Objective

Create and merge branches.

### Instructions

1. **Check your current branch:**

   ```bash
   git branch
   ```

   You should be on `main` or `master`.

2. **Create a new branch:**

   ```bash
   git branch feature/dark-mode
   ```

3. **List branches:**

   ```bash
   git branch
   ```

4. **Switch to the new branch:**

   ```bash
   git checkout feature/dark-mode
   ```

5. **Verify you're on the branch:**

   ```bash
   git branch
   ```

   The current branch should have an asterisk.

6. **Create a new file on this branch:**

   ```bash
   echo /* Dark mode styles */ > dark-mode.css
   ```

7. **Commit the file:**

   ```bash
   git add dark-mode.css
   git commit -m "Add dark mode styles"
   ```

8. **Switch back to main:**

   ```bash
   git checkout main
   ```

9. **Verify the dark-mode.css file is not here:**

   ```bash
   ls dark-mode.css
   ```

   You should get a "file not found" error.

10. **Switch back to the feature branch:**

    ```bash
    git checkout feature/dark-mode
    ```

11. **Verify the file exists:**

    ```bash
    ls dark-mode.css
    ```

12. **Switch back to main:**

    ```bash
    git checkout main
    ```

13. **Merge the feature branch:**

    ```bash
    git merge feature/dark-mode
    ```

14. **Verify the file now exists on main:**

    ```bash
    ls dark-mode.css
    ```

15. **Delete the feature branch:**
    ```bash
    git branch -d feature/dark-mode
    ```

✅ **You've successfully created, worked on, and merged a branch!**

---

## Exercise 4: Undoing Changes

### Objective

Practice different ways to undo changes.

### Instructions

### Scenario A: Undo unstaged changes

1. **Modify a file:**

   ```bash
   echo "// This is a mistake" >> app.js
   ```

2. **Check status:**

   ```bash
   git status
   ```

3. **Undo the change:**

   ```bash
   git restore app.js
   ```

4. **Verify the file is restored:**
   ```bash
   git status
   ```

### Scenario B: Undo staged changes

1. **Modify the file:**

   ```bash
   echo "// Another mistake" >> app.js
   ```

2. **Stage it:**

   ```bash
   git add app.js
   ```

3. **Undo staging (but keep the change):**

   ```bash
   git restore --staged app.js
   ```

4. **Undo the change itself:**
   ```bash
   git restore app.js
   ```

### Scenario C: Undo a commit

1. **Create a commit you'll undo:**

   ```bash
   echo "// This commit will be undone" > temp.js
   git add temp.js
   git commit -m "Temporary commit"
   ```

2. **View your commits:**

   ```bash
   git log --oneline
   ```

3. **Undo the last commit (creates a new commit that reverses it):**

   ```bash
   git revert HEAD
   ```

   This will open an editor to confirm the revert message. Save and exit.

4. **Check your log:**

   ```bash
   git log --oneline
   ```

   You'll see a new "Revert" commit.

5. **Check the file was removed:**
   ```bash
   ls temp.js
   ```
   Should not exist.

✅ **You've practiced undoing changes at different stages!**

---

## Exercise 5: Viewing History

### Objective

Learn how to navigate and understand Git history.

### Instructions

1. **View commits in detail:**

   ```bash
   git log
   ```

2. **View commits in short format:**

   ```bash
   git log --oneline
   ```

3. **View last 3 commits:**

   ```bash
   git log -3
   ```

4. **View commits with changes:**

   ```bash
   git log -p
   ```

5. **View commits by author:**

   ```bash
   git log --author="Your Name"
   ```

6. **View specific file history:**

   ```bash
   git log README.md
   ```

7. **View what changed in a specific commit:**
   (Use a commit hash from your log)

   ```bash
   git show abc1234
   ```

8. **View differences between branches:**
   ```bash
   git diff main feature/branch-name
   ```

✅ **You've learned to read and understand Git history!**

---

## Exercise 6: Creating Meaningful Commit Messages

### Objective

Learn good commit message practices.

### Instructions

**Good commit messages follow this format:**

```
<type>: <subject>

<body (optional)>

<footer (optional)>
```

**Types:**

- `feat:` A new feature
- `fix:` A bug fix
- `docs:` Documentation
- `style:` Code style changes (formatting, etc.)
- `refactor:` Code refactoring without features or fixes
- `test:` Adding tests
- `chore:` Maintenance tasks

**Examples of good commits:**

```bash
git commit -m "feat: Add dark mode toggle button"

git commit -m "fix: Correct CSS alignment on mobile devices"

git commit -m "docs: Update installation instructions in README"

git commit -m "refactor: Simplify login validation logic"
```

**Practice:**

1. **Make a change to a file:**

   ```bash
   echo "// New feature" >> app.js
   ```

2. **Commit with a proper message:**

   ```bash
   git add app.js
   git commit -m "feat: Add new feature to app"
   ```

3. **Make another change:**

   ```bash
   echo "/* Fixed alignment */" >> styles.css
   ```

4. **Commit with good message:**

   ```bash
   git add styles.css
   git commit -m "fix: Correct CSS alignment issue"
   ```

5. **View your commits:**
   ```bash
   git log --oneline
   ```

✅ **You're writing professional Git commits!**

---

## Next: Setting Up GitHub

Once you complete these exercises, you're ready for GitHub:

1. **Create a GitHub account** at https://github.com
2. **Create a new repository** on GitHub
3. **Link your local repo to GitHub:**

   ```bash
   git remote add origin https://github.com/your-username/repo-name.git
   git branch -M main
   git push -u origin main
   ```

4. **Try pushing and pulling changes**

---

## Troubleshooting Tips

| Problem                                    | Solution                                           |
| ------------------------------------------ | -------------------------------------------------- |
| "fatal: not a git repository"              | Run `git init` to initialize the repo              |
| "error: your changes would be overwritten" | Commit or stash changes before switching branches  |
| "nothing to commit"                        | You need to make changes or stage existing changes |
| "branch not fully merged"                  | Use `git branch -D <branch>` to force delete       |
| "permission denied"                        | Make sure you have write permissions               |

---

## Quiz: Test Your Knowledge

Try to answer these without looking at the guide:

1. What command stages a file for commit?
2. What's the difference between `git fetch` and `git pull`?
3. How do you create and switch to a new branch in one command?
4. What does `git status` show?
5. How do you undo the last commit while keeping your changes?

**Answers:** Check the main guide if you're unsure!

---

Good luck! 🎉
