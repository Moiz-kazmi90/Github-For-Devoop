# Git Switch (`git-switch.md`)

# What is `git switch`?

`git switch` is a Git command used to **switch from one branch to another**.

It is a modern command introduced to make branch switching easier and less confusing than `git checkout`.

**Simple Definition**

> **`git switch` is used to change the current branch in a Git repository.**

---

# Why do we use `git switch`?

When working on a project, you often have multiple branches such as:

* `main`
* `feature-login`
* `feature-payment`
* `bugfix-navbar`

To work on a different branch, you need to switch to it.

Example:

```text
Current Branch:
main

Available Branches:
feature-login
feature-payment
bugfix-navbar
```

Move to another branch:

```bash
git switch feature-login
```

Now all new commits will be added to `feature-login`.

---

# Why was `git switch` introduced?

Before Git 2.23, developers used:

```bash
git checkout
```

The problem was that `git checkout` had many responsibilities.

It was used to:

* Switch branches
* Restore files
* Checkout old commits
* Create new branches

This confused many beginners.

Example:

```bash
git checkout feature-login
```

Does this switch branches?

Yes.

Now another example:

```bash
git checkout app.js
```

Does this switch branches?

No.

It restores a file.

The same command performed completely different tasks.

To solve this confusion, Git introduced two new commands in Git 2.23.

| New Command   | Purpose         |
| ------------- | --------------- |
| `git switch`  | Switch branches |
| `git restore` | Restore files   |

Now every command has one clear responsibility.

---

# What problems does `git switch` solve?

It solves these common problems:

### Problem 1

You want to move from one branch to another.

```bash
git switch main
```

---

### Problem 2

You want to create a new branch and immediately start working on it.

```bash
git switch -c feature-login
```

---

### Problem 3

You accidentally used `git checkout` for many different tasks.

`git switch` removes that confusion.

---

# How Does `git switch` Work?

Current repository:

```text
main
│
├── feature-login
├── payment
└── profile
```

Current branch:

```text
main
```

Run:

```bash
git switch payment
```

Now:

```text
Current Branch

payment
```

Your working directory changes to match the selected branch.

---

# Understanding Branch Switching

Initial History

```text
A ---- B ---- C (main)
              \
               D ---- E (feature-login)
```

Current branch:

```text
main
```

Run:

```bash
git switch feature-login
```

Now HEAD moves to:

```text
feature-login
```

Your files now match the latest commit on `feature-login`.

---

# Syntax

```bash
git switch <branch-name>
```

Example:

```bash
git switch main
```

---

# Basic Commands

## Switch to an Existing Branch

```bash
git switch feature-login
```

---

## Switch Back to Main

```bash
git switch main
```

---

## Create a New Branch and Switch

```bash
git switch -c feature-payment
```

Equivalent older command:

```bash
git checkout -b feature-payment
```

---

## Create Another Branch

```bash
git switch -c bugfix-navbar
```

---

## Switch to the Previous Branch

```bash
git switch -
```

Example:

```text
Current

main
```

Run:

```bash
git switch feature-login
```

Later:

```bash
git switch -
```

Git returns to:

```text
main
```

This is useful when you frequently move between two branches.

---

## Create a Branch from Another Branch

Suppose:

```text
main

feature-login
```

Create:

```bash
git switch feature-login
git switch -c login-ui
```

Now:

```text
main

feature-login

login-ui
```

`login-ui` starts from `feature-login`.

---

# Understanding HEAD

Suppose:

```text
main

A ---- B ---- C
```

HEAD points to:

```text
main
```

Run:

```bash
git switch feature-login
```

HEAD now points to:

```text
feature-login
```

No commits are deleted.

Only the current branch changes.

---

# Difference Between Switch and Checkout

| git switch             | git checkout      |
| ---------------------- | ----------------- |
| Switches branches      | Switches branches |
| Cannot restore files   | Can restore files |
| Easy for beginners     | More confusing    |
| Introduced in Git 2.23 | Older command     |

---

# Difference Between Switch and Branch

| git switch                                     | git branch                                |
| ---------------------------------------------- | ----------------------------------------- |
| Moves to another branch                        | Creates, lists, renames, deletes branches |
| Does not create a branch (unless `-c` is used) | Does not switch branches                  |

Example:

Create:

```bash
git branch feature-login
```

Current branch remains:

```text
main
```

Now:

```bash
git switch feature-login
```

Current branch becomes:

```text
feature-login
```

---

# Difference Between Switch and Restore

| git switch             | git restore              |
| ---------------------- | ------------------------ |
| Switches branches      | Restores files           |
| Changes current branch | Changes file contents    |
| Does not restore files | Does not switch branches |

---

# Difference Between Switch and Reset

| git switch              | git reset                          |
| ----------------------- | ---------------------------------- |
| Changes current branch  | Moves HEAD and may rewrite history |
| Safe operation          | Can be destructive (`--hard`)      |
| Does not remove commits | Can remove local commits           |

---

# Real-World Example

Suppose five developers are working on the same repository.

Branches:

```text
main

feature-login

feature-payment

feature-search

bugfix-navbar
```

Developer A:

```bash
git switch feature-login
```

Developer B:

```bash
git switch feature-payment
```

Developer C:

```bash
git switch bugfix-navbar
```

Each developer works independently without affecting the others.

---

# Common Errors

## Error 1

```text
fatal: invalid reference: feature-login
```

Reason:

The branch does not exist.

Solution:

Check available branches:

```bash
git branch
```

Or create it:

```bash
git switch -c feature-login
```

---

## Error 2

```text
Your local changes would be overwritten by checkout.
```

Reason:

You have uncommitted changes.

Solution:

Commit or stash your changes before switching:

```bash
git add .
git commit -m "Save work"
```

or

```bash
git stash
```

Then:

```bash
git switch feature-login
```

---

# Advantages

* Easy to understand.
* Designed only for branch switching.
* Safer than `git checkout` for beginners.
* Supports creating and switching in one command.
* Reduces mistakes.

---

# Disadvantages

* Available only in Git 2.23 and later.
* Older tutorials may still use `git checkout`.

---

# Important Notes

* `git switch` only works with branches.
* It cannot restore files.
* Creating a branch with `git branch` does not switch to it.
* Use `git switch -c` to create and immediately switch.

---

# Most Used Commands (Quick Revision)

Switch branch:

```bash
git switch main
```

---

Switch to feature branch:

```bash
git switch feature-login
```

---

Create and switch:

```bash
git switch -c feature-login
```

---

Return to previous branch:

```bash
git switch -
```

---

List branches:

```bash
git branch
```

---

Current branch:

```bash
git branch --show-current
```

---

# Viva Questions

### Q1. What is `git switch`?

**Answer:**

`git switch` is a Git command used to switch from one branch to another.

---

### Q2. Why was `git switch` introduced?

**Answer:**

It was introduced in Git 2.23 to separate branch switching from the multiple responsibilities of `git checkout`, making Git easier to learn.

---

### Q3. Which command creates and switches to a new branch?

```bash
git switch -c feature-login
```

---

### Q4. Does `git switch` restore files?

**Answer:**

No. File restoration is done with `git restore`.

---

### Q5. Which command returns to the previous branch?

```bash
git switch -
```

---

### Q6. What happens to HEAD when using `git switch`?

**Answer:**

HEAD moves to the selected branch. No commits are deleted or changed.

---

### Q7. What is the older alternative to `git switch`?

**Answer:**

```bash
git checkout
```

---

# Interview One-Line Definition

> **`git switch` is a modern Git command introduced in Git 2.23 that is used exclusively for switching between branches, making branch navigation simpler and less error-prone than `git checkout`.**
