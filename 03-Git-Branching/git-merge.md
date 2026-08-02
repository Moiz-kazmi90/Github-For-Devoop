# Git Merge (`git-merge.md`)

# What is `git merge`?

`git merge` is a Git command used to **combine the changes from one branch into another branch**.

It is one of the most important Git commands because it brings completed work from feature branches into the main project.

**Simple Definition**

> **`git merge` combines the history and changes of one branch into another branch.**

---

# Why do we use Git Merge?

Imagine your project has these branches:

```text
main
feature-login
feature-payment
bugfix-navbar
```

Each developer works on a separate branch.

When a feature is completed and tested, it needs to become part of the main project.

For this, we use:

```bash
git merge
```

---

# Why was Git Merge introduced?

Git encourages developers to work on separate branches.

Without merging:

* New features would never reach the main project.
* Bug fixes would stay in their own branches.
* Team collaboration would be difficult.

Git Merge combines different branches into one project.

---

# Real-Life Example

Suppose five developers are working on one website.

Developer A

```text
feature-login
```

Developer B

```text
feature-payment
```

Developer C

```text
feature-search
```

Developer D

```text
feature-profile
```

Developer E

```text
bugfix-navbar
```

After testing, every branch is merged into:

```text
main
```

---

# How Git Merge Works

Initial history:

```text
A ---- B ---- C (main)
```

Create a new branch.

```bash
git switch -c feature-login
```

Add commits.

```text
A ---- B ---- C (main)
               \
                D ---- E (feature-login)
```

Now switch back.

```bash
git switch main
```

Merge:

```bash
git merge feature-login
```

Result:

```text
A ---- B ---- C -------- F (main)
               \        /
                D ---- E
```

Git creates a **merge commit** (`F`) because both branches have different histories.

---

# Syntax

```bash
git merge <branch-name>
```

Example:

```bash
git merge feature-login
```

---

# Important Rule

Always switch to the **destination branch** before merging.

Example:

```bash
git switch main
git merge feature-login
```

Meaning:

Merge `feature-login` **into** `main`.

---

# Basic Commands

## Merge Feature Branch into Main

```bash
git switch main
git merge feature-login
```

---

## Merge Payment Branch

```bash
git switch main
git merge feature-payment
```

---

## Merge Bug Fix

```bash
git switch main
git merge bugfix-navbar
```

---

# Types of Git Merge

Git mainly performs two kinds of merges.

## 1. Fast-Forward Merge

## 2. Three-Way Merge

---

# Fast-Forward Merge

Suppose:

```text
A ---- B ---- C (main)
               \
                D ---- E (feature-login)
```

No new commits were added to `main`.

Merge:

```bash
git switch main
git merge feature-login
```

Result:

```text
A ---- B ---- C ---- D ---- E (main)
```

Git simply moves the `main` pointer forward.

No merge commit is created.

This is called a **Fast-Forward Merge**.

---

# Three-Way Merge

Suppose both branches changed.

```text
A ---- B ---- C ---- X (main)

       \

        D ---- E (feature-login)
```

Now merge.

Git cannot simply move the pointer.

It creates:

```text
A ---- B ---- C ---- X -------- M (main)

       \                      /

        D -------- E --------
```

`M` is a **Merge Commit**.

---

# Merge Commit

A merge commit has **two parent commits**.

Example:

```text
Parent 1 → main

Parent 2 → feature-login
```

Git combines both histories.

---

# Checking Merge History

Use:

```bash
git log --oneline --graph
```

Example:

```text
*   Merge branch 'feature-login'
|\
| *
| *
*
```

The graph shows where branches joined together.

---

# Merge Without Fast Forward

Even if Git can perform a fast-forward merge, you can force a merge commit.

```bash
git merge --no-ff feature-login
```

Result:

A merge commit is always created.

Many companies use this because project history becomes easier to understand.

---

# Fast Forward Only

```bash
git merge --ff-only feature-login
```

Git merges only if a fast-forward merge is possible.

Otherwise it stops with an error.

---

# Abort a Merge

Suppose a merge conflict occurs.

Cancel the merge.

```bash
git merge --abort
```

Git returns to the state before the merge started.

---

# Merge Conflicts

Suppose both branches edit the same line.

Main:

```javascript
console.log("Hello");
```

Feature:

```javascript
console.log("Welcome");
```

Git does not know which version is correct.

It reports a merge conflict.

Example:

```text
CONFLICT (content): Merge conflict in app.js
```

Git marks the file like this:

```text
<<<<<<< HEAD
console.log("Hello");
=======
console.log("Welcome");
>>>>>>> feature-login
```

You must:

1. Edit the file.
2. Remove the conflict markers.
3. Keep the correct code.
4. Save the file.

Then:

```bash
git add app.js
git commit
```

The merge is completed.

---

# Merge Workflow

```text
Create Branch

↓

Develop Feature

↓

Commit Changes

↓

Switch to Main

↓

Merge Feature

↓

Delete Feature Branch
```

---

# Delete Merged Branch

After merging:

```bash
git branch -d feature-login
```

The code remains in `main`.

Only the branch name is removed.

---

# Difference Between Merge and Rebase

| Git Merge                        | Git Rebase                         |
| -------------------------------- | ---------------------------------- |
| Preserves branch history         | Rewrites history                   |
| Creates merge commit (sometimes) | Usually no merge commit            |
| Easy to understand               | Cleaner history                    |
| Safe for teams                   | Best for local work before pushing |

---

# Merge vs Cherry-Pick

| Merge             | Cherry-pick               |
| ----------------- | ------------------------- |
| Takes all commits | Takes selected commits    |
| Combines branches | Copies individual commits |

---

# Merge vs Revert

| Merge             | Revert                       |
| ----------------- | ---------------------------- |
| Combines branches | Undoes commits               |
| Adds new work     | Removes previous work safely |

---

# Merge vs Branch

| Merge             | Branch           |
| ----------------- | ---------------- |
| Combines branches | Creates branches |

---

# Advantages

* Easy collaboration.
* Keeps complete history.
* Combines feature branches.
* Safe for team projects.
* Standard Git workflow.

---

# Disadvantages

* Can create merge conflicts.
* Large branches may be difficult to merge.
* Too many merge commits can make history busy.

---

# Important Notes

* Always update your branch before merging.

```bash
git pull
```

* Test the feature before merging.
* Resolve merge conflicts carefully.
* Delete old feature branches after merging.

---

# Most Used Commands (Quick Revision)

Merge branch:

```bash
git merge feature-login
```

---

Force merge commit:

```bash
git merge --no-ff feature-login
```

---

Fast-forward only:

```bash
git merge --ff-only feature-login
```

---

Abort merge:

```bash
git merge --abort
```

---

View graph:

```bash
git log --oneline --graph
```

---

Delete merged branch:

```bash
git branch -d feature-login
```

---

# Real-World Scenario

You are working on an e-commerce website.

The `feature-payment` branch is complete and tested.

Steps:

```bash
git switch main
git pull
git merge feature-payment
git push origin main
git branch -d feature-payment
```

Now the payment feature is part of the main project.

---

# Viva Questions

### Q1. What is Git Merge?

**Answer:**

Git Merge combines the changes of one branch into another branch.

---

### Q2. Which branch should you switch to before merging?

**Answer:**

The destination branch.

Example:

```bash
git switch main
git merge feature-login
```

---

### Q3. What is a Fast-Forward Merge?

**Answer:**

A merge where Git simply moves the branch pointer forward without creating a merge commit.

---

### Q4. What is a Merge Commit?

**Answer:**

A special commit created when Git combines two different branch histories.

---

### Q5. What is a Merge Conflict?

**Answer:**

A merge conflict happens when Git cannot automatically combine changes because the same part of a file was modified differently in two branches.

---

### Q6. How do you cancel an unfinished merge?

```bash
git merge --abort
```

---

### Q7. How do you force Git to create a merge commit?

```bash
git merge --no-ff feature-login
```

---

### Q8. Which command shows the branch history graph?

```bash
git log --oneline --graph
```

---

# Interview One-Line Definition

> **`git merge` is a Git command that combines the changes and history of one branch into another, allowing completed features, bug fixes, or improvements to become part of the main project.**
