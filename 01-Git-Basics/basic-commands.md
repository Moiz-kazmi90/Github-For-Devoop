# Basic Git Commands

This document covers the most commonly used Git commands.

---

# Initialize a Repository

Create a new Git repository.

```bash
git init
```

---

# Clone a Repository

Copy a remote repository to your local machine.

```bash
git clone repository-url
```

Example:

```bash
git clone https://github.com/username/project.git
```

---

# Check Repository Status

Shows modified, staged, and untracked files.

```bash
git status
```

---

# Add a Single File

```bash
git add filename
```

Example:

```bash
git add index.js
```

---

# Add All Files

```bash
git add .
```

---

# Commit Changes

Save staged changes.

```bash
git commit -m "Initial Commit"
```

---

# View Commit History

```bash
git log
```

Short version:

```bash
git log --oneline
```

---

# Show Branches

```bash
git branch
```

---

# Create a New Branch

```bash
git branch feature-login
```

---

# Switch Branch

```bash
git switch feature-login
```

or

```bash
git checkout feature-login
```

---

# Create and Switch Branch

```bash
git switch -c feature-login
```

---

# Merge Branch

```bash
git merge feature-login
```

---

# Add Remote Repository

```bash
git remote add origin repository-url
```

Example:

```bash
git remote add origin https://github.com/username/project.git
```

---

# Check Remote Repository

```bash
git remote -v
```

---

# Push Code

First Push:

```bash
git push -u origin main
```

Next Push:

```bash
git push
```

---

# Pull Latest Changes

```bash
git pull
```

or

```bash
git pull origin main
```

---

# Fetch Changes

Downloads changes without merging.

```bash
git fetch
```

---

# Check Differences

```bash
git diff
```

---

# Show Current Branch

```bash
git branch --show-current
```

---

# Remove Untracked Files

```bash
git clean -f
```

---

# Delete Branch

```bash
git branch -d feature-login
```

Force Delete:

```bash
git branch -D feature-login
```

---

# Rename Branch

```bash
git branch -m new-branch-name
```

---

# Summary

These commands form the foundation of daily Git usage, including repository creation, tracking changes, committing code, managing branches, and synchronizing with remote repositories.