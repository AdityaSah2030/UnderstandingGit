# 🚀 Git & GitHub: A Complete Guide

## 🧐 What is Git?
Git is a **version control system** that helps in tracking changes in code and enables **collaboration** among developers.

## 🌍 What is GitHub?
GitHub is a **web-based platform** that allows developers to **store and manage code using Git**.

## 🗂️ Key Terminology
- **📂 Folder = 📦 Repository = 🏗️ Directory**

---

# 🏁 Getting Started with Git & GitHub

## 📌 1. Setting Up Your Environment
### 🌟 Check if Git is Installed
```sh
git --version  # Check installed Git version
```
### 🔹 Install Git (If not installed)
[Download Git](https://git-scm.com/downloads)

---

## 📌 2. Basic Commands

### 🏗️ Navigating the File System
```sh
ls          # 📜 List all files
ls -a       # 📜 List all files, including hidden ones
cd <dir>    # 🚪 Change directory
cd ..       # 🔙 Move up one directory level
mkdir <dir> # 🏗️ Create a new directory
```

### 🆕 Initializing a Repository
```sh
git init                        # 🔧 Initialize a new Git repository
git remote add origin <URL>     # 🔗 Add remote repository link
git remote -v                   # 🔍 Verify remote repository
git branch                      # 🌿 Check available branches
git branch -M main              # 🔄 Rename branch to 'main'
```

### 📥 Cloning a Repository
```sh
git clone <repo-link>  # 📩 Clone a remote repository
```

---

# 🚦 Git Workflow

## 📌 3. Understanding File Status
- 🟢 **Unmodified**: No changes made
- 🟡 **Modified**: Changes are made to existing files
- 🔴 **Untracked**: Newly added file
- 🔵 **Staged**: File ready to be committed

```sh
git status                # 🔍 Check status of files
git add <file>            # ➕ Stage a specific file
git add .                 # ➕ Stage all files
git commit -m "message"  # 📝 Commit staged files with a message
```

## 📤 4. Pushing Changes
```sh
git push origin main  # 🚀 Push local changes to the remote repository
```

## 📥 5. Pulling Changes
```sh
git pull origin main  # 🔄 Fetch and merge changes from remote repository
```

---

# 🌿 Branching & Merging

## 📌 6. Working with Branches
```sh
git branch                # 🌿 List all branches
git checkout <branch>     # 🔀 Switch to a branch
git checkout -b <branch>  # ➕ Create and switch to a new branch
git branch -d <branch>    # ❌ Delete a branch
```

## 🔄 7. Merging Branches
### 🏗️ Method 1: Using Git Commands
```sh
git diff <branch>    # 🔍 Compare changes between branches
git merge <branch>   # 🔀 Merge specified branch into current branch
```

### 🔗 Method 2: Using GitHub Pull Requests (PR)
1. 📤 Push branch to GitHub.
2. 🔗 Open GitHub repository.
3. 📜 Create a Pull Request (PR).
4. ✅ Review and merge.

---

# ⚠️ Handling Merge Conflicts
- 🛠️ When Git can't automatically merge changes, **manually resolve** conflicts in VS Code or another text editor.
- After resolving:
```sh
git add .
git commit -m "Resolved merge conflicts"
```

---

# 🔄 Undoing Changes

## ⏪ Undo Staged Changes
```sh
git reset <file>  # ⏪ Unstage a specific file
git reset         # ⏪ Unstage all files
```

## 🔙 Undo Committed Changes
```sh
git reset HEAD~1           # 🔄 Undo the last commit but keep changes
```

## 🕒 Undo Multiple Commits
```sh
git reset <commit-hash>       # ⏳ Reset to specific commit but keep changes
git reset --hard <commit-hash> # 🚨 Reset to specific commit and remove changes
```

---

# 🍴 Forking a Repository
Forking allows you to create a **copy** of someone else's repository in your GitHub account.

### 🔹 Steps to Fork:
1. 🔗 Go to the GitHub repository.
2. 🔀 Click **Fork** in the top-right corner.
3. 📩 Clone it using `git clone <forked-repo-url>`.
4. ✍️ Make changes and push them.

---

# 🔥 Additional Important Commands
```sh
git log                  # 📜 View commit history
git remote -v            # 🔗 View remote repositories
git fetch                # 📥 Download changes from remote repo without merging
git stash                # 🗄️ Temporarily store changes
git stash pop            # 🔄 Apply stashed changes
git rebase <branch>      # 🔀 Reapply commits on top of another base branch
git cherry-pick <commit> # 🍒 Apply specific commit from one branch to another
```

---

# 💻 GitHub Desktop
If you face issues using Git commands, you can use **GitHub Desktop**, a GUI tool that simplifies Git operations.

### 🔹 Installing GitHub Desktop
[Download GitHub Desktop](https://desktop.github.com/)

### 🔹 Basic GitHub Desktop Workflow
1. **Clone a Repository**: Click **File → Clone Repository**.
2. **Make Changes**: Edit files in your preferred code editor.
3. **Commit Changes**: Write a commit message and click **Commit to main**.
4. **Push Changes**: Click **Push Origin** to upload changes to GitHub.
5. **Pull Updates**: Click **Fetch Origin** to sync with the latest remote changes.

---

# 💻 Codespaces
GitHub Codespaces provides a **cloud-based development environment** to work on projects directly from GitHub.

---

# 🔄 Summary of Git Workflow
**GitHub Repo → Clone → Changes → Add → Commit → Push**

This README serves as a **quick reference** to essential Git & GitHub commands, ensuring an easy learning experience for beginners and professionals alike. 🚀

