# Git Pull (`git-pull.md`)

# What is `git pull`?

`git pull` is a Git command used to **download the latest changes from a remote repository and update your current local branch.**

It is one of the most frequently used Git commands when working in a team.

**Simple Definition**

> **`git pull` downloads new commits from a remote repository and merges them into your current local branch.**

---

# Why do we use `git pull`?

Imagine two developers are working on the same project.

Developer A pushes new code to GitHub.

Developer B still has the old version.

Before Developer B starts working, they should run:

```bash
git pull
```

This downloads the latest changes and updates the local repository.

---

# Why was Git Pull introduced?

Without `git pull`:

* Developers would work on outdated code.
* Team members would overwrite each other's changes.
* Merge conflicts would become more common.
* Everyone would have different versions of the project.

`git pull` helps every developer stay up to date.

---

# How does Git Pull Work?

`git pull` is actually **two Git commands combined**.

```text
git pull

↓

git fetch

↓

git merge
```

It first downloads new commits from the remote repository.

Then it merges those commits into your current branch.

---

# Syntax

```bash
git pull
```

or

```bash
git pull origin main
```

---

# Basic Example

Current Local Repository

```text
A ---- B ---- C (main)
```

Remote Repository (GitHub)

```text
A ---- B ---- C ---- D ---- E (main)
```

Run:

```bash
git pull
```

Result:

```text
A ---- B ---- C ---- D ---- E (main)
```

Now your local repository is updated.

---

# Pull From a Specific Branch

```bash
git pull origin main
```

Meaning:

* Download changes from `origin`
* Update the `main` branch

---

# Pull From Another Branch

```bash
git pull origin develop
```

---

# Git Pull Workflow

```text
Developer A

↓

git push

↓

GitHub Updated

↓

Developer B

↓

git pull

↓

Local Repository Updated
```

---

# What Happens Internally?

When you run:

```bash
git pull
```

Git performs:

### Step 1

Downloads new commits from the remote repository.

```bash
git fetch
```

### Step 2

Merges them into the current branch.

```bash
git merge
```

---

# Git Pull vs Git Fetch

| Git Pull                  | Git Fetch                             |
| ------------------------- | ------------------------------------- |
| Downloads changes         | Downloads changes                     |
| Automatically merges      | Does not merge                        |
| Updates working directory | Updates only remote tracking branches |
| Easier for beginners      | Safer for reviewing changes           |

---

# Git Pull vs Git Clone

| Git Pull                    | Git Clone                               |
| --------------------------- | --------------------------------------- |
| Updates existing repository | Downloads repository for the first time |
| Used regularly              | Used only once                          |

---

# Git Pull vs Git Push

| Git Pull          | Git Push        |
| ----------------- | --------------- |
| Downloads changes | Uploads changes |
| Remote → Local    | Local → Remote  |

---

# Git Pull vs Git Merge

| Git Pull                   | Git Merge     |
| -------------------------- | ------------- |
| Fetch + Merge              | Only merges   |
| Contacts remote repository | Works locally |

---

# Common Commands

Pull latest changes

```bash
git pull
```

---

Pull from main

```bash
git pull origin main
```

---

Pull from develop

```bash
git pull origin develop
```

---

# Real-World Example

Developer A

```bash
git add .
git commit -m "Login feature"
git push origin main
```

Developer B

```bash
git pull origin main
```

Now Developer B has the login feature.

---

# Merge Conflict During Pull

Sometimes both developers edit the same file.

Developer A

```javascript
const PORT = 3000;
```

Developer B

```javascript
const PORT = 5000;
```

Developer B runs:

```bash
git pull
```

Git reports:

```text
CONFLICT (content): Merge conflict
```

You must:

1. Open the conflicted file.
2. Remove conflict markers.
3. Keep the correct code.
4. Save the file.
5. Stage the file.
6. Commit the merge.

---

# Pull With Rebase

Instead of merging:

```bash
git pull --rebase
```

Git first downloads new commits and then places your local commits on top of the latest remote commits.

History becomes cleaner.

---

# When Should You Use Git Pull?

Use it:

* Before starting work.
* Before pushing changes.
* Before creating a Pull Request.
* Before merging branches.
* Whenever teammates push new commits.

---

# When Should You Avoid Git Pull?

Avoid using `git pull` if:

* You want to review remote changes first.
* You prefer using:

```bash
git fetch
```

followed by

```bash
git merge
```

---

# Common Errors

## Error

```text
Your local changes would be overwritten by merge.
```

Reason:

You have uncommitted changes.

Solution:

```bash
git add .
git commit -m "Save work"
```

or

```bash
git stash
```

Then run:

```bash
git pull
```

---

## Error

```text
CONFLICT (content)
```

Reason:

Both local and remote changed the same code.

Solution:

Resolve the conflict manually.

---

## Error

```text
fatal: not a git repository
```

Reason:

You are not inside a Git repository.

Solution:

Move into the project folder.

```bash
cd project-folder
```

---

## Error

```text
There is no tracking information for the current branch.
```

Solution:

```bash
git pull origin main
```

or set an upstream branch.

---

# Best Practices

* Pull before starting work.
* Commit or stash local changes before pulling.
* Pull frequently in team projects.
* Resolve conflicts carefully.
* Test the project after every pull.

---

# Advantages

* Keeps your project updated.
* Reduces conflicts.
* Easy to use.
* Improves team collaboration.
* Combines fetch and merge into one command.

---

# Disadvantages

* May create merge conflicts.
* Can accidentally merge unwanted changes.
* Beginners may not realize it performs two operations.

---

# Quick Revision

Pull latest changes

```bash
git pull
```

---

Pull from main

```bash
git pull origin main
```

---

Pull with rebase

```bash
git pull --rebase
```

---

Download only

```bash
git fetch
```

---

Remember

```text
git pull

=

git fetch

+

git merge
```

---

# Interview Questions

### Q1. What is `git pull`?

**Answer:**

`git pull` downloads the latest changes from a remote repository and merges them into the current local branch.

---

### Q2. What two commands does `git pull` perform?

**Answer:**

```text
git fetch

+

git merge
```

---

### Q3. What is the difference between `git pull` and `git fetch`?

**Answer:**

`git fetch` only downloads changes, while `git pull` downloads and merges them.

---

### Q4. When should you use `git pull`?

**Answer:**

Before starting work, before pushing changes, and whenever you need the latest updates from teammates.

---

### Q5. What causes merge conflicts during `git pull`?

**Answer:**

When the same part of a file has been modified both locally and remotely.

---

### Q6. What does `git pull --rebase` do?

**Answer:**

It downloads remote changes and reapplies your local commits on top of them, creating a cleaner history.

---

# Interview Scenarios

### Scenario 1

Your teammate pushed new commits to GitHub.

What should you do before writing new code?

```bash
git pull
```

---

### Scenario 2

You have uncommitted changes and `git pull` fails.

What are your options?

```bash
git add .
git commit -m "Save work"
```

or

```bash
git stash
git pull
git stash pop
```

---

### Scenario 3

You want to see remote changes before merging them.

Which command should you use?

```bash
git fetch
```

Then review the changes before merging.

---

# One-Line Interview Definition

> **`git pull` is a Git command that updates the current local branch by downloading the latest changes from a remote repository and merging them automatically.**
