# Git Stash (`git-stash.md`)

# What is `git stash`?

`git stash` is a Git command used to **temporarily save your uncommitted changes without creating a commit.**

It allows you to clean your working directory so you can switch branches, pull changes, or work on something else.

**Simple Definition**

> **`git stash` temporarily stores your uncommitted changes in a safe place so you can restore them later.**

---

# Why do we use Git Stash?

Imagine you're working on a feature but suddenly your team lead asks you to fix a production bug.

Your current work is incomplete, so you don't want to commit it yet.

Instead of creating a temporary commit, you can run:

```bash
git stash
```

Now your working directory becomes clean, and you can switch branches safely.

---

# Why was Git Stash introduced?

Without Git Stash:

* You would have to create temporary commits.
* Your Git history would become messy.
* Switching branches with uncommitted changes could cause conflicts.

Git Stash solves this by storing unfinished work temporarily.

---

# Git Stash Workflow

```text
Working Directory
        ↓
git stash
        ↓
Stash Stack
        ↓
Clean Working Directory
        ↓
git stash apply / git stash pop
        ↓
Working Directory Restored
```

---

# Basic Syntax

Save current changes

```bash
git stash
```

---

Save with a message

```bash
git stash push -m "Working on login page"
```

---

View all stashes

```bash
git stash list
```

---

Restore a stash

```bash
git stash apply
```

---

Restore and remove stash

```bash
git stash pop
```

---

Delete one stash

```bash
git stash drop stash@{0}
```

---

Delete all stashes

```bash
git stash clear
```

---

# What Happens Internally?

Suppose:

```text
main

↓

Modified app.js

Modified style.css
```

Run:

```bash
git stash
```

Result:

```text
Working Directory

↓

Clean

Stash Stack

↓

stash@{0}

↓

app.js
style.css
```

Your changes are safely stored.

---

# Stash Stack

Git stores stashes in a stack (Last In, First Out).

Example:

```bash
git stash
git stash
git stash
```

List:

```text
stash@{0}

stash@{1}

stash@{2}
```

Newest stash is always:

```text
stash@{0}
```

---

# Viewing Stashes

```bash
git stash list
```

Example:

```text
stash@{0}: WIP on main

stash@{1}: Working on login

stash@{2}: Bug fixes
```

---

# Applying a Stash

```bash
git stash apply
```

Restores the latest stash.

The stash remains in the stash list.

---

Apply a specific stash

```bash
git stash apply stash@{1}
```

---

# Pop a Stash

```bash
git stash pop
```

This:

1. Restores the changes.
2. Removes the stash from the stack.

---

# Apply vs Pop

| `git stash apply` | `git stash pop`  |
| ----------------- | ---------------- |
| Restores changes  | Restores changes |
| Keeps stash       | Deletes stash    |
| Safer             | More convenient  |

---

# Save with a Message

Instead of:

```bash
git stash
```

Use:

```bash
git stash push -m "Payment API"
```

Now:

```bash
git stash list
```

shows:

```text
stash@{0}: Payment API
```

Much easier to identify later.

---

# Show Stash Content

Summary

```bash
git stash show
```

Detailed changes

```bash
git stash show -p
```

---

# Delete a Stash

Delete latest

```bash
git stash drop
```

Delete specific

```bash
git stash drop stash@{2}
```

Delete all

```bash
git stash clear
```

---

# Stashing Untracked Files

By default:

```bash
git stash
```

does **not** stash untracked files.

Include them:

```bash
git stash -u
```

or

```bash
git stash --include-untracked
```

---

# Include Ignored Files

```bash
git stash -a
```

or

```bash
git stash --all
```

This includes:

* Tracked files
* Untracked files
* Ignored files

---

# Real-World Example

You are working on:

```text
Feature: Login

↓

Modified:

app.js

login.css
```

Manager says:

"Fix production bug."

Run:

```bash
git stash
git switch main
```

Fix bug.

Commit:

```bash
git commit -m "Fix production bug"
```

Return:

```bash
git switch feature-login
git stash pop
```

Continue your unfinished work.

---

# Git Stash vs Git Commit

| Git Stash                | Git Commit              |
| ------------------------ | ----------------------- |
| Temporary                | Permanent               |
| No commit history        | Added to history        |
| Can be removed           | Stays forever           |
| Used for unfinished work | Used for completed work |

---

# Git Stash vs Git Reset

| Git Stash       | Git Reset                 |
| --------------- | ------------------------- |
| Saves changes   | Discards or moves history |
| Temporary       | History manipulation      |
| Easy to restore | May lose work             |

---

# Git Stash vs Git Restore

| Git Stash         | Git Restore             |
| ----------------- | ----------------------- |
| Saves changes     | Discards/restores files |
| Can recover later | Changes may be lost     |

---

# Git Stash vs Git Branch

| Git Stash             | Git Branch               |
| --------------------- | ------------------------ |
| Stores temporary work | Creates development line |
| No new branch         | New branch created       |

---

# Common Errors

## Error

```text
No local changes to save
```

Reason:

No modified files exist.

---

## Error

```text
stash@{5}: unknown revision
```

Reason:

That stash does not exist.

Check:

```bash
git stash list
```

---

## Merge Conflict After Pop

Sometimes:

```bash
git stash pop
```

may produce merge conflicts if the project changed.

Resolve conflicts manually.

---

# Best Practices

* Use stash for unfinished work.
* Give stashes meaningful names.
* Delete old stashes regularly.
* Prefer `apply` if you're unsure.
* Use `pop` after confirming you no longer need the stash.

---

# Advantages

* Temporary storage.
* Clean Git history.
* Easy branch switching.
* No unnecessary commits.
* Great for urgent tasks.

---

# Disadvantages

* Easy to forget stashed work.
* Can create conflicts when restoring.
* Not a replacement for commits.
* Too many unnamed stashes become confusing.

---

# Quick Revision

Save changes

```bash
git stash
```

---

Save with message

```bash
git stash push -m "Login feature"
```

---

View stashes

```bash
git stash list
```

---

Apply stash

```bash
git stash apply
```

---

Pop stash

```bash
git stash pop
```

---

Delete stash

```bash
git stash drop
```

---

Delete all

```bash
git stash clear
```

---

Include untracked files

```bash
git stash -u
```

---

Include ignored files

```bash
git stash -a
```

---

# Real-World Workflow

```text
Modify Files

↓

git stash

↓

Switch Branch

↓

Fix Bug

↓

Commit

↓

Switch Back

↓

git stash pop

↓

Continue Work
```

---

# Interview Questions

### Q1. What is Git Stash?

**Answer:**

`git stash` temporarily saves uncommitted changes without creating a commit.

---

### Q2. When should you use Git Stash?

**Answer:**

When you need to switch tasks or branches without committing incomplete work.

---

### Q3. What is the difference between `git stash apply` and `git stash pop`?

**Answer:**

`apply` restores changes but keeps the stash, while `pop` restores changes and removes the stash.

---

### Q4. Does `git stash` save untracked files?

**Answer:**

Not by default. Use:

```bash
git stash -u
```

---

### Q5. Which command shows all stashes?

```bash
git stash list
```

---

### Q6. How do you remove all stashes?

```bash
git stash clear
```

---

### Q7. Can `git stash` create merge conflicts?

**Answer:**

Yes. If the project changed after the stash was created, conflicts may occur when applying or popping it.

---

# Interview Scenarios

### Scenario 1

You're halfway through a feature and must immediately fix a production issue.

What do you do?

```bash
git stash
git switch main
```

---

### Scenario 2

You accidentally restored the wrong stash.

How do you avoid this?

Use:

```bash
git stash list
git stash apply stash@{1}
```

---

### Scenario 3

You want to keep the stash after restoring it.

Which command should you use?

```bash
git stash apply
```

---

# MCQs

### MCQ 1

Which command temporarily saves uncommitted changes?

A. `git reset`

B. `git stash`

C. `git restore`

D. `git merge`

**Answer:** B

---

### MCQ 2

Which command restores changes and removes the stash?

A. `git stash apply`

B. `git stash pop`

C. `git stash list`

D. `git stash show`

**Answer:** B

---

### MCQ 3

Which command lists all stashes?

A. `git status`

B. `git stash list`

C. `git log`

D. `git show`

**Answer:** B

---

### MCQ 4

Which option includes untracked files in a stash?

A. `-m`

B. `-u`

C. `-d`

D. `-f`

**Answer:** B

---

### MCQ 5

Which command permanently deletes all stashes?

A. `git stash remove`

B. `git stash clear`

C. `git stash clean`

D. `git stash delete`

**Answer:** B

---

# True / False

1. `git stash` creates a commit.

**False**

---

2. `git stash pop` removes the stash after restoring it.

**True**

---

3. `git stash apply` keeps the stash.

**True**

---

4. `git stash` includes untracked files by default.

**False**

---

5. Stashes are stored in a stack.

**True**

---

6. `git stash list` displays saved stashes.

**True**

---

7. `git stash clear` removes every stash.

**True**

---

8. Git Stash is mainly used for temporary work.

**True**

---

# One-Line Interview Definition

> **`git stash` is a Git command that temporarily saves uncommitted changes in a stack so you can work on something else and restore those changes later without creating a commit.**
