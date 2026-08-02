# Git Checkout (`git-checkout.md`)

# What is `git checkout`?

`git checkout` is an older Git command used to:

* Switch branches
* Create and switch to a new branch
* Restore files
* View old commits
* Enter detached HEAD state

Before Git 2.23, `git checkout` was one of the most commonly used Git commands because it handled multiple tasks.

**Simple Definition**

> **`git checkout` is a multi-purpose Git command used to switch branches, restore files, or move to another commit.**

---

# Why do we use `git checkout`?

Suppose you have multiple branches.

```text
main
feature-login
feature-payment
bugfix-navbar
```

You want to move from `main` to `feature-login`.

Use:

```bash
git checkout feature-login
```

Now all your work happens on `feature-login`.

---

# Why was `git checkout` introduced?

Git repositories contain:

* Many branches
* Many commits
* Many versions of files

Developers needed one command that could:

* Move between branches
* Restore previous versions of files
* Inspect old commits

`git checkout` was created to perform all these tasks.

---

# Why was `git switch` and `git restore` introduced later?

Although `git checkout` was powerful, it became confusing.

Example:

```bash
git checkout feature-login
```

This switches branches.

Now another command:

```bash
git checkout app.js
```

This restores a file.

Same command.

Different job.

Many beginners accidentally restored files when they wanted to switch branches.

Git 2.23 introduced:

| Command       | Purpose         |
| ------------- | --------------- |
| `git switch`  | Switch branches |
| `git restore` | Restore files   |

Today:

* Use `git switch` for branches.
* Use `git restore` for files.
* Use `git checkout` mainly for older projects or when working with older Git versions.

---

# What problems does `git checkout` solve?

It can:

* Switch branches
* Create branches
* Restore deleted files
* Restore modified files
* Open old commits
* Compare project versions

---

# Syntax

```bash
git checkout <branch-name>
```

or

```bash
git checkout <commit-id>
```

or

```bash
git checkout -- <file>
```

---

# Basic Commands

## Switch Branch

```bash
git checkout main
```

---

```bash
git checkout feature-login
```

---

## Create New Branch

```bash
git checkout -b feature-login
```

Equivalent modern command:

```bash
git switch -c feature-login
```

---

## Restore a File

Suppose:

```text
app.js
```

was modified.

Restore it.

```bash
git checkout -- app.js
```

Modern command:

```bash
git restore app.js
```

---

## Restore Multiple Files

```bash
git checkout -- app.js index.html style.css
```

---

## Restore Entire Project

```bash
git checkout -- .
```

Modern equivalent:

```bash
git restore .
```

---

# Checkout a Previous Commit

View an older commit.

```bash
git checkout a12bc34
```

Git moves to that commit.

Notice:

You are **not** on any branch.

You enter **Detached HEAD** state.

---

# Understanding Detached HEAD

Normal situation:

```text
A ---- B ---- C (main)
```

HEAD

↓

```text
main
```

Now:

```bash
git checkout B
```

Result:

```text
A ---- B ---- C (main)

      ↑

     HEAD
```

HEAD points directly to Commit B.

It is no longer attached to a branch.

This is called **Detached HEAD**.

---

# What is Detached HEAD?

Detached HEAD means:

HEAD points directly to a commit instead of a branch.

You can:

* Explore old code.
* Test previous versions.
* Run old applications.

But be careful.

If you create commits here and switch away without creating a branch, those commits may become difficult to find.

---

# Create a Branch from Detached HEAD

Suppose:

```bash
git checkout a12bc34
```

Now create:

```bash
git switch -c experiment
```

or

```bash
git checkout -b experiment
```

Now your work is safe because HEAD is attached to the new branch.

---

# Checkout vs Switch

| git checkout      | git switch                        |
| ----------------- | --------------------------------- |
| Older command     | Modern command                    |
| Switches branches | Switches branches                 |
| Restores files    | Cannot restore files              |
| Opens commits     | Cannot directly check out commits |
| Multi-purpose     | Single-purpose                    |

---

# Checkout vs Restore

| git checkout         | git restore             |
| -------------------- | ----------------------- |
| Can restore files    | Restores files          |
| Can switch branches  | Cannot switch branches  |
| Can checkout commits | Cannot checkout commits |
| Older command        | Modern command          |

---

# Checkout vs Branch

| git checkout         | git branch                     |
| -------------------- | ------------------------------ |
| Switches branch      | Creates/lists/deletes branches |
| Can create with `-b` | Cannot switch branches         |

---

# Checkout vs Reset

| git checkout                                     | git reset                          |
| ------------------------------------------------ | ---------------------------------- |
| Moves working directory to another branch/commit | Moves HEAD and may rewrite history |
| Does not remove commits                          | Can remove local commits           |
| Safe for navigation                              | Can be destructive (`--hard`)      |

---

# Checkout vs Revert

| git checkout                           | git revert                               |
| -------------------------------------- | ---------------------------------------- |
| Used for navigation or restoring files | Creates a new commit that undoes changes |
| Does not create commits                | Creates a new commit                     |

---

# Real-World Example

A project has:

```text
main

feature-login

feature-payment

release-v1.0
```

Switch:

```bash
git checkout release-v1.0
```

Fix bug.

Return:

```bash
git checkout main
```

Merge later.

---

# Common Errors

## Error

```text
error: pathspec 'feature-login' did not match any file(s) known to git
```

Reason:

Branch does not exist.

Check:

```bash
git branch
```

---

## Error

```text
Your local changes would be overwritten by checkout.
```

Reason:

Uncommitted changes.

Solution:

Commit:

```bash
git add .
git commit -m "Save work"
```

or

```bash
git stash
```

Then switch again.

---

## Error

```text
You are in 'detached HEAD' state.
```

Reason:

You checked out a commit instead of a branch.

Solution:

Return:

```bash
git switch main
```

or create a branch:

```bash
git switch -c new-feature
```

---

# Advantages

* Powerful.
* Works with branches, commits, and files.
* Supported by every Git version.
* Useful for older tutorials.

---

# Disadvantages

* Performs multiple jobs.
* Confusing for beginners.
* Modern Git recommends using `git switch` and `git restore`.

---

# Important Notes

* `git checkout` is **not deprecated**.
* It is still available in modern Git.
* Git simply recommends using:

  * `git switch`
  * `git restore`
* Many older projects and tutorials still use `git checkout`.

---

# Most Used Commands (Quick Revision)

Switch branch:

```bash
git checkout main
```

---

Create and switch:

```bash
git checkout -b feature-login
```

---

Restore file:

```bash
git checkout -- app.js
```

---

Restore all files:

```bash
git checkout -- .
```

---

Checkout commit:

```bash
git checkout <commit-id>
```

---

Return to main:

```bash
git switch main
```

---

# Common Interview Questions

### Q1. What is `git checkout`?

**Answer:**

`git checkout` is a multi-purpose Git command used to switch branches, restore files, or move to another commit.

---

### Q2. Why did Git introduce `git switch` and `git restore`?

**Answer:**

Because `git checkout` performed multiple unrelated tasks, which confused beginners. Git separated branch switching and file restoration into dedicated commands.

---

### Q3. Which command creates and switches to a new branch?

```bash
git checkout -b feature-login
```

---

### Q4. What is Detached HEAD?

**Answer:**

Detached HEAD is a state where HEAD points directly to a commit instead of a branch.

---

### Q5. Can `git checkout` restore files?

**Answer:**

Yes.

Example:

```bash
git checkout -- app.js
```

---

### Q6. Which modern command replaces branch switching?

**Answer:**

```bash
git switch
```

---

### Q7. Which modern command replaces file restoration?

**Answer:**

```bash
git restore
```

---

### Q8. Is `git checkout` removed from Git?

**Answer:**

No.

It is still available and widely used, especially in older repositories and tutorials.

---

# Interview One-Line Definition

> **`git checkout` is a multi-purpose Git command that can switch branches, restore files, or check out older commits. In modern Git, its branch-switching and file-restoration responsibilities are largely replaced by `git switch` and `git restore`.**
