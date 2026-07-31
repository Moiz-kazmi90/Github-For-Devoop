# Git Reset (`git reset`)

## What is `git reset`?

`git reset` is a Git command used to **move the current branch (HEAD) to another commit**.

It can also:

* Unstage files
* Remove commits
* Discard changes
* Move HEAD to a previous commit

Depending on the option you use, `git reset` can be safe or destructive.

**Simple Definition**

> `git reset` is used to move HEAD to a previous commit and optionally remove changes from the staging area or working directory.

---

# Why do we use `git reset`?

Sometimes we make mistakes like:

* Committed the wrong files
* Wrote a wrong commit message
* Added unwanted changes
* Want to remove recent commits
* Accidentally staged files

`git reset` helps fix these mistakes.

---

# Why was `git reset` introduced?

Git stores every commit in a timeline.

Sometimes developers need to:

* Go back to an older commit
* Remove recent commits
* Unstage files before committing

Without `git reset`, this would be difficult.

Git introduced `git reset` to let developers safely move the branch pointer to another commit.

---

# What problems does `git reset` solve?

It solves these common problems:

### Problem 1

You staged a file by mistake.

```bash
git add app.js
```

Unstage it:

```bash
git reset app.js
```

---

### Problem 2

You made a wrong commit.

```text
Commit A
Commit B (Wrong)
```

Go back:

```bash
git reset --soft HEAD~1
```

Commit B is removed, but your changes stay staged.

---

### Problem 3

You want to remove local commits before pushing.

Use:

```bash
git reset --hard HEAD~2
```

The last two commits disappear.

---

# How does `git reset` work?

Suppose the history is:

```text
Commit A

Commit B

Commit C ← HEAD
```

Run:

```bash
git reset --soft HEAD~1
```

Now:

```text
Commit A

Commit B ← HEAD

Commit C (removed from branch)
```

HEAD moves back to Commit B.

---

# Three Areas in Git

Understanding these three areas makes `git reset` easy.

```text
Working Directory
       ↓
Staging Area
       ↓
Repository (Commits)
```

`git reset` can affect one, two, or all three areas depending on the option.

---

# Types of Git Reset

Git has three main reset modes.

| Reset Mode | Staging Area         | Working Directory | Commit History |
| ---------- | -------------------- | ----------------- | -------------- |
| `--soft`   | Keeps changes staged | Keeps changes     | Moves HEAD     |
| `--mixed`  | Clears staging       | Keeps changes     | Moves HEAD     |
| `--hard`   | Clears staging       | Deletes changes   | Moves HEAD     |

---

# 1. Soft Reset

Command:

```bash
git reset --soft HEAD~1
```

What happens?

* HEAD moves back.
* Commit is removed.
* Changes stay staged.

Example:

Before:

```text
Commit A

Commit B ← HEAD
```

After:

```text
Commit A ← HEAD
```

Files remain ready to commit.

---

# 2. Mixed Reset (Default)

Command:

```bash
git reset HEAD~1
```

or

```bash
git reset --mixed HEAD~1
```

What happens?

* HEAD moves back.
* Commit is removed.
* Files become unstaged.
* Working directory keeps the changes.

This is the default reset mode.

---

# 3. Hard Reset

Command:

```bash
git reset --hard HEAD~1
```

What happens?

* HEAD moves back.
* Commit disappears.
* Staging area is cleared.
* Working directory is cleaned.
* Local changes are deleted.

**Warning**

`git reset --hard` permanently removes uncommitted changes.

Use it carefully.

---

# Syntax

```bash
git reset [option] <commit>
```

Examples:

```bash
git reset --soft HEAD~1
```

```bash
git reset --mixed HEAD~2
```

```bash
git reset --hard HEAD~3
```

---

# Understanding HEAD

HEAD always points to the latest commit.

Example:

```text
Commit A

Commit B

Commit C ← HEAD
```

Move back one commit:

```bash
git reset --soft HEAD~1
```

Now:

```text
Commit A

Commit B ← HEAD
```

---

# Finding Commit IDs

Use:

```bash
git log
```

Example:

```text
commit a12bc34
Added Login

commit 7cd45ef
Navbar Update

commit 123abcd
Initial Commit
```

Reset:

```bash
git reset --soft a12bc34
```

---

# Basic Commands

## Unstage one file

```bash
git reset app.js
```

---

## Unstage all files

```bash
git reset
```

---

## Soft reset

```bash
git reset --soft HEAD~1
```

---

## Mixed reset

```bash
git reset --mixed HEAD~1
```

---

## Hard reset

```bash
git reset --hard HEAD~1
```

---

## Reset to a specific commit

```bash
git reset --hard a12bc34
```

---

## Reset current branch to latest remote version

```bash
git fetch origin
git reset --hard origin/main
```

---

# Real Example

Create:

```text
app.js
```

Commit:

```bash
git add .
git commit -m "Version 1"
```

Modify file.

Commit again.

History:

```text
Commit A

Commit B ← HEAD
```

Remove latest commit but keep changes staged:

```bash
git reset --soft HEAD~1
```

Now:

```text
Commit A ← HEAD
```

Your modified files are still staged.

---

# Soft vs Mixed vs Hard

| Feature                         | Soft | Mixed | Hard |
| ------------------------------- | ---- | ----- | ---- |
| Moves HEAD                      | Yes  | Yes   | Yes  |
| Removes Commit                  | Yes  | Yes   | Yes  |
| Keeps Staged Changes            | Yes  | No    | No   |
| Keeps Working Directory Changes | Yes  | Yes   | No   |
| Deletes Local Changes           | No   | No    | Yes  |

---

# Difference Between Reset and Restore

| `git reset`                    | `git restore`           |
| ------------------------------ | ----------------------- |
| Moves HEAD                     | Restores files          |
| Can remove commits             | Does not remove commits |
| Can affect history             | Does not change history |
| Works with commits and staging | Mainly works with files |

---

# Difference Between Reset and Revert

| `git reset`                         | `git revert`                 |
| ----------------------------------- | ---------------------------- |
| Removes commits from current branch | Creates a new commit         |
| Can rewrite history                 | Keeps history                |
| Risky after pushing                 | Safe after pushing           |
| Best for local work                 | Best for shared repositories |

---

# Difference Between Reset and Checkout

| `git reset`              | `git checkout`                                |
| ------------------------ | --------------------------------------------- |
| Moves HEAD and branch    | Switches branches or checks out commits/files |
| Can remove commits       | Does not remove commits                       |
| Used for undoing commits | Used for navigation                           |

---

# When should you use `git reset`?

Use it when:

* You have not pushed your commits.
* You want to remove recent commits.
* You staged the wrong files.
* You want to rewrite local history.
* You want to clean your local branch.

---

# Advantages

* Easy to remove recent commits.
* Can unstage files.
* Helps clean commit history.
* Useful before pushing.
* Offers three reset modes.

---

# Disadvantages

* `--hard` can permanently delete changes.
* Rewriting history can create problems after pushing.
* Not recommended for shared branches.

---

# Important Notes

* Always check commit history:

```bash
git log
```

* Check file status:

```bash
git status
```

* Avoid `git reset --hard` unless you are sure.
* Never use `git reset --hard` on shared branches without understanding the consequences.

---

# Most Used Commands (Quick Revision)

```bash
git reset
```

Unstage all files.

---

```bash
git reset app.js
```

Unstage one file.

---

```bash
git reset --soft HEAD~1
```

Remove latest commit and keep staged changes.

---

```bash
git reset --mixed HEAD~1
```

Remove latest commit and unstage changes.

---

```bash
git reset --hard HEAD~1
```

Remove latest commit and delete local changes.

---

```bash
git reset --hard <commit-id>
```

Move to a specific commit.

---

# Real-Life Scenario

You accidentally committed temporary debug code.

```text
Commit A

Commit B (Debug Code)
```

The commit has **not** been pushed.

Run:

```bash
git reset --soft HEAD~1
```

The commit disappears, but your changes stay staged so you can fix the code and commit again.

---

# Viva Questions

### Q1. What is `git reset`?

**Answer:**

`git reset` moves the current branch (HEAD) to another commit and can also unstage files or remove commits depending on the reset mode.

---

### Q2. What are the three types of `git reset`?

**Answer:**

* `--soft`
* `--mixed`
* `--hard`

---

### Q3. Which reset mode is the default?

**Answer:**

`--mixed`

---

### Q4. Which reset mode deletes local changes?

**Answer:**

`--hard`

---

### Q5. How do you unstage a file?

```bash
git reset app.js
```

---

### Q6. Which command safely undoes a pushed commit?

**Answer:**

`git revert`

---

### Q7. When should you use `git reset`?

**Answer:**

Use `git reset` mainly for local commits that have **not** been pushed, especially when you want to remove commits or unstage files.

---

# Interview One-Line Definition

> **`git reset` is a Git command that moves the current branch (HEAD) to a previous commit and can optionally remove commits, unstage files, or discard local changes depending on the reset mode (`--soft`, `--mixed`, or `--hard`).**
