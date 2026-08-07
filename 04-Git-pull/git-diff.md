# Git Diff (`git-diff.md`)

# What is `git diff`?

`git diff` is a Git command used to **compare differences between files, commits, branches, or the staging area.**

It helps developers see **what has changed** before committing, merging, or pushing code.

**Simple Definition**

> **`git diff` shows the differences between two versions of your project.**

---

# Why do we use `git diff`?

Imagine you modified several files.

Before committing, you want to check:

* What lines changed?
* Which lines were added?
* Which lines were removed?
* Did you accidentally change something?

Instead of guessing, run:

```bash
git diff
```

Git shows every change.

---

# Why was Git Diff introduced?

Without `git diff`:

* Developers could commit unwanted changes.
* Bugs would be harder to find.
* Code reviews would become difficult.

`git diff` lets developers review changes before saving them permanently.

---

# How Git Diff Works

Git compares two versions.

Example:

Original file

```javascript
console.log("Hello");
```

Modified file

```javascript
console.log("Hello World");
```

Run:

```bash
git diff
```

Output:

```diff
-console.log("Hello");
+console.log("Hello World");
```

Meaning:

* `-` → Removed line
* `+` → Added line

---

# Understanding Git Diff Symbols

Example:

```diff
@@ -1,3 +1,3 @@

-console.log("Hello");

+console.log("Hello World");
```

Meaning:

| Symbol | Meaning                |
| ------ | ---------------------- |
| `-`    | Removed line           |
| `+`    | Added line             |
| `@@`   | Location of the change |

---

# Basic Syntax

```bash
git diff
```

---

# Compare Working Directory with Staging Area

```bash
git diff
```

Shows:

**Working Directory** vs **Staging Area**

Example:

```text
Working Directory

↓

Modified File

↓

git diff

↓

Shows Unstaged Changes
```

---

# Compare Staged Changes

```bash
git diff --staged
```

or

```bash
git diff --cached
```

Shows:

**Staging Area** vs **Last Commit**

---

# Compare Two Commits

```bash
git diff <commit1> <commit2>
```

Example

```bash
git diff abc123 xyz789
```

Git shows differences between those commits.

---

# Compare Two Branches

```bash
git diff main feature-login
```

Shows all differences between both branches.

---

# Compare Specific File

```bash
git diff app.js
```

Shows only changes in:

```text
app.js
```

---

# Compare Staged Version of One File

```bash
git diff --staged app.js
```

---

# Compare Current Branch with Remote Branch

```bash
git diff main origin/main
```

Useful after:

```bash
git fetch
```

---

# Compare Current Commit with Previous Commit

```bash
git diff HEAD~1 HEAD
```

Meaning:

Previous commit vs Current commit.

---

# Compare Last Commit

```bash
git diff HEAD
```

Shows:

Current working directory vs latest commit.

---

# Compare Using Commit Hashes

```bash
git diff a12bc34 b45de67
```

---

# Git Diff Workflow

```text
Modify File

↓

git diff

↓

Review Changes

↓

git add

↓

git diff --staged

↓

git commit
```

---

# Real-World Example

Modify:

```javascript
const PORT = 3000;
```

New version:

```javascript
const PORT = 5000;
```

Run:

```bash
git diff
```

Output:

```diff
-const PORT = 3000;
+const PORT = 5000;
```

Now you know exactly what changed.

---

# Git Diff vs Git Status

| Git Diff                  | Git Status              |
| ------------------------- | ----------------------- |
| Shows code changes        | Shows file status       |
| Displays modified lines   | Displays modified files |
| Shows added/removed lines | Does not show code      |

---

# Git Diff vs Git Log

| Git Diff               | Git Log              |
| ---------------------- | -------------------- |
| Shows code differences | Shows commit history |
| Compares versions      | Lists commits        |

---

# Git Diff vs Git Show

| Git Diff             | Git Show                   |
| -------------------- | -------------------------- |
| Compare versions     | Show details of one commit |
| Multiple comparisons | Single commit information  |

---

# Git Diff vs Git Fetch

| Git Diff          | Git Fetch         |
| ----------------- | ----------------- |
| Shows differences | Downloads commits |

---

# Git Diff vs Git Merge

| Git Diff         | Git Merge         |
| ---------------- | ----------------- |
| Compares changes | Combines branches |

---

# Common Commands

Show unstaged changes

```bash
git diff
```

---

Show staged changes

```bash
git diff --staged
```

---

Compare branches

```bash
git diff main feature-login
```

---

Compare commits

```bash
git diff HEAD~1 HEAD
```

---

Compare remote branch

```bash
git diff main origin/main
```

---

Compare file

```bash
git diff app.js
```

---

# Common Errors

## No Output

You run:

```bash
git diff
```

Nothing appears.

Reason:

No unstaged changes.

---

## Wrong Comparison

Running:

```bash
git diff
```

instead of:

```bash
git diff --staged
```

will not show staged changes.

---

## Unknown Commit

```text
fatal: bad revision
```

Reason:

Incorrect commit hash.

---

# Best Practices

* Always review code before committing.
* Use `git diff --staged` before every commit.
* Compare branches before merging.
* Compare with remote after `git fetch`.
* Review important changes carefully.

---

# Advantages

* Finds mistakes before committing.
* Easy code review.
* Shows exact line changes.
* Useful for debugging.
* Essential for team collaboration.

---

# Disadvantages

* Large diffs can be difficult to read.
* Comparing very old commits may produce lengthy output.
* Beginners may confuse staged and unstaged differences.

---

# Quick Revision

Working directory changes

```bash
git diff
```

---

Staged changes

```bash
git diff --staged
```

---

Compare branches

```bash
git diff main feature-login
```

---

Compare commits

```bash
git diff HEAD~1 HEAD
```

---

Compare remote

```bash
git diff main origin/main
```

---

# Real-World Workflow

```text
Edit Code

↓

git diff

↓

Review Changes

↓

git add

↓

git diff --staged

↓

git commit

↓

git push
```

---

# Interview Questions

### Q1. What is `git diff`?

**Answer:**

`git diff` compares different versions of files and shows what has changed.

---

### Q2. What does `git diff` show by default?

**Answer:**

The differences between the **working directory** and the **staging area**.

---

### Q3. What does `git diff --staged` show?

**Answer:**

The differences between the **staging area** and the **latest commit (HEAD)**.

---

### Q4. How do you compare two branches?

```bash
git diff main feature-login
```

---

### Q5. How do you compare two commits?

```bash
git diff <commit1> <commit2>
```

---

### Q6. What do `+` and `-` mean in Git Diff?

**Answer:**

* `+` = Added line
* `-` = Removed line

---

### Q7. Why is `git diff` important?

**Answer:**

It lets developers review changes before committing or merging.

---

# Interview Scenarios

### Scenario 1

You edited five files.

Before committing, you want to review every change.

Command:

```bash
git diff
```

---

### Scenario 2

You already staged changes.

Now you want to verify what will be committed.

Command:

```bash
git diff --staged
```

---

### Scenario 3

You fetched remote updates.

You want to compare your branch with GitHub.

Commands:

```bash
git fetch
git diff main origin/main
```

---

# Viva Questions

### Q1. What is Git Diff?

### Q2. What is the difference between `git diff` and `git status`?

### Q3. What is the difference between `git diff` and `git log`?

### Q4. Which command compares staged changes?

### Q5. Which command compares branches?

### Q6. Which command compares commits?

### Q7. Why do developers use Git Diff before committing?

---

# Interview One-Line Definition

> **`git diff` is a Git command used to compare files, commits, branches, or the staging area, showing the exact line-by-line differences between two versions of a project.**
