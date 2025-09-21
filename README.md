# Git & GitHub: A Beginner-Friendly Guide

## Introduction

Git is a version control system that helps track changes in code and enables collaboration among developers. GitHub is a web-based platform that allows developers to store and manage code using Git.

## Getting Started with Git

### Install Git

To install Git, download it from the official website:
- Visit [git-scm.com/downloads](https://git-scm.com/downloads)
- Follow the installation instructions for your operating system

### Check Your Git Version

After installation, verify Git is properly installed:

```bash
git --version
```

### Configure Your Settings

Set up your identity in Git (this information will be attached to your commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Configure your default branch name (modern standard):

```bash
git config --global init.defaultBranch main
```

Set your default editor (optional):

```bash
git config --global core.editor "code --wait"  # For VS Code
git config --global core.editor "nano"         # For nano
```

View your configuration settings:

```bash
git config --list
```

## Understanding Git Basics

### What is a Repository?

A repository (repo) is a storage space where your project lives. It contains all of your project's files and stores each file's revision history.

### Creating a Repository

To create a new Git repository:

```bash
# Navigate to your project folder
cd your-project-folder

# Initialize a new Git repository
git init
```

## The Git Workflow

### Complete Git Flow

The basic Git workflow follows these steps:
1. Make changes to files
2. Stage the changes
3. Commit the changes
4. Push to a remote repository (if working with GitHub)

### Working Directory, Staging Area, and Repository

Understanding the three areas in Git:
- **Working Directory**: Your local files where you make changes
- **Staging Area (Index)**: Files prepared for the next commit
- **Repository**: Committed snapshots of your project

### Stage

Staging is preparing files for a commit. It's like a preparation area for your changes.

```bash
# Stage a specific file
git add file.txt

# Stage all changes
git add .

# Stage all changes to tracked files
git add -u

# Remove file from staging area (unstage)
git reset HEAD file.txt
```

### Commit

A commit is a snapshot of your changes at a specific point in time.

```bash
# Commit with a message
git commit -m "Add a descriptive message about your changes"

# Commit all tracked files (skipping staging)
git commit -am "Your commit message"

# Amend the last commit (add changes or modify message)
git commit --amend -m "Updated commit message"
```

### Status and Logs

Check the status of your repository and view history:

```bash
# Check current status
git status

# View commit history
git log

# View simplified log (one line per commit)
git log --oneline

# View graphical representation of commits
git log --graph --oneline

# View changes in commits
git log -p

# View last n commits
git log -3
```

## Working with .gitignore

A `.gitignore` file specifies files that Git should ignore.

```bash
# Create a .gitignore file
touch .gitignore
```

Common .gitignore patterns:

```gitignore
# Dependencies
node_modules/
vendor/

# Build outputs
dist/
build/
*.exe
*.dll

# Environment files
.env
.env.local
.env.production

# IDE files
.vscode/
.idea/
*.swp
*.swo

# OS files
.DS_Store
Thumbs.db

# Logs
*.log
logs/

# Temporary files
*.tmp
*.temp
```

## Understanding Git Branches

### What are Branches?

Branches allow you to develop features, fix bugs, or experiment with new ideas in a contained area of your repository.

### HEAD in Git

HEAD is a reference to the current commit you're viewing. Think of it as the "current branch."

### List All Branches

```bash
# List local branches
git branch

# List all branches (local and remote)
git branch -a

# List remote branches only
git branch -r
```

### Creating a New Branch

```bash
# Create a new branch
git branch branch-name

# Create and switch to new branch
git checkout -b branch-name

# Modern way to create and switch (Git 2.23+)
git switch -c branch-name
```

### Checkout/Switch Branches

Switching to a different branch:

```bash
# Traditional way
git checkout branch-name

# Modern way (Git 2.23+)
git switch branch-name

# Switch to previous branch
git switch -
```

### Rename a Branch

```bash
# Rename current branch
git branch -m new-branch-name

# Rename specific branch
git branch -m old-branch-name new-branch-name
```

### Merging Branches

Combining changes from different branches:

```bash
# First checkout the target branch (where changes will go)
git checkout main

# Merge another branch into current branch
git merge branch-name

# Create a merge commit even for fast-forward merges
git merge --no-ff branch-name
```

### Delete a Branch

```bash
# Delete a branch (safe, will warn if unmerged changes)
git branch -d branch-name

# Force delete a branch (will delete even with unmerged changes)
git branch -D branch-name

# Delete remote branch
git push origin --delete branch-name
```

## Understanding Git Diff

Diff shows differences between commits, branches, or changes:

### How to Read the Diff

When you run a diff command, you'll see:
- Files being compared
- Chunks of changes, marked with `@@`
- Lines removed (prefixed with `-`)
- Lines added (prefixed with `+`)

### Comparing Working Directory and Staging Area

```bash
git diff
```

### Comparing Staging Area with Repository

```bash
git diff --staged
# or
git diff --cached
```

### Comparing Between Branches

```bash
git diff branch1 branch2
```

### Comparing Specific Commits

```bash
git diff commit1 commit2
```

### Show Changes for Specific Files

```bash
git diff filename.txt
git diff HEAD~1 filename.txt
```

## Undoing Changes in Git

### Undo Working Directory Changes

```bash
# Discard changes to a specific file
git checkout -- filename.txt

# Modern way (Git 2.23+)
git restore filename.txt

# Discard all changes in working directory
git checkout .
# or
git restore .
```

### Undo Staging Area Changes

```bash
# Unstage a file
git reset HEAD filename.txt

# Modern way
git restore --staged filename.txt

# Unstage all files
git reset HEAD
```

### Undo Commits

```bash
# Undo last commit but keep changes in working directory
git reset --soft HEAD~1

# Undo last commit and unstage changes
git reset HEAD~1

# Undo last commit and discard changes (dangerous!)
git reset --hard HEAD~1

# Create a new commit that undoes a previous commit
git revert commit-hash
```

## Git Stash

Stashing lets you set aside changes temporarily without committing.

### Basic Stashing

```bash
# Stash your changes
git stash

# Stash with a message
git stash push -m "Work in progress on feature X"
```

### Naming the Stash

```bash
git stash save "Description of the stashed changes"
```

### View the Stash List

```bash
git stash list
```

### Apply the Stash

```bash
# Apply most recent stash
git stash apply

# Apply specific stash
git stash apply stash@{n}
```

### Applying and Dropping the Stash

```bash
# Apply and then remove the stash
git stash pop
```

### Drop the Stash

```bash
# Remove the most recent stash
git stash drop

# Remove a specific stash
git stash drop stash@{n}
```

### Applying Stash to a Specific Branch

```bash
git checkout branch-name
git stash apply
```

### Clearing the Stash

```bash
git stash clear
```

### Stashing Untracked Files

```bash
# Stash including untracked files
git stash -u
```

## Git Tags

Tags are references to specific points in Git history, typically used for marking release versions.

### Creating a Tag

```bash
# Create a lightweight tag
git tag v1.0.0
```

### Create an Annotated Tag

```bash
git tag -a v1.0.0 -m "Version 1.0.0"
```

### List All Tags

```bash
git tag

# List tags with pattern
git tag -l "v1.*"
```

### View Tag Information

```bash
git show v1.0.0
```

### Tagging a Specific Commit

```bash
git tag -a v1.0.0 9fceb02 -m "Version 1.0.0"
```

### Delete a Tag

```bash
# Delete local tag
git tag -d v1.0.0

# Delete remote tag
git push origin --delete tag v1.0.0
```

## Working with GitHub

### What is GitHub?

GitHub is a web-based hosting service for Git repositories. It provides a platform for collaboration and code sharing.

### Configure SSH Key and Add to GitHub

1. Generate an SSH key:
   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   ```

2. Start the SSH agent and add your key:
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```

3. Copy the key to clipboard:
   ```bash
   # On macOS
   pbcopy < ~/.ssh/id_ed25519.pub
   
   # On Windows (via Git Bash)
   cat ~/.ssh/id_ed25519.pub | clip
   
   # On Linux
   xclip -sel clip < ~/.ssh/id_ed25519.pub
   ```

4. Add the key to your GitHub account:
   - Go to GitHub Settings > SSH and GPG keys
   - Click "New SSH key"
   - Paste your key and save

5. Test your connection:
   ```bash
   ssh -T git@github.com
   ```

### Personal Access Tokens (Alternative to SSH)

For HTTPS authentication:

1. Go to GitHub Settings > Developer settings > Personal access tokens > Tokens (classic)
2. Generate a new token with appropriate scopes
3. Use the token as your password when pushing/pulling

### Adding Code to Remote Repository

#### Add Remote Repository

```bash
git remote add origin git@github.com:username/repository.git

# For HTTPS
git remote add origin https://github.com/username/repository.git
```

#### View Remote Repositories

```bash
git remote -v
```

#### Push Code to Remote Repository

```bash
# Push to main branch (first time)
git push -u origin main

# Subsequent pushes
git push

# Push specific branch
git push origin branch-name

# Push all branches
git push --all origin
```

### Push Tags to Remote Repository

```bash
# Push a specific tag
git push origin v1.0.0

# Push all tags
git push origin --tags
```

### Delete Tag on Remote Repository

```bash
git push origin --delete v1.0.0
```

### Setup an Upstream Remote

When working with a forked repository:

```bash
git remote add upstream git@github.com:original-owner/repository.git
```

### Get Code from Remote Repository

#### Fetch Code

Downloads changes from remote without merging:

```bash
git fetch origin

# Fetch all remotes
git fetch --all
```

#### Pull Code

Fetches and merges changes:

```bash
git pull origin main

# Pull current branch from origin
git pull

# Pull with rebase instead of merge
git pull --rebase
```

#### Clone a Repository

```bash
# Clone via SSH
git clone git@github.com:username/repository.git

# Clone via HTTPS
git clone https://github.com/username/repository.git

# Clone to specific directory
git clone git@github.com:username/repository.git my-project

# Clone specific branch
git clone -b branch-name git@github.com:username/repository.git
```

## GitHub Features

### Issues

GitHub Issues help you track bugs, feature requests, and other tasks:

- Use descriptive titles
- Provide clear reproduction steps for bugs
- Use labels to categorize issues
- Reference issues in commits with "Fixes #123" or "Closes #123"

### GitHub CLI

Install and use GitHub CLI for command-line GitHub operations:

```bash
# Install GitHub CLI (gh)
# Visit: https://cli.github.com/

# Authenticate
gh auth login

# Create a repository
gh repo create my-project --public

# Clone your repositories
gh repo clone username/repository

# Create an issue
gh issue create --title "Bug report" --body "Description"

# Create a pull request
gh pr create --title "New feature" --body "Description"

# View pull requests
gh pr list

# Merge a pull request
gh pr merge 123
```

## Pull Requests

Pull Requests (PRs) are a way to propose changes, discuss modifications, and merge code into a repository.

### Creating a Pull Request

1. Push your branch to GitHub:
   ```bash
   git push origin your-branch-name
   ```

2. On GitHub, navigate to the repository and click "Pull requests" > "New pull request"

3. Select your branch as the "compare" branch and the target branch (usually main) as the "base" branch

4. Add a title and description explaining your changes

5. Click "Create pull request"

### Anatomy of a Good Pull Request

A good pull request includes:

- **Clear title**: Summarizes what the PR does
- **Detailed description**: Explains why the change is needed and how it works
- **Related issues**: Links to any related issues (e.g., "Fixes #123")
- **Screenshots/GIFs**: Visual demonstrations (if applicable)
- **Tests**: Evidence that the code has been tested
- **Checklist**: Tasks completed or to be completed

### Pull Request Template

Create a `.github/pull_request_template.md` file:

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Tests pass
- [ ] Manual testing completed

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Comments added to hard-to-understand areas
- [ ] Documentation updated
```

### Reviewing Pull Requests

When reviewing a PR:

1. Click on the "Files changed" tab to see code changes
2. Add comments on specific lines by hovering and clicking the "+" icon
3. Use suggestion feature to propose specific code changes
4. Approve, request changes, or comment on the PR under "Review changes"

### Merging a Pull Request

Once a PR is approved:

1. Click the "Merge pull request" button
2. Choose a merge method:
   - **Create a merge commit**: Preserves history with a merge commit
   - **Squash and merge**: Combines all commits into one
   - **Rebase and merge**: Creates a linear history without merge commit
3. Delete the branch after merging (recommended)

### Addressing PR Feedback

When changes are requested:

1. Make the changes locally
2. Commit and push to the same branch
3. The PR will automatically update

### Draft Pull Requests

Use draft PRs for work in progress:

```bash
gh pr create --draft --title "WIP: New feature"
```

## Git Workflows

Understanding common Git workflows helps teams collaborate effectively.

### GitHub Flow

A lightweight workflow ideal for small teams and continuous delivery:

1. Create a branch from main for your feature/fix
2. Make changes and commit to your branch
3. Open a pull request
4. Discuss and review the code
5. Deploy and test (optional)
6. Merge to main

### GitFlow

A more structured workflow for larger projects with scheduled releases:

1. **Main Branch**: Production-ready code
2. **Develop Branch**: Latest development changes
3. **Feature Branches**: New features, branched from develop
4. **Release Branches**: Preparing for a release
5. **Hotfix Branches**: Quick fixes for production

#### GitFlow Commands

```bash
# Initialize GitFlow (requires git-flow extension)
git flow init

# Start a new feature
git flow feature start feature-name

# Finish a feature
git flow feature finish feature-name

# Start a release
git flow release start 1.0.0

# Finish a release
git flow release finish 1.0.0
```

### Trunk-Based Development

A simpler alternative focused on small, frequent changes:

1. Most work happens directly on main (the "trunk")
2. Feature branches are very short-lived (1-2 days)
3. Frequent integration to main
4. Heavy use of feature flags to control functionality

### Forking Workflow

Common for open-source projects:

1. Fork the repository on GitHub
2. Clone your fork locally
3. Create feature branches in your fork
4. Push to your fork and create pull requests
5. Maintainers review and merge

## Git Rebasing

Rebasing is an alternative to merging that creates a cleaner, linear history.

### Basic Rebasing

```bash
# While on your feature branch
git rebase main
```

This takes your branch's commits, sets them aside, applies the main branch's commits, then reapplies your commits on top.

### Interactive Rebasing

Interactive rebasing allows you to modify commits:

```bash
# Rebase the last 3 commits
git rebase -i HEAD~3
```

This opens an editor where you can:
- `pick`: Keep the commit as is
- `reword`: Change the commit message
- `edit`: Amend the commit
- `squash`: Combine with previous commit
- `fixup`: Combine with previous commit, discard message
- `drop`: Remove the commit

### Rebase vs. Merge Conflicts

When conflicts occur during rebase:

```bash
# Fix conflicts in files, then
git add conflicted-file.txt

# Continue rebase
git rebase --continue

# Skip current commit
git rebase --skip

# Abort rebase and return to original state
git rebase --abort
```

### When to Use Rebase vs. Merge

**Use rebase when:**
- You want a clean, linear history
- Working on a feature branch that needs to incorporate main branch changes
- Cleaning up local commits before sharing

**Use merge when:**
- You want to preserve complete history
- The branch is public and others are basing work on it
- You want to create an explicit merge commit

### The Golden Rule of Rebasing

**Never rebase commits that have been pushed to a public repository** (unless you're the only one working on that branch).

## Git Hooks

Git hooks are scripts that run automatically when certain Git events occur.

### Types of Hooks

- **Pre-commit**: Runs before a commit is created
- **Prepare-commit-msg**: Runs before the commit message editor is launched
- **Commit-msg**: Validates commit messages
- **Post-commit**: Runs after a commit is created
- **Pre-push**: Runs before pushing to a remote
- **Pre-receive**: Runs on the remote when pushing
- **Post-receive**: Runs on the remote after a push completes

### Creating a Simple Git Hook

Git hooks are stored in the `.git/hooks` directory. To create a hook:

1. Navigate to your repository's hook directory:
   ```bash
   cd .git/hooks
   ```

2. Create a new file with the hook name (without extension):
   ```bash
   touch pre-commit
   chmod +x pre-commit
   ```

3. Edit the file with your script:
   ```bash
   #!/bin/sh
   # Example: Prevent committing to main branch
   branch=$(git symbolic-ref HEAD)
   if [ "$branch" = "refs/heads/main" ]; then
     echo "Direct commits to main branch are not allowed!"
     exit 1
   fi
   ```

### Common Hook Use Cases

- Enforce code style (run linters)
- Run tests before commits
- Validate commit messages (enforce conventional commits)
- Prevent committing to protected branches
- Automatically add issue numbers to commit messages

### Sharing Hooks with Your Team

Git hooks aren't copied when a repository is cloned. To share hooks:

1. Store hooks in a directory in your repository:
   ```
   project-root/
   ├── .git/
   └── git-hooks/
       └── pre-commit
   ```

2. Use tools like Husky or pre-commit to install and manage hooks from code

## GitHub Actions

GitHub Actions automates workflows directly in your GitHub repository.

### What are GitHub Actions?

GitHub Actions is a CI/CD (Continuous Integration/Continuous Deployment) platform that allows you to automate your build, test, and deployment pipeline.

### Workflow File Structure

GitHub Actions workflows are defined in YAML files stored in the `.github/workflows` directory:

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v4
    
    - name: Set up Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '20'
        cache: 'npm'
        
    - name: Install dependencies
      run: npm ci
      
    - name: Run linter
      run: npm run lint
      
    - name: Run tests
      run: npm test
      
    - name: Build
      run: npm run build
```

### Common GitHub Actions Use Cases

- **Automated testing**: Run tests when code is pushed
- **Code linting**: Check code style automatically
- **Building and publishing packages**: Automate releases
- **Deployments**: Deploy applications to different environments
- **Issue and PR management**: Automate labeling, closing, etc.
- **Security scanning**: Check for vulnerabilities

### Creating Your First GitHub Action

1. Create a `.github/workflows` directory in your repository
2. Add a YAML file (e.g., `main.yml`) with your workflow configuration
3. Commit and push to GitHub
4. View workflow results in the "Actions" tab of your repository

### Useful GitHub Actions

```yaml
# Auto-merge dependabot PRs
name: Auto-merge Dependabot PRs
on: pull_request
jobs:
  auto-merge:
    if: github.actor == 'dependabot[bot]'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: gh pr merge --auto --merge "$PR_URL"
        env:
          PR_URL: ${{github.event.pull_request.html_url}}
          GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
```

## Advanced Git Techniques

### Git Cherry-Pick

Apply specific commits from one branch to another:

```bash
# Cherry-pick a single commit
git cherry-pick <commit-hash>

# Cherry-pick multiple commits
git cherry-pick commit1 commit2 commit3

# Cherry-pick a range of commits
git cherry-pick commit1..commit5
```

### Git Bisect

Find which commit introduced a bug:

```bash
# Start bisect
git bisect start

# Mark current commit as bad
git bisect bad

# Mark a known good commit
git bisect good <commit-hash>

# Git will checkout commits for you to test
# After testing, mark each as good or bad
git bisect good
# or
git bisect bad

# When done, reset to your original state
git bisect reset
```

### Git Worktree

Work on multiple branches simultaneously without switching:

```bash
# Add a new worktree
git worktree add ../path-to-new-directory branch-name

# List worktrees
git worktree list

# Remove a worktree
git worktree remove ../path-to-directory
```

### Git Reflog

View a history of your HEAD movements:

```bash
# Show reflog
git reflog

# Show reflog for specific branch
git reflog show branch-name

# Recover "lost" commits
git reset --hard HEAD@{3}
```

### Submodules and Subtrees

Include other Git repositories within your repository:

**Submodules**:
```bash
# Add a submodule
git submodule add https://github.com/username/repo.git path/to/submodule

# Initialize and update submodules after cloning
git submodule update --init --recursive

# Update submodules
git submodule update --remote
```

**Subtrees**:
```bash
# Add a subtree
git subtree add --prefix=path/to/subtree https://github.com/username/repo.git main --squash

# Update subtree
git subtree pull --prefix=path/to/subtree https://github.com/username/repo.git main --squash
```

## Performance and Troubleshooting

### Large Repository Management

For large repositories:

```bash
# Clone with limited history
git clone --depth 1 https://github.com/username/repo.git

# Fetch more history later
git fetch --unshallow

# Use Git LFS for large files
git lfs install
git lfs track "*.psd"
git add .gitattributes
```

### Common Git Problems and Solutions

#### Uncommitted Changes Preventing Branch Switch

```bash
# Stash changes temporarily
git stash
git switch other-branch
git switch -
git stash pop
```

#### Accidentally Committed to Wrong Branch

```bash
# Move commits to new branch
git branch new-branch-name
git reset HEAD~3 --hard  # Remove last 3 commits from current branch
git switch new-branch-name
```

#### Reset Author Information

```bash
# Change author of last commit
git commit --amend --author="New Author <new@email.com>"

# Change author of multiple commits
git rebase -i HEAD~3
# Mark commits as 'edit', then for each:
git commit --amend --author="New Author <new@email.com>"
git rebase --continue
```

### Git Aliases

Create shortcuts for common commands:

```bash
# Set up useful aliases
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

## Security Best Practices

### Protecting Sensitive Information

1. **Never commit secrets**:
   ```gitignore
   # Add to .gitignore
   .env
   secrets.json
   *.key
   *.pem
   ```

2. **Use environment variables**:
   ```bash
   # Instead of hardcoding
   API_KEY=your-secret-key
   ```

3. **Use git-secrets or similar tools**:
   ```bash
   # Install git-secrets
   git secrets --install
   git secrets --register-aws
   ```

### GPG Commit Signing

Sign your commits for authenticity:

```bash
# Generate GPG key
gpg --gen-key

# List GPG keys
gpg --list-secret-keys --keyid-format LONG

# Configure Git to use GPG key
git config --global user.signingkey YOUR_KEY_ID
git config --global commit.gpgsign true

# Sign individual commit
git commit -S -m "Signed commit"
```

### Branch Protection Rules

On GitHub, set up branch protection:
- Require pull request reviews
- Dismiss stale reviews
- Require status checks
- Require branches to be up to date
- Restrict pushes to matching branches

## Practical Examples

### Example 1: Starting a New Project

```bash
# Initialize repository
mkdir my-project
cd my-project
git init

# Create initial files
touch README.md .gitignore

# Edit files with your content
echo "# My Project" > README.md
echo "node_modules/" > .gitignore

# Stage and commit
git add .
git commit -m "Initial commit: Add README and .gitignore"

# Create repository on GitHub using CLI
gh repo create my-project --public --source=. --remote=origin --push
```

### Example 2: Contributing to an Open Source Project

```bash
# Fork the repository on GitHub using CLI
gh repo fork original-owner/project --clone

# Navigate to cloned repository
cd project

# Add original repository as upstream
git remote add upstream git@github.com:original-owner/project.git

# Create a feature branch
git switch -c feature/awesome-feature

# Make changes and commit
git add .
git commit -m "feat: add awesome feature

- Implement feature X
- Add tests for feature X
- Update documentation"

# Keep your branch updated with upstream
git fetch upstream
git rebase upstream/main

# Push to your fork
git push origin feature/awesome-feature

# Create pull request using CLI
gh pr create --title "Add awesome feature" --body "This PR implements feature X to solve issue #123"
```

### Example 3: Managing a Release

```bash
# Create a release branch
git switch -c release/1.0.0 develop

# Make any last-minute fixes
git commit -am "fix: resolve critical bug #123"

# Merge to main
git switch main
git merge --no-ff release/1.0.0

# Create annotated tag
git tag -a v1.0.0 -m "Release version 1.0.0

- Add feature A
- Fix bug B
- Update dependencies"

# Merge back to develop
git switch develop
git merge --no-ff release/1.0.0

# Delete release branch
git branch -d release/1.0.0

# Push everything
git push origin main develop --tags

# Create GitHub release
gh release create v1.0.0 --title "Version 1.0.0" --notes "See CHANGELOG.md for details"
```

### Example 4: Resolving a Merge Conflict

When you encounter a merge conflict:

```bash
# Attempt merge
git merge feature-branch
# Conflict occurs!

# Check which files have conflicts
git status

# Open conflicted files and resolve manually
# Look for markers: <<<<<<< HEAD, =======, >>>>>>> feature-branch

# Example conflict resolution:
# <<<<<<< HEAD
# const version = "1.0.0";
# =======
# const version = "1.1.0";
# >>>>>>> feature-branch
# 
# Resolve to:
# const version = "1.1.0";

# After editing, stage resolved files
git add resolved-file.txt

# Complete the merge
git commit -m "Merge feature-branch, resolve version conflict"

# Push the merged changes
git push origin main
```

### Example 5: Hotfix Workflow

```bash
# Create hotfix branch from main
git switch main
git pull origin main
git switch -c hotfix/critical-bug-fix

# Make the fix
git commit -am "fix: resolve critical security vulnerability"

# Test the fix
npm test

# Merge to main
git switch main
git merge --no-ff hotfix/critical-bug-fix

# Create patch release tag
git tag -a v1.0.1 -m "Hotfix release 1.0.1"

# Merge to develop
git switch develop
git merge --no-ff hotfix/critical-bug-fix

# Clean up
git branch -d hotfix/critical-bug-fix
git push origin main develop --tags
```

## Git and GitHub Best Practices

### Commit Messages

Follow these guidelines for clear commit messages:

1. **Use Conventional Commits format**:
   ```
   feat: add user authentication system
   fix: resolve login page crash on mobile (#123)
   docs: update API documentation
   style: format code with prettier
   refactor: extract user service logic
   test: add unit tests for authentication
   chore: update dependencies
   ```

2. **Structure your commit message**:
   ```
   type(scope): brief description (50 chars max)
   
   More detailed explanation if needed, wrapped at 72 characters.
   Explain what and why, not how.
   
   - List changes made
   - Reference issues closed
   
   Closes #123
   Fixes #456
   ```

### Repository Organization

Keep your repository clean and well-organized:

1. **Use a meaningful `.gitignore` file**
2. **Include a comprehensive README.md**:
   ```markdown
   # Project Name
   
   Brief description of what your project does.
   
   ## Installation
   
   ```bash
   git clone https://github.com/username/project.git
   cd project
   npm install
   ```
   
   ## Usage
   
   How to use your project with examples.
   
   ## Contributing
   
   Guidelines for contributors.
   
   ## License
   
   License information.
   ```

3. **Document your code and processes**
4. **Use GitHub issues for tracking work**
5. **Apply labels to categorize issues and PRs**
6. **Create templates for issues and PRs**
7. **Use semantic versioning for releases**
8. **Maintain a CHANGELOG.md file**

### Branch Naming Conventions

Use consistent branch naming:

```bash
# Feature branches
feature/user-authentication
feature/payment-integration

# Bug fix branches
bugfix/login-error
fix/memory-leak

# Hotfix branches
hotfix/security-patch
hotfix/critical-bug

# Release branches
release/v1.2.0
release/2024-q1

# Experimental branches
experiment/new-architecture
spike/performance-test
```

### Security Considerations

1. **Never commit sensitive information**:
   - API keys or tokens
   - Passwords or credentials
   - Personal data
   - Database connection strings
   
2. **Use environment variables for secrets**:
   ```bash
   # .env file (add to .gitignore)
   DATABASE_URL=postgresql://localhost:5432/mydb
   API_KEY=your-secret-key
   JWT_SECRET=your-jwt-secret
   ```

3. **Enable two-factor authentication on GitHub**

4. **Use Git-secrets or similar tools to prevent accidental commits of sensitive data**

5. **Regularly audit repository access and permissions**

6. **Sign commits with GPG for authenticity**

### Code Review Best Practices

When reviewing pull requests:

1. **Be constructive and respectful**
2. **Focus on the code, not the person**
3. **Provide specific, actionable feedback**
4. **Suggest improvements rather than just pointing out problems**
5. **Test the changes locally when possible**
6. **Check for security vulnerabilities**
7. **Ensure documentation is updated**

Example good review comments:
```
✅ "Consider extracting this logic into a separate function for better readability"
✅ "This could cause a memory leak if the component unmounts. Try using useEffect cleanup"
✅ "Great improvement! The new algorithm is much more efficient"

❌ "This is wrong"
❌ "Bad code"
❌ "I don't like this approach"
```

## Git Configuration Tips

### Global Configuration

Set up useful global configurations:

```bash
# Better diff output
git config --global diff.tool vimdiff

# Auto-correct typos
git config --global help.autocorrect 1

# Better merge conflict resolution
git config --global merge.conflictstyle diff3

# Automatically prune remote branches
git config --global fetch.prune true

# Use modern push behavior
git config --global push.default simple

# Store credentials (use with caution)
git config --global credential.helper cache

# Better log formatting
git config --global format.pretty format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)'
```

### Repository-Specific Configuration

For specific repositories:

```bash
# Use different email for work repositories
git config user.email work@company.com

# Set up different merge strategies
git config merge.ours.driver true
```

## Debugging and Troubleshooting

### Common Error Messages and Solutions

1. **"fatal: not a git repository"**
   ```bash
   # You're not in a Git repository
   git init  # or navigate to correct directory
   ```

2. **"Your branch is ahead of 'origin/main' by X commits"**
   ```bash
   git push origin main
   ```

3. **"Please commit your changes or stash them before you switch branches"**
   ```bash
   git stash
   git switch other-branch
   # Later: git switch - && git stash pop
   ```

4. **"Merge conflict in file.txt"**
   ```bash
   # Edit the conflicted file, then:
   git add file.txt
   git commit
   ```

5. **"Permission denied (publickey)"**
   ```bash
   # Check SSH key setup
   ssh -T git@github.com
   # May need to add SSH key to GitHub account
   ```

### Git Forensics

Investigate repository history:

```bash
# Find when a line was changed
git blame filename.txt

# Search commit messages
git log --grep="bug fix"

# Find commits that changed a specific function
git log -L :function_name:filename.js

# Show commits touching specific file
git log --follow filename.txt

# Find commits by author
git log --author="John Doe"

# Find large files in history
git rev-list --objects --all | git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' | grep '^blob' | sort -k3nr | head
```

### Performance Optimization

For large repositories:

```bash
# Clean up unnecessary files and optimize
git gc --aggressive --prune=now

# Reduce repository size
git filter-branch --tree-filter 'rm -rf path/to/large/files' HEAD

# Use shallow clones for CI/CD
git clone --depth 1 --single-branch --branch main https://github.com/user/repo.git

# Configure sparse-checkout for large repositories
git config core.sparseCheckout true
echo "src/*" > .git/info/sparse-checkout
git read-tree -m -u HEAD
```

## Modern Git Features

### Git Worktrees for Parallel Development

```bash
# Create a new worktree for a feature
git worktree add -b feature/new-ui ../my-project-new-ui

# Work on main and feature simultaneously
cd ../my-project-new-ui
# Make changes...

# Back to main project
cd ../my-project
git worktree list

# Remove worktree when done
git worktree remove ../my-project-new-ui
```

### Git Maintenance Commands

Keep your repository healthy:

```bash
# Run maintenance tasks
git maintenance start  # Enable background maintenance

# Manual maintenance
git maintenance run --task=gc
git maintenance run --task=commit-graph
git maintenance run --task=prefetch
```

### Partial Clone and Sparse Checkout

For very large repositories:

```bash
# Partial clone (Git 2.19+)
git clone --filter=blob:none https://github.com/large/repo.git

# Sparse checkout
git sparse-checkout init --cone
git sparse-checkout set src tests docs
```

## Continuous Integration Integration

### GitHub Actions for Git Workflows

```yaml
name: Git Workflow Validation

on:
  pull_request:
    branches: [main]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
      with:
        fetch-depth: 0
    
    - name: Validate commit messages
      run: |
        git log --oneline origin/main..HEAD | while read commit; do
          if ! echo "$commit" | grep -qE "^[a-f0-9]+ (feat|fix|docs|style|refactor|test|chore)(\(.+\))?: .+"; then
            echo "Invalid commit message: $commit"
            exit 1
          fi
        done
    
    - name: Check for merge commits
      run: |
        if git log --oneline origin/main..HEAD --merges | grep -q .; then
          echo "Merge commits not allowed in pull requests"
          exit 1
        fi
    
    - name: Validate branch naming
      run: |
        branch_name="${{ github.head_ref }}"
        if ! echo "$branch_name" | grep -qE "^(feature|bugfix|hotfix|release)/[a-z0-9-]+$"; then
          echo "Invalid branch name: $branch_name"
          echo "Use format: type/description (e.g., feature/user-auth)"
          exit 1
        fi
```

### Pre-commit Hooks with GitHub Actions

```yaml
name: Pre-commit Hooks

on: [push, pull_request]

jobs:
  pre-commit:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-python@v4
      with:
        python-version: '3.x'
    - uses: pre-commit/action@v3.0.0
```

## Team Collaboration Strategies

### Feature Flags with Git

Use feature flags to deploy incomplete features:

```javascript
// Example feature flag implementation
const features = {
  newDashboard: process.env.FEATURE_NEW_DASHBOARD === 'true',
  betaPayments: process.env.FEATURE_BETA_PAYMENTS === 'true'
};

// In your code
if (features.newDashboard) {
  return <NewDashboard />;
}
return <LegacyDashboard />;
```

### Code Owners

Create a `.github/CODEOWNERS` file:

```
# Global owners
* @team-leads

# Frontend code
/frontend/ @frontend-team

# Backend code
/backend/ @backend-team

# DevOps and CI
/.github/ @devops-team
/docker/ @devops-team

# Documentation
/docs/ @tech-writers
*.md @tech-writers
```

### Issue and PR Templates

Create issue templates in `.github/ISSUE_TEMPLATE/`:

```markdown
---
name: Bug Report
about: Create a report to help us improve
title: '[BUG] '
labels: bug
assignees: ''
---

## Bug Description
A clear and concise description of what the bug is.

## Steps to Reproduce
1. Go to '...'
2. Click on '....'
3. Scroll down to '....'
4. See error

## Expected Behavior
A clear and concise description of what you expected to happen.

## Screenshots
If applicable, add screenshots to help explain your problem.

## Environment
- OS: [e.g. iOS]
- Browser: [e.g. chrome, safari]
- Version: [e.g. 22]

## Additional Context
Add any other context about the problem here.
```

### Release Management

Automate releases with GitHub Actions:

```yaml
name: Release

on:
  push:
    tags:
      - 'v*'

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
      with:
        fetch-depth: 0
    
    - name: Generate changelog
      id: changelog
      run: |
        # Generate changelog from commit messages
        git log --pretty=format:"- %s" $(git describe --tags --abbrev=0 HEAD^)..HEAD > CHANGELOG_TEMP.md
        echo "changelog<<EOF" >> $GITHUB_OUTPUT
        cat CHANGELOG_TEMP.md >> $GITHUB_OUTPUT
        echo "EOF" >> $GITHUB_OUTPUT
    
    - name: Create Release
      uses: actions/create-release@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        tag_name: ${{ github.ref }}
        release_name: Release ${{ github.ref }}
        body: ${{ steps.changelog.outputs.changelog }}
        draft: false
        prerelease: false
```

## A Message for Beginners

Welcome to the world of Git and GitHub! 

Remember, everyone starts somewhere, and learning version control is a journey, not a race. Don't feel overwhelmed by all these commands and concepts—you don't need to memorize everything at once. Start with the basics: init, add, commit, push, and pull. As you grow more comfortable, gradually incorporate branches, merges, and other advanced features.

Making mistakes is part of the learning process. Git actually makes it safer to experiment because you can always go back to a previous state. Don't be afraid to try things out!

Here's a suggested learning path:

### Week 1: Git Basics
- Install and configure Git
- Learn `git init`, `git add`, `git commit`
- Understand working directory, staging area, and repository
- Practice with local repositories

### Week 2: Remote Repositories
- Create GitHub account and set up SSH keys
- Learn `git clone`, `git push`, `git pull`
- Create your first repository on GitHub
- Practice pushing local work to GitHub

### Week 3: Branching and Merging
- Understand branches with `git branch`, `git checkout`/`git switch`
- Learn basic merging with `git merge`
- Practice creating feature branches
- Handle simple merge conflicts

### Week 4: Collaboration
- Fork repositories and create pull requests
- Learn to review code and provide feedback
- Understand GitHub Flow workflow
- Practice collaborating on open source projects

### Month 2: Advanced Features
- Learn rebasing and when to use it
- Explore stashing, cherry-picking, and tags
- Set up Git hooks and GitHub Actions
- Master conflict resolution and debugging

### Ongoing: Best Practices
- Develop good commit message habits
- Learn to read Git history and logs
- Understand different workflow strategies
- Keep practicing and helping others

The Git community is vast and supportive. When you encounter challenges (and you will!), remember that countless developers have faced the same issues. Online resources, forums like Stack Overflow, and GitHub's own documentation are there to help you.

Keep this guide handy as a reference. Return to it whenever you need a refresher, and soon these commands will become second nature. Before you know it, you'll be branching, merging, and collaborating with confidence.

Don't just read about Git—practice it! Create repositories, make commits, experiment with branches. The more you use Git, the more intuitive it becomes.

Most importantly, don't be afraid to make mistakes. Git's power lies in its ability to track and recover from changes. Every mistake is a learning opportunity, and with Git, you can always go back and try again.

Happy coding, and may your commits always be meaningful and your merges conflict-free!

## Quick Reference

### Essential Commands

```bash
# Repository setup
git init
git clone <url>

# Basic workflow
git status
git add <file>
git commit -m "message"
git push origin main
git pull origin main

# Branching
git branch <name>
git switch <branch>
git switch -c <new-branch>
git merge <branch>

# Viewing history
git log
git log --oneline
git diff

# Undoing changes
git restore <file>
git reset HEAD~1
git revert <commit>

# Stashing
git stash
git stash pop

# Remote repositories
git remote add origin <url>
git fetch origin
git push -u origin main
```

### Useful Aliases

Add these to your `.gitconfig`:

```ini
[alias]
    co = checkout
    sw = switch
    br = branch
    ci = commit
    st = status
    unstage = reset HEAD --
    last = log -1 HEAD
    visual = !gitk
    lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
    undo = reset --soft HEAD~1
    amend = commit --amend --no-edit
    pushf = push --force-with-lease
    aliases = config --get-regexp alias
```

Remember: Git is a tool that grows with you. Start simple, practice regularly, and gradually incorporate more advanced features as you become comfortable. The most important thing is to start using it consistently in your projects.
