# Git Comparisons

# Introduction

Git provides several commands to undo mistakes, but each command works differently.

The three most commonly confused commands are:

* `git restore`
* `git reset`
* `git revert`

Many beginners think they do the same thing, but they solve different problems.

Understanding the differences is very important for interviews, university exams, and real-world development.

---

# Quick Definitions

## Git Restore

> Restores files to a previous state without changing commit history.

---

## Git Reset

> Moves the current branch (HEAD) to another commit and can remove commits, unstage files, or discard local changes.

---

## Git Revert

> Creates a new commit that undoes the changes of an earlier commit while keeping the original commit in history.

---

# Simple Real-Life Analogy

Imagine your project is a notebook.

### Git Restore

You erase the writing on one page and rewrite it exactly as it was.

The notebook history stays the same.

---

### Git Reset

You tear out one or more recent pages from your notebook.

Those pages no longer appear in your notebook's timeline.

---

### Git Revert

You keep every page in the notebook.

Instead, you add a new page saying:

> "Ignore everything written on page 15."

Nothing is removed.

---

# The Three Git Areas

Git works with three places.

```text
Working Directory
       ↓
Staging Area
       ↓
Repository (Commits)
```

Knowing which area a command changes makes Git much easier.

---

# What Each Command Changes

| Feature            | git restore | git reset               | git revert              |
| ------------------ | ----------- | ----------------------- | ----------------------- |
| Working Directory  | ✅ Yes       | ✅ Yes (depends on mode) | ❌ No                    |
| Staging Area       | ✅ Yes       | ✅ Yes                   | ❌ No                    |
| Repository History | ❌ No        | ✅ Yes                   | ✅ Yes (adds new commit) |
| Creates New Commit | ❌ No        | ❌ No                    | ✅ Yes                   |
| Moves HEAD         | ❌ No        | ✅ Yes                   | ❌ No                    |

---

# Main Purpose

| Command       | Main Purpose                     |
| ------------- | -------------------------------- |
| `git restore` | Restore files                    |
| `git reset`   | Move HEAD and undo local commits |
| `git revert`  | Safely undo a committed change   |

---

# Working Directory Comparison

Suppose:

```text
app.js
```

You edit the file.

---

### Restore

```bash
git restore app.js
```

Result:

* Local edits disappear.
* File becomes like the latest commit.

---

### Reset

```bash
git reset --hard
```

Result:

* Local edits disappear.
* Staging clears.
* HEAD may move.

---

### Revert

Nothing happens.

`git revert` works only with commits.

---

# Staging Area Comparison

Suppose:

```bash
git add app.js
```

Now:

```text
app.js
```

is staged.

---

### Restore

```bash
git restore --staged app.js
```

Result:

* File becomes unstaged.

---

### Reset

```bash
git reset app.js
```

Result:

* File becomes unstaged.

Both commands can unstage files.

---

### Revert

Cannot unstage files.

---

# Commit History Comparison

History:

```text
Commit A

Commit B

Commit C ← HEAD
```

---

## Restore

```text
Commit A

Commit B

Commit C ← HEAD
```

History stays exactly the same.

---

## Reset

```bash
git reset --soft HEAD~1
```

History becomes:

```text
Commit A

Commit B ← HEAD
```

Commit C disappears from the current branch.

---

## Revert

```bash
git revert HEAD
```

History becomes:

```text
Commit A

Commit B

Commit C

Commit D (Undo C)
```

Nothing is removed.

---

# Visual Comparison

## Restore

```text
Commit A

Commit B

Commit C ← HEAD

↓

Restore File

↓

Commit A

Commit B

Commit C ← HEAD
```

History unchanged.

---

## Reset

```text
Commit A

Commit B

Commit C ← HEAD

↓

git reset

↓

Commit A

Commit B ← HEAD
```

History rewritten.

---

## Revert

```text
Commit A

Commit B

Commit C ← HEAD

↓

git revert

↓

Commit A

Commit B

Commit C

Commit D ← HEAD
```

History preserved.

---

# Safety Comparison

| Command | Safe After Push? |
| ------- | ---------------- |
| Restore | ✅ Yes            |
| Reset   | ❌ Usually No     |
| Revert  | ✅ Yes            |

---

# Which One Creates a Commit?

| Command | Creates Commit |
| ------- | -------------- |
| Restore | ❌              |
| Reset   | ❌              |
| Revert  | ✅              |

---

# Which One Changes Git History?

| Command | Changes History                                |
| ------- | ---------------------------------------------- |
| Restore | ❌                                              |
| Reset   | ✅                                              |
| Revert  | ✅ (adds a new commit without deleting history) |

---

# Which One Removes Commits?

| Command | Removes Commit |
| ------- | -------------- |
| Restore | ❌              |
| Reset   | ✅              |
| Revert  | ❌              |

---

# Which One Is Best for Teams?

| Command | Team Projects          |
| ------- | ---------------------- |
| Restore | ✅                      |
| Reset   | ⚠️ Only before pushing |
| Revert  | ✅ Best choice          |

---

# Which One Is Best Before Push?

| Situation                  | Command       |
| -------------------------- | ------------- |
| Remove latest local commit | `git reset`   |
| Discard file changes       | `git restore` |
| Undo pushed commit         | `git revert`  |

---

# Soft, Mixed and Hard Reset

| Reset Mode | Working Directory | Staging        | Commit History |
| ---------- | ----------------- | -------------- | -------------- |
| `--soft`   | Keeps changes     | Keeps staged   | Moves HEAD     |
| `--mixed`  | Keeps changes     | Clears staging | Moves HEAD     |
| `--hard`   | Deletes changes   | Clears staging | Moves HEAD     |

---

# Common Interview Scenarios

## Scenario 1

"I edited a file but haven't committed it."

Use:

```bash
git restore file.txt
```

---

## Scenario 2

"I accidentally staged the wrong file."

Use:

```bash
git restore --staged file.txt
```

or

```bash
git reset file.txt
```

---

## Scenario 3

"I made a wrong commit but haven't pushed it."

Use:

```bash
git reset --soft HEAD~1
```

---

## Scenario 4

"I pushed a bad commit to GitHub."

Use:

```bash
git revert <commit-id>
```

Never use `git reset --hard` on a shared branch unless everyone agrees and understands the consequences.

---

## Scenario 5

"I want to completely remove all local changes."

Use:

```bash
git reset --hard
```

---

# Decision Tree

```text
Did you already commit?

│

├── No

│      │

│      ├── Want to discard file changes?

│      │          │

│      │          └── git restore

│      │

│      └── Want to unstage files?

│                 │

│                 └── git restore --staged

│                     or git reset

│

└── Yes

       │

       ├── Already pushed?

       │

       │       ├── Yes

       │       │

       │       └── git revert

       │

       └── No

               │

               └── git reset
```

---

# Advantages Comparison

| Restore            | Reset           | Revert            |
| ------------------ | --------------- | ----------------- |
| Easy               | Powerful        | Safe              |
| Simple             | Flexible        | Team Friendly     |
| No history changes | Removes commits | Preserves history |

---

# Disadvantages Comparison

| Restore                     | Reset                   | Revert                 |
| --------------------------- | ----------------------- | ---------------------- |
| Cannot remove commits       | Can destroy history     | Adds extra commits     |
| Only works on tracked files | Dangerous with `--hard` | History becomes longer |

---

# Command Summary

## Restore

```bash
git restore file.txt
```

Restore one file.

```bash
git restore .
```

Restore all files.

```bash
git restore --staged file.txt
```

Unstage a file.

---

## Reset

```bash
git reset file.txt
```

Unstage a file.

```bash
git reset --soft HEAD~1
```

Remove commit, keep staged changes.

```bash
git reset --mixed HEAD~1
```

Remove commit, keep local changes.

```bash
git reset --hard HEAD~1
```

Remove commit and delete local changes.

---

## Revert

```bash
git revert HEAD
```

Undo latest commit safely.

```bash
git revert <commit-id>
```

Undo a specific commit.

---

# Final Comparison Table

| Feature            | Restore             | Reset                 | Revert                                          |
| ------------------ | ------------------- | --------------------- | ----------------------------------------------- |
| Restores Files     | ✅                   | ❌                     | ❌                                               |
| Unstages Files     | ✅                   | ✅                     | ❌                                               |
| Removes Commits    | ❌                   | ✅                     | ❌                                               |
| Creates New Commit | ❌                   | ❌                     | ✅                                               |
| Moves HEAD         | ❌                   | ✅                     | ❌                                               |
| Changes History    | ❌                   | ✅                     | ❌ (history is preserved; a new commit is added) |
| Safe After Push    | ✅                   | ❌                     | ✅                                               |
| Team Friendly      | ✅                   | ⚠️ Limited            | ✅                                               |
| Best For           | Local file recovery | Local history cleanup | Undoing pushed commits                          |

---

# Viva Questions

### Q1. Which command is used to restore a file?

**Answer:**

```bash
git restore file.txt
```

---

### Q2. Which command removes recent local commits?

**Answer:**

```bash
git reset
```

---

### Q3. Which command is safest after pushing commits?

**Answer:**

```bash
git revert
```

---

### Q4. Which command creates a new commit?

**Answer:**

`git revert`

---

### Q5. Which command moves HEAD?

**Answer:**

`git reset`

---

### Q6. Which command changes file contents without changing Git history?

**Answer:**

`git restore`

---

# One-Line Revision

* **git restore** → Restore files.
* **git reset** → Move HEAD and rewrite local history.
* **git revert** → Undo a commit safely by creating a new commit.
