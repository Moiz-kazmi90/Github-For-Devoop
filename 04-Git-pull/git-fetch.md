# Git Fetch (`git-fetch.md`)

# What is `git fetch`?

`git fetch` is a Git command used to **download the latest changes from a remote repository without changing your local branch or working files.**

Unlike `git pull`, it **does not merge** the downloaded changes.

**Simple Definition**

> **`git fetch` downloads the latest commits from a remote repository but does not merge them into your current branch.**

---

# Why do we use Git Fetch?

Suppose your teammate pushed new commits to GitHub.

You want to:

* See what has changed.
* Review new commits.
* Compare branches.
* Decide when to merge.

Instead of updating your branch immediately, you can use:

```bash
git fetch
```

This downloads the latest changes without affecting your current work.

---

# Why was Git Fetch introduced?

Imagine this situation.

Developer A pushes new code to GitHub.

Developer B is working on an important feature.

If Developer B runs:

```bash
git pull
```

Git immediately downloads and merges the new changes.

This may create merge conflicts or interrupt ongoing work.

Instead, Developer B can run:

```bash
git fetch
```

Git downloads the updates but leaves the current branch unchanged.

Developer B can review the changes before merging.

---

# How Git Fetch Works

Current Local Repository

```text
A ---- B ---- C (main)
```

Remote Repository

```text
A ---- B ---- C ---- D ---- E (origin/main)
```

Run:

```bash
git fetch
```

Result:

```text
Local Branch

A ---- B ---- C (main)

Remote Tracking Branch

A ---- B ---- C ---- D ---- E (origin/main)
```

Notice:

Your local `main` branch is still at **C**.

Only `origin/main` moved to **E**.

---

# Syntax

Basic fetch

```bash
git fetch
```

---

Fetch from origin

```bash
git fetch origin
```

---

Fetch one branch

```bash
git fetch origin main
```

---

Fetch all remotes

```bash
git fetch --all
```

---

# What Happens Internally?

When you run:

```bash
git fetch
```

Git:

1. Connects to the remote repository.
2. Downloads new commits.
3. Updates remote-tracking branches.
4. Does **not** change your working directory.
5. Does **not** create merge commits.

---

# What is a Remote Tracking Branch?

A remote-tracking branch is Git's record of the remote branch.

Example:

```text
origin/main
```

It is updated after:

```bash
git fetch
```

Your own local branch remains unchanged until you merge or rebase.

---

# Git Fetch Workflow

```text
Developer A

↓

git push

↓

GitHub Updated

↓

Developer B

↓

git fetch

↓

origin/main Updated

↓

Review Changes

↓

git merge origin/main
```

---

# Viewing Downloaded Changes

After fetching:

View commits:

```bash
git log main..origin/main
```

---

View differences:

```bash
git diff main origin/main
```

---

See commit graph:

```bash
git log --oneline --graph --all
```

---

# Merge After Fetch

After reviewing:

```bash
git merge origin/main
```

or

```bash
git rebase origin/main
```

---

# Git Fetch vs Git Pull

| Git Fetch                   | Git Pull                           |
| --------------------------- | ---------------------------------- |
| Downloads changes           | Downloads and merges changes       |
| Safe for review             | Updates current branch immediately |
| No merge                    | Merge happens automatically        |
| Working directory unchanged | Working directory updated          |

---

# Git Fetch vs Git Clone

| Git Fetch                   | Git Clone                               |
| --------------------------- | --------------------------------------- |
| Updates existing repository | Downloads repository for the first time |
| Used many times             | Usually used once                       |

---

# Git Fetch vs Git Push

| Git Fetch         | Git Push        |
| ----------------- | --------------- |
| Downloads commits | Uploads commits |
| Remote → Local    | Local → Remote  |

---

# Git Fetch vs Git Merge

| Git Fetch          | Git Merge               |
| ------------------ | ----------------------- |
| Downloads commits  | Combines branches       |
| No merge performed | Creates merge if needed |

---

# Real-World Example

Developer A

```bash
git add .
git commit -m "Payment feature"
git push origin main
```

Developer B

```bash
git fetch
```

Check new commits:

```bash
git log main..origin/main
```

If everything looks correct:

```bash
git merge origin/main
```

---

# Why Many Companies Prefer Fetch

Large companies often recommend:

```bash
git fetch
```

instead of

```bash
git pull
```

because developers can review changes before merging.

This reduces mistakes.

---

# Common Errors

## Error

```text
fatal: not a git repository
```

Reason:

You are outside the project folder.

Solution:

```bash
cd project-folder
```

---

## Error

```text
Could not read from remote repository.
```

Reason:

* Wrong remote URL
* No permission
* SSH key problem

Check:

```bash
git remote -v
```

---

## Error

```text
Authentication failed
```

Reason:

GitHub authentication problem.

Update your credentials or Personal Access Token.

---

# Advantages

* Safe.
* No automatic merge.
* Good for reviewing changes.
* Reduces accidental conflicts.
* Recommended for large teams.

---

# Disadvantages

* Requires an extra merge or rebase step.
* Beginners sometimes think fetch updates the current branch (it does not).

---

# Best Practices

* Fetch before starting work.
* Review commits before merging.
* Use fetch regularly in team projects.
* Merge only after understanding the changes.

---

# Quick Revision

Download latest changes

```bash
git fetch
```

---

Fetch origin

```bash
git fetch origin
```

---

Fetch main

```bash
git fetch origin main
```

---

Fetch all remotes

```bash
git fetch --all
```

---

View downloaded commits

```bash
git log main..origin/main
```

---

Merge later

```bash
git merge origin/main
```

---

# Real-World Workflow

```text
Developer Pushes Code

↓

git fetch

↓

Review Changes

↓

git merge

↓

Continue Working
```

---

# Interview Questions

### Q1. What is `git fetch`?

**Answer:**

`git fetch` downloads the latest changes from a remote repository without merging them into the current branch.

---

### Q2. Does `git fetch` change your working directory?

**Answer:**

No. It only updates remote-tracking branches.

---

### Q3. What is the difference between `git fetch` and `git pull`?

**Answer:**

`git fetch` only downloads changes, while `git pull` downloads and merges them automatically.

---

### Q4. Why do many companies prefer `git fetch`?

**Answer:**

Because developers can review changes before merging, making the workflow safer.

---

### Q5. Which branch is updated after `git fetch`?

**Answer:**

The remote-tracking branch (for example, `origin/main`).

---

### Q6. How do you merge fetched changes?

```bash
git merge origin/main
```

---

# Interview Scenarios

### Scenario 1

Your teammate pushed new commits.

You want to review them before updating your branch.

Which command will you use?

```bash
git fetch
```

---

### Scenario 2

You fetched changes but your local branch did not update.

Is this normal?

**Answer:**

Yes. `git fetch` updates only the remote-tracking branch. You must merge or rebase manually.

---

### Scenario 3

You want to compare your local branch with the latest remote branch.

Commands:

```bash
git fetch
git diff main origin/main
```

---

# Git Fetch Workflow Summary

```text
git fetch

↓

Downloads New Commits

↓

Updates origin/main

↓

Local main Remains Unchanged

↓

Review Changes

↓

Merge or Rebase

↓

Local Branch Updated
```

---

# Interview One-Line Definition

> **`git fetch` is a Git command that safely downloads the latest commits from a remote repository by updating remote-tracking branches without modifying the current local branch or working directory.**
