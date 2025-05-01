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

### Stage

Staging is preparing files for a commit. It's like a preparation area for your changes.

```bash
# Stage a specific file
git add file.txt

# Stage all changes
git add .

# Stage all changes to tracked files
git add -u
```

### Commit

A commit is a snapshot of your changes at a specific point in time.

```bash
# Commit with a message
git commit -m "Add a descriptive message about your changes"

# Commit all tracked files (skipping staging)
git commit -am "Your commit message"
```

### Logs

View the history of commits:

```bash
# View commit history
git log

# View simplified log (one line per commit)
git log --oneline

# View graphical representation of commits
git log --graph --oneline
```

## Working with .gitignore

A `.gitignore` file specifies files that Git should ignore.

```bash
# Create a .gitignore file
touch .gitignore

# Example .gitignore content
node_modules/
*.log
.DS_Store
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
```

### Creating a New Branch

```bash
# Create a new branch
git branch branch-name

# Create and switch to new branch
git checkout -b branch-name
```

### Checkout a Branch

Switching to a different branch:

```bash
git checkout branch-name
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
```

### Delete a Branch

```bash
# Delete a branch (safe, will warn if unmerged changes)
git branch -d branch-name

# Force delete a branch (will delete even with unmerged changes)
git branch -D branch-name
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
```

### Comparing Between Branches

```bash
git diff branch1 branch2
```

### Comparing Specific Commits

```bash
git diff commit1 commit2
```

## Git Stash

Stashing lets you set aside changes temporarily without committing.

### Basic Stashing

```bash
# Stash your changes
git stash
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
```

### Tagging a Specific Commit

```bash
git tag -a v1.0.0 9fceb02 -m "Version 1.0.0"
```

### Delete a Tag

```bash
git tag -d v1.0.0
```

## Working with GitHub

### What is GitHub?

GitHub is a web-based hosting service for Git repositories. It provides a platform for collaboration and code sharing.

### Configure SSH Key and Add to GitHub

1. Generate an SSH key:
   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   ```

2. Copy the key to clipboard:
   ```bash
   # On macOS
   pbcopy < ~/.ssh/id_ed25519.pub
   
   # On Windows (via Git Bash)
   cat ~/.ssh/id_ed25519.pub | clip
   
   # On Linux
   xclip -sel clip < ~/.ssh/id_ed25519.pub
   ```

3. Add the key to your GitHub account:
   - Go to GitHub Settings > SSH and GPG keys
   - Click "New SSH key"
   - Paste your key and save

### Adding Code to Remote Repository

#### Add Remote Repository

```bash
git remote add origin git@github.com:username/repository.git
```

#### Push Code to Remote Repository

```bash
# Push to main branch
git push -u origin main
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
```

#### Pull Code

Fetches and merges changes:

```bash
git pull origin main
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

### Reviewing Pull Requests

When reviewing a PR:

1. Click on the "Files changed" tab to see code changes
2. Add comments on specific lines by hovering and clicking the "+" icon
3. Approve, request changes, or comment on the PR under "Review changes"

### Merging a Pull Request

Once a PR is approved:

1. Click the "Merge pull request" button
2. Choose a merge method:
   - Create a merge commit (preserves history)
   - Squash and merge (combines all commits)
   - Rebase and merge (creates a linear history)
3. Delete the branch after merging (optional)

### Addressing PR Feedback

When changes are requested:

1. Make the changes locally
2. Commit and push to the same branch
3. The PR will automatically update

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
    - uses: actions/checkout@v3
    
    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
        
    - name: Install dependencies
      run: npm ci
      
    - name: Run tests
      run: npm test
```

### Common GitHub Actions Use Cases

- **Automated testing**: Run tests when code is pushed
- **Code linting**: Check code style automatically
- **Building and publishing packages**: Automate releases
- **Deployments**: Deploy applications to different environments
- **Issue and PR management**: Automate labeling, closing, etc.

### Creating Your First GitHub Action

1. Create a `.github/workflows` directory in your repository
2. Add a YAML file (e.g., `main.yml`) with your workflow configuration
3. Commit and push to GitHub
4. View workflow results in the "Actions" tab of your repository

## Advanced Git Techniques

### Git Cherry-Pick

Apply specific commits from one branch to another:

```bash
git cherry-pick <commit-hash>
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

### Submodules and Subtrees

Include other Git repositories within your repository:

**Submodules**:
```bash
# Add a submodule
git submodule add https://github.com/username/repo.git path/to/submodule

# Initialize and update submodules after cloning
git submodule update --init --recursive
```

**Subtrees**:
```bash
# Add a subtree
git subtree add --prefix=path/to/subtree https://github.com/username/repo.git main --squash
```

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
# ...

# Stage and commit
git add .
git commit -m "Initial commit"

# Create repository on GitHub and push
git remote add origin git@github.com:username/my-project.git
git push -u origin main
```

### Example 2: Contributing to an Open Source Project

```bash
# Fork the repository on GitHub

# Clone your fork
git clone git@github.com:your-username/project.git
cd project

# Add original repository as upstream
git remote add upstream git@github.com:original-owner/project.git

# Create a feature branch
git checkout -b feature/awesome-feature

# Make changes and commit
git add .
git commit -m "Add awesome feature"

# Keep your branch updated with upstream
git pull upstream main
git push origin feature/awesome-feature

# Now create a pull request on GitHub
```

### Example 3: Managing a Release

```bash
# Create a release branch
git checkout -b release/1.0.0 develop

# Make any last-minute fixes
git commit -am "Fix bug #123"

# Merge to main
git checkout main
git merge --no-ff release/1.0.0
git tag -a v1.0.0 -m "Version 1.0.0"

# Merge back to develop
git checkout develop
git merge --no-ff release/1.0.0

# Delete release branch
git branch -d release/1.0.0

# Push everything
git push origin main develop --tags
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

# After editing, stage resolved files
git add resolved-file.txt

# Complete the merge
git commit

# Push the merged changes
git push origin main
```

## Git and GitHub Best Practices

### Commit Messages

Follow these guidelines for clear commit messages:

1. Use present tense ("Add feature" not "Added feature")
2. Be concise but descriptive
3. Reference issue numbers when applicable
4. Consider using conventional commits format:
   ```
   feat: add user authentication
   fix: resolve login page crash (#123)
   docs: update API documentation
   ```

### Repository Organization

Keep your repository clean and well-organized:

1. Use a meaningful `.gitignore` file
2. Include a descriptive README.md
3. Document your code and processes
4. Use GitHub issues for tracking work
5. Apply labels to categorize issues and PRs

### Security Considerations

1. Never commit sensitive information:
   - API keys or tokens
   - Passwords or credentials
   - Personal data
   
2. Use environment variables for secrets

3. Consider Git-secrets or similar tools to prevent accidental commits of sensitive data

## A Message for Beginners

Welcome to the world of Git and GitHub! 

Remember, everyone starts somewhere, and learning version control is a journey, not a race. Don't feel overwhelmed by all these commands and concepts—you don't need to memorize everything at once. Start with the basics: init, add, commit, push, and pull. As you grow more comfortable, gradually incorporate branches, merges, and other advanced features.

Making mistakes is part of the learning process. Git actually makes it safer to experiment because you can always go back to a previous state. Don't be afraid to try things out!

The Git community is vast and supportive. When you encounter challenges (and you will!), remember that countless developers have faced the same issues. Online resources, forums like Stack Overflow, and GitHub's own documentation are there to help you.

Keep this guide handy as a reference. Return to it whenever you need a refresher, and soon these commands will become second nature. Before you know it, you'll be branching, merging, and collaborating with confidence.

Happy coding, and may your commits always be meaningful!
