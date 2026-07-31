# Git Restore (`git restore`)

## What is `git restore`?

`git restore` is a Git command used to **restore files** to a previous state.

It helps you:

* Discard unwanted changes.
* Restore deleted files.
* Unstage files from the staging area.
* Recover a file from another commit.

**Simple Definition**

> `git restore` is used to restore files to their previous version without changing the commit history.

---

# Why was `git restore` introduced?

Before Git 2.23, developers used:

```bash
git checkout
```

The problem was that `git checkout` did **too many different jobs**.

It was used to:

* Switch branches
* Restore files
* Recover deleted files
* Checkout old commits

Because of this, many beginners became confused.

Example:

```bash
git checkout file.txt
```

Is it switching a branch?

OR

Is it restoring a file?

The command looked the same but performed different tasks depending on what you typed.

This caused many mistakes.

---

# Solution

Git introduced two new commands in Git 2.23.

| Command       | Purpose         |
| ------------- | --------------- |
| `git switch`  | Switch branches |
| `git restore` | Restore files   |

Now every command has one clear job.

This makes Git easier to learn.

---

# What problems does `git restore` solve?

It solves these common problems:

### Problem 1

You edited a file by mistake.

Example:

```text
README.md
```

You added wrong text.

You want the original file back.

Use:

```bash
git restore README.md
```

---

### Problem 2

You accidentally deleted a file.

Restore it:

```bash
git restore file.txt
```

---

### Problem 3

You staged a file by mistake.

Example:

```bash
git add app.js
```

Now you don't want to commit it.

Use:

```bash
git restore --staged app.js
```

---

### Problem 4

You want a file from an older commit.

Use:

```bash
git restore --source=HEAD~1 app.js
```

Now the file becomes the version from the previous commit.

---

# Syntax

```bash
git restore [options] <file>
```

Example:

```bash
git restore index.html
```

---

# Important Terms

## Working Directory

The place where you edit files.

Example:

```
project/
    app.js
    index.html
```

When you edit files here, they are in the Working Directory.

---

## Staging Area

After:

```bash
git add file.txt
```

The file moves to the Staging Area.

---

## Repository

After:

```bash
git commit
```

The changes are saved permanently in the Git Repository.

---

# Basic Commands

## Restore one file

```bash
git restore file.txt
```

---

## Restore multiple files

```bash
git restore file1.txt file2.txt
```

---

## Restore every changed file

```bash
git restore .
```

`.` means current directory.

---

## Restore a deleted file

```bash
git restore file.txt
```

---

## Restore only staged file

```bash
git restore --staged file.txt
```

This removes the file from staging.

It does **not** delete your work.

---

## Restore staged and working directory together

```bash
git restore --staged --worktree file.txt
```

Everything becomes exactly like the latest commit.

---

## Restore file from another commit

```bash
git restore --source=HEAD~1 file.txt
```

---

## Restore from a specific commit

```bash
git restore --source=9f8c123 file.txt
```

Replace the commit ID with your own commit hash.

---

## Restore an entire folder

```bash
git restore src/
```

---

# Understanding HEAD

HEAD points to your latest commit.

Example:

```
Commit 1
    ↓

Commit 2
    ↓

Commit 3 ← HEAD
```

Restore from HEAD:

```bash
git restore app.js
```

Git copies the file from the latest commit.

---

# Restore from Previous Commit

```
Commit 1

Commit 2

Commit 3 (HEAD)
```

Use:

```bash
git restore --source=HEAD~1 app.js
```

Now:

```
app.js
```

becomes the version from Commit 2.

---

# Common Options

## `--staged`

Restore staging area.

```bash
git restore --staged app.js
```

---

## `--worktree`

Restore working directory.

```bash
git restore --worktree app.js
```

---

## `--source`

Restore from another commit.

```bash
git restore --source=HEAD~2 app.js
```

---

# Real Example

Current status:

```bash
git status
```

Output:

```text
modified: app.js
modified: style.css
```

Discard changes:

```bash
git restore app.js
```

Status:

```text
modified: style.css
```

Only `style.css` is still modified.

---

# Example of Unstaging

You ran:

```bash
git add app.js
```

Check:

```bash
git status
```

Output:

```text
Changes to be committed:
    app.js
```

Remove from staging:

```bash
git restore --staged app.js
```

Now:

```text
Changes not staged for commit:
    app.js
```

Your work is still safe.

---

# Difference Between Restore and Checkout

| `git restore`          | `git checkout`                                           |
| ---------------------- | -------------------------------------------------------- |
| Restores files         | Switches branches and can also restore files (older Git) |
| Easy for beginners     | Confusing because it has multiple purposes               |
| Introduced in Git 2.23 | Older command                                            |
| Safer to use           | Easier to make mistakes                                  |

---

# Difference Between Restore and Reset

| `git restore`                  | `git reset`                            |
| ------------------------------ | -------------------------------------- |
| Restores files                 | Moves branch or unstages commits/files |
| Does not change commit history | Can change commit history              |
| Safe for beginners             | More powerful and risky                |

---

# Difference Between Restore and Revert

| `git restore`                                    | `git revert`                                     |
| ------------------------------------------------ | ------------------------------------------------ |
| Restores files                                   | Creates a new commit that reverses an old commit |
| No new commit                                    | Creates a new commit                             |
| Used before commit (or to restore file contents) | Used after commits have been pushed/shared       |

---

# When should you use `git restore`?

Use it when:

* You edited a file by mistake.
* You want to discard local changes.
* You accidentally staged a file.
* You deleted a tracked file by mistake.
* You want a file from an older commit.
* You do **not** want to change commit history.

---

# Advantages

* Easy to understand.
* Safe for beginners.
* Separates file restoration from branch switching.
* Prevents accidental mistakes.
* Makes Git commands cleaner.
* Replaces confusing uses of `git checkout`.

---

# Disadvantages

* Cannot restore files that Git has never tracked.
* If you restore a file after editing it (without committing or backing it up), your local changes are lost.
* Available only in Git 2.23 and later.

---

# Important Notes

* `git restore` works only with **tracked files**.
* Always run `git status` before restoring files.
* Restoring local changes cannot usually be undone unless the changes were committed or saved elsewhere.

---

# Most Used Commands (Quick Revision)

```bash
git restore file.txt
```

Restore one file.

---

```bash
git restore .
```

Restore all changed files.

---

```bash
git restore --staged file.txt
```

Unstage a file.

---

```bash
git restore --staged .
```

Unstage all files.

---

```bash
git restore --source=HEAD~1 file.txt
```

Restore from previous commit.

---

```bash
git restore src/
```

Restore a folder.

---

```bash
git status
```

Check file status before and after restore.

---

# Viva Questions

### Q1. What is `git restore`?

**Answer:**
`git restore` is used to restore files to a previous state or discard unwanted local changes without changing Git commit history.

---

### Q2. Why was `git restore` introduced?

**Answer:**
It was introduced in Git 2.23 because `git checkout` had multiple purposes, which confused beginners. Git separated branch switching (`git switch`) and file restoration (`git restore`).

---

### Q3. Does `git restore` create a commit?

**Answer:**
No. It only restores files and does not create a new commit.

---

### Q4. Can `git restore` change Git history?

**Answer:**
No. It only changes files in the working directory or staging area.

---

### Q5. How do you unstage a file?

```bash
git restore --staged file.txt
```

---

### Q6. How do you discard changes in all files?

```bash
git restore .
```

---

### Q7. Which Git version introduced `git restore`?

**Answer:**
Git **2.23**.
