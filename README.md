# 🚀 Git & GitHub Masterclass

> A comprehensive, beginner-friendly guide to mastering Git and GitHub — from your very first commit to advanced workflows used by professional teams.

---

## 📑 Table of Contents

1. [What is Git?](#-what-is-git)
2. [What is GitHub?](#-what-is-github)
3. [Git vs GitHub — Key Differences](#-git-vs-github--key-differences)
4. [Installation & Setup](#%EF%B8%8F-installation--setup)
5. [Core Concepts You Must Know](#-core-concepts-you-must-know)
6. [Basic Commands](#-basic-commands)
7. [Branching & Merging](#-branching--merging)
8. [Working with Remote Repositories](#-working-with-remote-repositories)
9. [Undoing Changes](#-undoing-changes)
10. [Advanced Commands](#-advanced-commands)
11. [Git Best Practices](#-git-best-practices)
12. [Common Workflows](#-common-workflows)
13. [Glossary](#-glossary)
14. [Resources](#-resources)

---

## 🔍 What is Git?

**Git** is a free, open-source **distributed version control system (DVCS)**. Think of it like an "unlimited undo" system for your entire project — it records every change you make, who made it, and when, so you can always go back.

### Why use Git?

- **Track every change** — See exactly what changed, when, and by whom.
- **Collaborate safely** — Multiple people can work on the same project simultaneously without overwriting each other's work.
- **Experiment freely** — Create branches to try new ideas. If they don't work, just delete the branch — your main code is untouched.
- **Work offline** — Everything is stored locally; you don't need an internet connection to commit or view history.

---

## 🐙 What is GitHub?

**GitHub** is a cloud-based platform that hosts Git repositories online. It adds powerful collaboration features on top of Git:

- **Pull Requests** — Propose changes and review code before merging.
- **Issues** — Track bugs, feature requests, and tasks.
- **Actions** — Automate testing, building, and deploying your code.
- **Social features** — Follow developers, star projects, and contribute to open source.

> **Analogy:** If Git is Microsoft Word's "Track Changes" feature, GitHub is Google Docs — it puts your work online so others can see, comment, and collaborate.

---

## ⚖ Git vs GitHub — Key Differences

| # | Git | GitHub |
|---|-----|--------|
| 1 | A command-line **tool** you install locally | A **web platform** with a graphical interface |
| 2 | Open-source **software** | A **service** (owned by Microsoft) |
| 3 | Runs **locally** on your computer | Hosted **in the cloud** |
| 4 | Maintained by the **Linux community** | Maintained by **Microsoft** |
| 5 | Focused on **version control** | Focused on **collaboration & hosting** |
| 6 | No user management features | Built-in user management, teams, and permissions |
| 7 | Minimal tool integrations | Rich **marketplace** for integrations (CI/CD, project management, etc.) |
| 8 | Desktop interface: **Git GUI** | Desktop interface: **GitHub Desktop** |
| 9 | Competitors: SVN, Mercurial, CVS | Competitors: GitLab, Bitbucket, AWS CodeCommit |

---

## 🛠️ Installation & Setup

### Step 1: Install Git

Download Git for your operating system: **[git-scm.com/download](https://git-scm.com/download)**

After installing, verify the installation by opening your terminal and running:

```bash
git --version
```

You should see something like `git version 2.42.0`.

### Step 2: Create a GitHub Account

Sign up for free at **[github.com](https://github.com/)**

### Step 3: Configure Git (Required — Do This First!)

Tell Git who you are. This information is attached to every commit you make.

```bash
# Set your name
git config --global user.name "Your Name"

# Set your email (use the same email as your GitHub account)
git config --global user.email "youremail@example.com"
```

Verify your configuration:

```bash
# Check your name
git config --global user.name

# Check your email
git config --global user.email

# See all your Git settings
git config --list
```

### Step 4 (Recommended): Set Default Branch Name

Modern convention uses `main` instead of `master`:

```bash
git config --global init.defaultBranch main
```

### Step 5 (Recommended): Set Your Default Editor

```bash
# Use VS Code as your default editor
git config --global core.editor "code --wait"

# Or use nano (simpler)
git config --global core.editor "nano"
```

---

## 💡 Core Concepts You Must Know

Before diving into commands, understand these fundamental concepts:

### The Three Areas of Git

```
┌──────────────┐     git add     ┌──────────────┐   git commit   ┌──────────────┐
│  Working     │ ──────────────► │   Staging    │ ─────────────► │  Repository  │
│  Directory   │                 │   Area       │                │  (.git)      │
│              │                 │  (Index)     │                │              │
│ Your files   │                 │ Ready to     │                │ Permanent    │
│ as you see   │                 │ be committed │                │ history      │
│ them         │                 │              │                │              │
└──────────────┘                 └──────────────┘                └──────────────┘
```

1. **Working Directory** — The folder on your computer where you edit files.
2. **Staging Area (Index)** — A "preparation zone" where you decide which changes to include in your next commit.
3. **Repository (.git folder)** — The permanent history of all your committed changes.

### What is a Commit?

A **commit** is a snapshot of your project at a specific point in time. Each commit has:
- A unique **hash** (ID), e.g., `a1b2c3d`
- The **author's** name and email
- A **timestamp**
- A **message** describing the change
- A pointer to the **parent commit** (previous snapshot)

### What is a Branch?

A **branch** is a lightweight, movable pointer to a specific commit. It lets you work on features, fixes, or experiments without affecting the main codebase.

---

## 📘 Basic Commands

### Initializing a Repository

```bash
# Create a brand-new Git repository in your current folder
git init
```

> **What it does:** Creates a hidden `.git` folder that stores all version history. Run this once per project.

### Cloning an Existing Repository

```bash
# Download a remote repository to your computer
git clone <repository-url>
```

**Example:**
```bash
git clone https://github.com/username/my-project.git
```

> **What it does:** Creates a local copy of a remote repository, including all files, branches, and commit history.

### Checking Status

```bash
# See which files have been modified, staged, or are untracked
git status
```

> **What it does:** Shows the current state of your working directory and staging area. Use this **often** — it's your best friend.

```bash
# Compact version of status
git status -s
```

### Staging Changes (Adding Files)

```bash
# Stage a specific file
git add filename.txt

# Stage multiple specific files
git add file1.txt file2.txt file3.txt

# Stage all changes in the current directory and subdirectories
git add .

# Stage all changes in the entire repository
git add -A

# Interactively choose which parts of a file to stage
git add -p
```

> **What it does:** Moves changes from your Working Directory to the Staging Area, marking them "ready to commit."

> **💡 Best Practice:** Avoid blindly using `git add .`. Review what you're staging first with `git status`, and only stage files relevant to the current change.

### Committing Changes

```bash
# Commit with an inline message
git commit -m "Add user login feature"

# Stage all tracked files AND commit in one step
git commit -am "Fix typo in README"

# Open your editor to write a detailed commit message (title + body)
git commit
```

> **What it does:** Saves a permanent snapshot of everything in the Staging Area to the repository history.

> **💡 Best Practice:** Write clear, descriptive commit messages. A good commit message explains **why** the change was made, not just what changed.

#### How to Write Great Commit Messages

```
<type>: <short summary in imperative mood> (max 50 chars)

<optional body — explain WHY, not what> (wrap at 72 chars)
```

**Good examples:**
```
feat: add email validation to signup form
fix: resolve crash when user profile is empty
docs: update API authentication guide
refactor: simplify database connection logic
```

**Bad examples:**
```
fixed stuff
update
asdfgh
changes
```

### Viewing Commit History

```bash
# Full commit log (press 'q' to exit)
git log

# Compact one-line-per-commit view
git log --oneline

# Show the last 5 commits
git log -5

# Graphical branch view
git log --oneline --graph --all

# Show commits by a specific author
git log --author="Your Name"

# Show commits within a date range
git log --after="2024-01-01" --before="2024-12-31"
```

### Viewing Changes (Diffs)

```bash
# Show unstaged changes (working directory vs staging area)
git diff

# Show staged changes (staging area vs last commit)
git diff --staged

# Compare two branches
git diff main..feature-branch

# Show changes in a specific file
git diff filename.txt
```

### Inspecting a Specific Commit

```bash
# Show details and changes introduced by a commit
git show <commit-hash>
```

**Example:**
```bash
git show a1b2c3d
```

### Removing & Moving Files

```bash
# Remove a file from Git AND your filesystem
git rm filename.txt

# Remove a file from Git but keep it on your computer
# (useful for files you accidentally committed)
git rm --cached filename.txt

# Rename/move a file
git mv old_name.txt new_name.txt
```

---

## 🌿 Branching & Merging

Branching is one of Git's most powerful features. It lets multiple people (or even just you) work on different things simultaneously.

### Creating Branches

```bash
# Create a new branch (stays on current branch)
git branch feature-login

# Create a new branch AND switch to it immediately
git checkout -b feature-login

# Modern alternative (Git 2.23+) — create and switch
git switch -c feature-login
```

### Listing Branches

```bash
# List local branches (* marks the current branch)
git branch

# List remote branches
git branch -r

# List all branches (local + remote)
git branch -a

# List branches with last commit info
git branch -v
```

### Switching Branches

```bash
# Switch to an existing branch
git checkout branch-name

# Modern alternative (Git 2.23+)
git switch branch-name
```

> **⚠️ Important:** Make sure your working directory is clean (no uncommitted changes) before switching branches, or stash your changes first (see [Stashing](#stashing)).

### Merging Branches

```bash
# First, switch to the branch you want to merge INTO
git checkout main

# Then merge the feature branch into it
git merge feature-login
```

> **What it does:** Combines the changes from `feature-login` into `main`.

#### Merge Conflicts

Sometimes Git can't automatically combine changes (e.g., two people edited the same line). When this happens:

1. Git marks the conflicting sections in the file:
   ```
   <<<<<<< HEAD
   Your changes on the current branch
   =======
   Changes from the branch being merged
   >>>>>>> feature-login
   ```
2. **Manually edit** the file to keep the correct code.
3. **Remove** the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
4. Stage and commit the resolved file:
   ```bash
   git add resolved-file.txt
   git commit -m "fix: resolve merge conflict in resolved-file.txt"
   ```

### Deleting Branches

```bash
# Delete a branch that has been merged
git branch -d feature-login

# Force delete a branch (even if unmerged) — USE WITH CAUTION
git branch -D feature-login

# Delete a remote branch
git push origin --delete feature-login
```

### Renaming Branches

```bash
# Rename the branch you're currently on
git branch -m new-name

# Rename a specific branch
git branch -m old-name new-name
```

---

## 🌐 Working with Remote Repositories

A **remote** is a version of your repository hosted somewhere else (like GitHub).

### Connecting to a Remote

```bash
# Add a remote repository (usually named "origin")
git remote add origin https://github.com/username/my-project.git
```

### Viewing Remotes

```bash
# List remote names
git remote

# List remotes with their URLs
git remote -v
```

### Pushing Changes

```bash
# Push to remote and set up tracking (first time)
git push -u origin main

# After tracking is set, just use:
git push

# Push a specific branch
git push origin feature-login

# Force push (DANGEROUS — overwrites remote history)
git push --force

# Safer force push (fails if someone else pushed first)
git push --force-with-lease
```

> **`-u` (or `--set-upstream`):** Creates a tracking link between your local branch and the remote branch so that future `git push` and `git pull` commands know where to push/pull from.

> **⚠️ WARNING:** Never `--force` push to shared branches like `main` unless you absolutely know what you're doing. Use `--force-with-lease` instead.

### Pulling Changes

```bash
# Fetch + merge changes from the remote
git pull origin main

# After tracking is set, just use:
git pull

# Pull with rebase instead of merge (cleaner history)
git pull --rebase
```

> **What it does:** Downloads changes from the remote repository and merges them into your local branch.

### Fetching Changes

```bash
# Download changes from remote WITHOUT merging
git fetch

# Fetch from a specific remote
git fetch origin

# Fetch and prune deleted remote branches
git fetch --prune
```

> **`fetch` vs `pull`:** `fetch` downloads updates but doesn't touch your working files. `pull` = `fetch` + `merge`. Use `fetch` when you want to review changes before merging.

### Managing Remote URLs

```bash
# Change the remote URL
git remote set-url origin https://new-url.git

# Add an additional push URL
git remote set-url --add --push origin https://mirror-url.git

# Remove a remote URL
git remote set-url --delete origin https://old-url.git

# Remove the entire remote
git remote remove origin
```

---

## ↩️ Undoing Changes

Mistakes happen. Git provides several ways to undo things safely.

### Unstaging Files

```bash
# Unstage a file (keeps changes in working directory)
git restore --staged filename.txt

# Older syntax (still works)
git reset HEAD filename.txt
```

### Discarding Changes in Working Directory

```bash
# Discard changes in a specific file (IRREVERSIBLE)
git restore filename.txt

# Discard ALL changes in working directory (IRREVERSIBLE)
git restore .

# Older syntax
git checkout -- filename.txt
```

> **⚠️ WARNING:** `git restore filename.txt` permanently deletes your uncommitted changes to that file. There is no undo.

### Amending the Last Commit

```bash
# Change the commit message of the last commit
git commit --amend -m "New corrected message"

# Add forgotten files to the last commit (without changing the message)
git add forgotten-file.txt
git commit --amend --no-edit
```

> **⚠️ Note:** Only amend commits that haven't been pushed yet. Amending pushed commits rewrites history and can cause problems for collaborators.

### Reverting a Commit

```bash
# Create a NEW commit that undoes a previous commit (safe for shared branches)
git revert <commit-hash>
```

> **What it does:** Doesn't delete history — it creates a new commit that reverses the changes. This is the **safest** way to undo changes on shared branches.

### Resetting (Moving HEAD)

```bash
# Soft reset — undo commit but keep changes staged
git reset --soft HEAD~1

# Mixed reset (default) — undo commit, unstage changes, keep files
git reset HEAD~1

# Hard reset — undo commit AND delete all changes (DANGEROUS)
git reset --hard HEAD~1
```

> **HEAD~1** means "one commit before HEAD." Use `HEAD~2` for two commits back, etc.

> **⚠️ WARNING:** `git reset --hard` permanently destroys uncommitted work. Use with extreme caution.

---

## ⚡ Advanced Commands

### Stashing

Temporarily save your uncommitted changes without committing them.

```bash
# Stash your current changes
git stash

# Stash with a descriptive message
git stash save "work in progress: login form"

# List all stashes
git stash list

# Apply the most recent stash (keeps it in the stash list)
git stash apply

# Apply AND remove the most recent stash
git stash pop

# Apply a specific stash
git stash apply stash@{2}

# Delete a specific stash
git stash drop stash@{0}

# Delete all stashes
git stash clear
```

> **When to use:** You're in the middle of work and need to quickly switch branches, but you're not ready to commit yet.

### Rebasing

Replay your commits on top of another branch for a cleaner, linear history.

```bash
# Rebase current branch onto main
git rebase main

# Interactive rebase — edit, squash, reorder, or drop commits
git rebase -i HEAD~3

# Abort a rebase in progress
git rebase --abort

# Continue after resolving conflicts during rebase
git rebase --continue
```

> **`merge` vs `rebase`:** Both integrate changes. `merge` preserves exact history (creates a merge commit). `rebase` rewrites history to be linear (cleaner, but never rebase shared/public branches).

#### Interactive Rebase Options

When you run `git rebase -i HEAD~3`, your editor opens with:

```
pick a1b2c3d First commit message
pick e4f5g6h Second commit message
pick i7j8k9l Third commit message
```

You can change `pick` to:
| Command   | What It Does |
|-----------|-------------|
| `pick`    | Keep the commit as-is |
| `reword`  | Keep the commit but edit the message |
| `squash`  | Combine with the previous commit (keep both messages) |
| `fixup`   | Combine with the previous commit (discard this message) |
| `drop`    | Delete the commit entirely |
| `edit`    | Pause to amend the commit |

### Cherry-Picking

Apply a specific commit from another branch to your current branch.

```bash
# Apply a single commit
git cherry-pick <commit-hash>

# Apply without committing (just stage the changes)
git cherry-pick --no-commit <commit-hash>
```

> **When to use:** You need a specific bug fix from another branch but don't want to merge the entire branch.

### Tagging

Mark specific points in history as important (e.g., releases).

```bash
# Create a lightweight tag
git tag v1.0.0

# Create an annotated tag (recommended — includes metadata)
git tag -a v1.0.0 -m "Release version 1.0.0"

# List all tags
git tag

# Push a specific tag to remote
git push origin v1.0.0

# Push all tags to remote
git push origin --tags

# Delete a local tag
git tag -d v1.0.0

# Delete a remote tag
git push origin --delete v1.0.0
```

### Git Bisect (Finding Bugs)

Use binary search to find which commit introduced a bug.

```bash
# Start bisecting
git bisect start

# Mark the current commit as bad (has the bug)
git bisect bad

# Mark a known good commit (didn't have the bug)
git bisect good <commit-hash>

# Git checks out a commit halfway between — test it, then:
git bisect good   # if this commit works fine
git bisect bad    # if this commit has the bug

# When done, reset to your original branch
git bisect reset
```

### Git Reflog (Safety Net)

View a log of everywhere `HEAD` has pointed — even after resets and rebases.

```bash
# View the reflog
git reflog

# Recover a "lost" commit
git checkout <reflog-hash>
```

> **When to use:** You accidentally ran `git reset --hard` and need to recover lost work. The reflog keeps a record of every change for ~90 days.

### Git Blame

See who last modified each line of a file.

```bash
# Show author and commit for each line
git blame filename.txt

# Blame a specific range of lines
git blame -L 10,20 filename.txt
```

### Git Clean

Remove untracked files from the working directory.

```bash
# Dry run — show what WOULD be removed
git clean -n

# Remove untracked files
git clean -f

# Remove untracked files AND directories
git clean -fd

# Remove ignored files too
git clean -fdx
```

> **⚠️ WARNING:** `git clean -f` permanently deletes files. Always run `git clean -n` first to preview.

### Git Worktree

Work on multiple branches simultaneously without stashing or switching.

```bash
# Create a worktree for another branch in a separate directory
git worktree add ../feature-branch feature-login

# List all worktrees
git worktree list

# Remove a worktree
git worktree remove ../feature-branch
```

---

## ✅ Git Best Practices

### Commits

| ✅ Do | ❌ Don't |
|-------|---------|
| Make small, focused commits | Make huge commits with unrelated changes |
| Write descriptive messages | Write vague messages like "fix" or "update" |
| Commit often | Wait days between commits |
| Use imperative mood: "Add feature" | Use past tense: "Added feature" |

### Branching

| ✅ Do | ❌ Don't |
|-------|---------|
| Use feature branches for new work | Commit directly to `main` |
| Use descriptive branch names: `feature/user-auth` | Use vague names: `test`, `branch1` |
| Delete branches after merging | Leave dozens of stale branches |
| Pull latest `main` before creating a branch | Branch off an outdated `main` |

### Branch Naming Conventions

```
feature/description     → feature/add-user-auth
bugfix/description      → bugfix/fix-login-crash
hotfix/description      → hotfix/patch-security-vuln
release/version         → release/v2.1.0
docs/description        → docs/update-api-guide
chore/description       → chore/update-dependencies
```

### Collaboration

| ✅ Do | ❌ Don't |
|-------|---------|
| Pull before you push | Push without checking for updates |
| Use Pull Requests for code review | Push directly to shared branches |
| Use `--force-with-lease` if you must force push | Use `--force` on shared branches |
| Communicate with your team about rebases | Silently rewrite shared history |

### The `.gitignore` File

Create a `.gitignore` file in your project root to tell Git which files to **not** track:

```gitignore
# Dependencies
node_modules/
vendor/

# Environment variables (NEVER commit secrets!)
.env
.env.local

# Build outputs
dist/
build/

# OS files
.DS_Store
Thumbs.db

# IDE settings
.vscode/
.idea/
*.swp
```

> **💡 Tip:** Use [gitignore.io](https://www.toptal.com/developers/gitignore) to generate `.gitignore` files for your tech stack.

> **⚠️ CRITICAL:** Never commit passwords, API keys, tokens, or other secrets. If you accidentally commit a secret, consider it compromised — rotate it immediately.

---

## 🔄 Common Workflows

### Solo Developer Workflow

```bash
# 1. Create or clone a repo
git init                              # or git clone <url>

# 2. Create a feature branch
git checkout -b feature/new-feature

# 3. Make changes, then stage and commit
git add .
git commit -m "feat: add new feature"

# 4. Switch to main and merge
git checkout main
git merge feature/new-feature

# 5. Push to remote
git push origin main

# 6. Clean up
git branch -d feature/new-feature
```

### Team Collaboration Workflow (GitHub Flow)

```bash
# 1. Pull latest main
git checkout main
git pull origin main

# 2. Create a feature branch
git checkout -b feature/user-profile

# 3. Work, commit, push
git add .
git commit -m "feat: add user profile page"
git push -u origin feature/user-profile

# 4. Open a Pull Request on GitHub for code review

# 5. After approval, merge the PR on GitHub

# 6. Locally, update main and clean up
git checkout main
git pull origin main
git branch -d feature/user-profile
```

### Forking Workflow (Open Source Contributions)

```bash
# 1. Fork the repository on GitHub (click "Fork" button)

# 2. Clone YOUR fork
git clone https://github.com/YOUR-USERNAME/project.git

# 3. Add the original repo as "upstream"
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git

# 4. Keep your fork updated
git fetch upstream
git checkout main
git merge upstream/main

# 5. Create a feature branch, make changes, push to YOUR fork
git checkout -b fix/typo-in-docs
git commit -am "fix: correct typo in README"
git push origin fix/typo-in-docs

# 6. Open a Pull Request from your fork to the original repo
```

---

## 📖 Glossary

| Term | Definition |
|------|-----------|
| **Repository (Repo)** | A folder tracked by Git, containing your project files and the entire history of changes |
| **Commit** | A snapshot of your project at a specific point in time |
| **Branch** | An independent line of development; a pointer to a specific commit |
| **HEAD** | A pointer to the current commit/branch you're working on |
| **Staging Area** | The "prep zone" where you place changes before committing |
| **Remote** | A version of your repository hosted on a server (e.g., GitHub) |
| **Origin** | The default name for your primary remote repository |
| **Upstream** | The original repository that a fork was created from |
| **Clone** | A local copy of a remote repository |
| **Fork** | A personal copy of someone else's repository on GitHub |
| **Pull Request (PR)** | A request to merge your branch's changes into another branch |
| **Merge** | Combining changes from one branch into another |
| **Rebase** | Re-applying commits on top of another branch for a linear history |
| **Stash** | Temporarily shelving uncommitted changes |
| **Tag** | A named reference to a specific commit (often used for releases) |
| **Conflict** | When Git can't automatically merge changes and needs human help |

---

## 📚 Resources

- 📘 [Official Git Documentation](https://git-scm.com/doc)
- 📙 [Pro Git Book (Free)](https://git-scm.com/book/en/v2)
- 🎮 [Learn Git Branching (Interactive)](https://learngitbranching.js.org/)
- 📝 [GitHub Docs](https://docs.github.com)
- 🔧 [Git Cheat Sheet (GitHub)](https://education.github.com/git-cheat-sheet-education.pdf)
- 🌐 [Oh Shit, Git!?!](https://ohshitgit.com/) — Fixes for common Git mistakes

---

## 🗺️ Quick Reference Cheat Sheet

```
SETUP                           BASICS                          BRANCHING
─────                           ──────                          ─────────
git init                        git status                      git branch <name>
git clone <url>                 git add <file>                  git checkout -b <name>
git config --global             git commit -m "msg"             git switch -c <name>
                                git log --oneline               git merge <branch>
                                git diff                        git branch -d <name>

REMOTE                          UNDO                            ADVANCED
──────                          ────                            ────────
git remote add origin <url>     git restore <file>              git stash
git push -u origin main         git restore --staged <file>     git rebase -i HEAD~3
git pull origin main            git commit --amend              git cherry-pick <hash>
git fetch                       git revert <hash>               git bisect start
git clone <url>                 git reset --hard HEAD~1         git reflog
```

---

<p align="center">
  <b>Happy coding! 🎉</b><br>
  <i>Star ⭐ this repo if you found it helpful!</i>
</p>
