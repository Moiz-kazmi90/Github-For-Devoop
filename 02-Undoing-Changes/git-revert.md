# Git Revert (`git revert`)

## What is `git revert`?

`git revert` is a Git command used to **undo the changes of a previous commit** by creating a **new commit**.

It does **not** delete or remove the old commit.

Instead, Git creates another commit that reverses the changes made by the selected commit.

**Simple Definition**

> `git revert` creates a new commit that undoes the changes of an earlier commit without changing Git history.

---

# Why do we use `git revert`?

Imagine you pushed a commit to GitHub.

Later you realize that the commit contains:

* A bug
* Wrong code
* Wrong documentation
* Unwanted changes

You want to remove those changes.

Since the commit is already part of the project's history, deleting it can create problems for other developers.

Instead of deleting it, Git adds another commit that cancels its changes.

This is exactly what `git revert` does.

---

# Why was `git revert` introduced?

Git projects often have many developers working together.

Suppose Developer A pushes a commit.

Developer B and Developer C pull the latest code.

Now if Developer A deletes that commit using commands like `git reset --hard` and force pushes, everyone else's history becomes different.

This can lead to:

* Merge conflicts
* Lost commits
* Broken repositories
* Confused team members

To solve this problem, Git provides `git revert`.

It safely undoes changes **without rewriting commit history**.

---

# What problems does `git revert` solve?

It solves these common problems:

### Problem 1

You committed buggy code.

Instead of deleting the commit:

```text
Commit A
Commit B (Bug)
Commit C
```

Use:

```bash
git revert <commit-id-of-B>
```

Git creates:

```text
Commit A
Commit B
Commit C
Commit D (Revert of B)
```

The history remains complete.

---

### Problem 2

You accidentally deleted important code.

Undo that commit with `git revert`.

---

### Problem 3

You already pushed the commit to GitHub.

Using `git reset` could affect everyone.

Using `git revert` is safe.

---

# How does `git revert` work?

Original history:

```text
Commit 1
Commit 2
Commit 3
```

Suppose Commit 2 added:

```javascript
console.log("Hello");
```

After:

```bash
git revert <commit-2-id>
```

Git creates a new commit that removes:

```javascript
console.log("Hello");
```

Now history becomes:

```text
Commit 1
Commit 2
Commit 3
Commit 4 (Revert Commit 2)
```

---

# Syntax

```bash
git revert <commit-id>
```

Example:

```bash
git revert a12b34c
```

---

# Finding Commit IDs

Use:

```bash
git log
```

Example output:

```text
commit 7fa12bc
Added Login Page

commit c23ad11
Fixed Navbar

commit 91bc221
Initial Commit
```

Now revert:

```bash
git revert c23ad11
```

---

# Basic Commands

## Revert one commit

```bash
git revert <commit-id>
```

---

## Revert the latest commit

```bash
git revert HEAD
```

---

## Revert previous commit

```bash
git revert HEAD~1
```

---

## Revert two commits

```bash
git revert HEAD~1
git revert HEAD
```

Each command creates a separate revert commit.

---

## Revert without opening the editor

```bash
git revert --no-edit <commit-id>
```

Git automatically uses the default revert message.

---

## Revert but do not commit immediately

```bash
git revert --no-commit <commit-id>
```

Git applies the reverse changes but waits for you to create the commit manually.

Then:

```bash
git commit -m "Reverted old feature"
```

---

# Real Example

Create a file:

```text
app.js
```

Content:

```javascript
console.log("Version 1");
```

Commit:

```bash
git add .
git commit -m "Version 1"
```

Modify:

```javascript
console.log("Version 2");
```

Commit again:

```bash
git add .
git commit -m "Version 2"
```

History:

```text
Commit A
Version 1

Commit B
Version 2
```

Now Version 2 has a bug.

Run:

```bash
git log
```

Copy Commit B ID.

Then:

```bash
git revert <Commit-B-ID>
```

Git creates:

```text
Commit C
Revert "Version 2"
```

Now the file becomes:

```javascript
console.log("Version 1");
```

---

# Reverting the Latest Commit

Instead of using the full commit ID:

```bash
git revert HEAD
```

`HEAD` always points to the latest commit.

---

# Reverting an Older Commit

History:

```text
Commit A

Commit B

Commit C

Commit D (HEAD)
```

Suppose Commit B contains a bug.

Run:

```bash
git revert <Commit-B-ID>
```

Result:

```text
Commit A

Commit B

Commit C

Commit D

Commit E (Revert of B)
```

Notice that Commit B still exists.

Only its changes are reversed.

---

# Common Options

## `--no-edit`

```bash
git revert --no-edit HEAD
```

Skips the editor and automatically creates the revert commit.

---

## `--no-commit`

```bash
git revert --no-commit HEAD
```

Applies reverse changes but waits for manual commit.

---

## `--edit`

```bash
git revert --edit HEAD
```

Lets you edit the commit message.

---

# Understanding HEAD

```text
Commit A

Commit B

Commit C ← HEAD
```

Revert latest commit:

```bash
git revert HEAD
```

Git creates:

```text
Commit A

Commit B

Commit C

Commit D (Undo Commit C)
```

---

# Difference Between Revert and Reset

| `git revert`                 | `git reset`                     |
| ---------------------------- | ------------------------------- |
| Creates a new commit         | Moves the branch pointer        |
| Keeps commit history         | Can remove commits from history |
| Safe for shared repositories | Risky after pushing             |
| Best for team projects       | Mostly used for local work      |

---

# Difference Between Revert and Restore

| `git revert`                       | `git restore`                                              |
| ---------------------------------- | ---------------------------------------------------------- |
| Works with commits                 | Works with files                                           |
| Creates a new commit               | Does not create a commit                                   |
| Used after commits                 | Usually used before committing or to restore file contents |
| Changes history by adding a commit | Does not change commit history                             |

---

# Difference Between Revert and Checkout

| `git revert`          | `git checkout`                                |
| --------------------- | --------------------------------------------- |
| Creates a new commit  | Switches branches or checks out commits/files |
| Safely undoes changes | Does not automatically undo commit history    |
| Keeps history         | Older multi-purpose command                   |

---

# When should you use `git revert`?

Use it when:

* You already committed wrong code.
* The commit is pushed to GitHub.
* You work with a team.
* You want to keep project history.
* You want a safe way to undo changes.

---

# Advantages

* Safe for shared repositories.
* Never deletes commit history.
* Easy to track changes.
* Creates a clear undo record.
* Recommended for team projects.

---

# Disadvantages

* Creates an extra commit.
* History becomes longer.
* Does not completely remove the old commit.

---

# Important Notes

* Always check commit IDs using:

```bash
git log
```

* `git revert` is safer than `git reset` after pushing commits.
* Every revert creates a new commit.
* The original commit remains in the repository history.

---

# Most Used Commands (Quick Revision)

```bash
git log
```

Show commit history.

---

```bash
git revert HEAD
```

Undo the latest commit.

---

```bash
git revert HEAD~1
```

Undo the previous commit.

---

```bash
git revert <commit-id>
```

Undo a specific commit.

---

```bash
git revert --no-edit HEAD
```

Revert without opening the editor.

---

```bash
git revert --no-commit HEAD
```

Apply reverse changes without creating the commit immediately.

---

# Real-Life Scenario

Suppose you pushed this commit:

```text
Added Payment Feature
```

Users report that the payment page crashes.

Instead of deleting the commit with `git reset`, you run:

```bash
git revert <payment-feature-commit-id>
```

Git creates a new commit that removes the payment feature while preserving the complete project history.

This is the safest solution for team projects.

---

# Viva Questions

### Q1. What is `git revert`?

**Answer:**

`git revert` creates a new commit that undoes the changes of a previous commit while keeping the original commit in Git history.

---

### Q2. Does `git revert` delete commits?

**Answer:**

No. It keeps the original commit and creates a new commit that reverses its changes.

---

### Q3. Which command is safer after pushing commits?

**Answer:**

`git revert` is safer because it does not rewrite Git history.

---

### Q4. Which command shows commit IDs?

```bash
git log
```

---

### Q5. How do you revert the latest commit?

```bash
git revert HEAD
```

---

### Q6. Does `git revert` create a new commit?

**Answer:**

Yes. Every successful revert creates a new commit.

---

### Q7. When should you use `git revert` instead of `git reset`?

**Answer:**

Use `git revert` when the commit has already been pushed or shared with others because it safely undoes changes without rewriting history.

---

# Interview One-Line Definition

> **`git revert` is a safe Git command that creates a new commit to undo the changes of a previous commit while preserving the complete commit history.**
