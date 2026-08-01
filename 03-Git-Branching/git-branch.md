# Git Branch (`git-branch.md`)

# What is a Git Branch?

A **Git Branch** is a separate line of development in a Git repository.

It allows developers to work on new features, fix bugs, or test code **without affecting the main project**.

**Simple Definition**

> **A Git branch is an independent copy of your project's development where you can make changes safely without affecting other branches.**

---

# Why do we use Git Branches?

Imagine you have a website that is working perfectly.

Now you want to:

* Add a login page
* Fix a bug
* Test a new feature
* Experiment with new code

If you work directly on the `main` branch, you might break the working project.

Instead, create a new branch and work there.

If everything works, merge it into `main`.

---

# Why was Git Branch introduced?

Before Git, many version control systems copied the entire project to create a branch.

This was:

* Slow
* Large in size
* Time-consuming

Git introduced lightweight branches.

A Git branch is just a **pointer to a commit**, so creating or switching branches is almost instant.

---

# Real-Life Example

Imagine a company is building an e-commerce website.

The team members are working on different features.

```text
Main Project
│
├── Login Feature
├── Payment Feature
├── Shopping Cart
├── Search Feature
└── Bug Fix
```

Each feature is developed in its own branch.

After testing, all branches are merged into the `main` branch.

---

# Default Branch

Most Git repositories use:

```text
main
```

Older repositories may still use:

```text
master
```

---

# Understanding Branches

Example:

```text
A ----- B ----- C (main)
```

Create a new branch:

```bash
git branch feature-login
```

Now:

```text
              feature-login
                    │
                    ▼

A ----- B ----- C (main)
```

Both branches point to the same commit.

---

# Working on a Branch

Switch to the branch:

```bash
git switch feature-login
```

Add a commit:

```text
A ----- B ----- C (main)
               \
                D (feature-login)
```

Now the new work exists only in `feature-login`.

---

# Main Branch Remains Safe

```text
main

A ----- B ----- C
```

Feature branch:

```text
feature-login

A ----- B ----- C ----- D
```

The `main` branch is not affected.

---

# Basic Git Branch Commands

## Show All Local Branches

```bash
git branch
```

Example:

```text
* main
  feature-login
  payment
```

The `*` shows the current branch.

---

## Create a New Branch

```bash
git branch feature-login
```

This creates the branch but does **not** switch to it.

---

## Switch to Another Branch

Modern command:

```bash
git switch feature-login
```

Older command:

```bash
git checkout feature-login
```

---

## Create and Switch Together

Modern:

```bash
git switch -c feature-login
```

Older:

```bash
git checkout -b feature-login
```

Both commands:

1. Create the branch.
2. Switch to it immediately.

---

## Rename Current Branch

```bash
git branch -m new-name
```

Example:

```bash
git branch -m login-feature
```

---

## Rename Another Branch

```bash
git branch -m old-name new-name
```

Example:

```bash
git branch -m feature-login login-feature
```

---

## Delete a Branch

Safe delete:

```bash
git branch -d feature-login
```

Git only deletes the branch if it has been merged.

---

## Force Delete a Branch

```bash
git branch -D feature-login
```

This deletes the branch even if it has not been merged.

Use carefully.

---

## Show Current Branch

```bash
git branch --show-current
```

Example Output:

```text
main
```

---

## Show All Branches

Local branches:

```bash
git branch
```

Remote branches:

```bash
git branch -r
```

All branches:

```bash
git branch -a
```

---

## Show Last Commit of Every Branch

```bash
git branch -v
```

---

## Show Merged Branches

```bash
git branch --merged
```

---

## Show Unmerged Branches

```bash
git branch --no-merged
```

---

# Branch Workflow

Example:

```text
A ---- B ---- C (main)
```

Create:

```bash
git switch -c feature-login
```

Now:

```text
A ---- B ---- C (main)
               \
                D
                E (feature-login)
```

Merge later:

```text
A ---- B ---- C -------- F (main)
               \        /
                D ---- E
```

---

# Branch Naming Best Practices

Good names:

```text
feature-login
feature-payment
bugfix-navbar
hotfix-api
release-v1.0
```

Avoid:

```text
branch1
test123
abc
newbranch
```

Use meaningful names.

---

# Local vs Remote Branch

| Local Branch              | Remote Branch           |
| ------------------------- | ----------------------- |
| Exists on your computer   | Exists on GitHub/GitLab |
| Created with `git branch` | Created after pushing   |
| Not visible to others     | Shared with the team    |

---

# Difference Between Branch and Folder

Many beginners think a branch is another folder.

This is incorrect.

A branch is **not a copy of the project folder**.

A branch is simply a pointer to a commit.

Git stores commits efficiently and moves the pointer when you switch branches.

---

# Branch vs Merge

| Branch                            | Merge                                     |
| --------------------------------- | ----------------------------------------- |
| Creates a new line of development | Combines branches                         |
| Used before development           | Used after development                    |
| Safe for experiments              | Brings completed work into another branch |

---

# Branch vs Checkout vs Switch

| Command        | Purpose                                                       |
| -------------- | ------------------------------------------------------------- |
| `git branch`   | Create, list, rename, and delete branches                     |
| `git switch`   | Switch branches                                               |
| `git checkout` | Older command used for switching branches and restoring files |

---

# Real-World Example

Suppose your team has five developers.

```text
main
│
├── feature-login
├── feature-payment
├── feature-search
├── feature-profile
└── bugfix-navbar
```

Each developer works on a separate branch.

After testing, all branches are merged into `main`.

This prevents developers from overwriting each other's work.

---

# Advantages

* Safe development.
* Multiple developers can work together.
* Easy bug fixing.
* Easy feature testing.
* Fast switching.
* Lightweight.

---

# Disadvantages

* Too many branches can become difficult to manage.
* Long-lived branches may cause merge conflicts.
* Requires proper naming and cleanup.

---

# Important Notes

* Creating a branch does **not** copy the entire project.
* Branches are lightweight pointers.
* Creating a branch does not automatically switch to it.
* Delete branches after merging to keep the repository clean.

---

# Most Used Commands (Quick Revision)

Create branch:

```bash
git branch feature-login
```

---

Switch branch:

```bash
git switch feature-login
```

---

Create and switch:

```bash
git switch -c feature-login
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

Rename branch:

```bash
git branch -m new-name
```

---

Delete merged branch:

```bash
git branch -d feature-login
```

---

Force delete branch:

```bash
git branch -D feature-login
```

---

Remote branches:

```bash
git branch -r
```

---

All branches:

```bash
git branch -a
```

---

Merged branches:

```bash
git branch --merged
```

---

Unmerged branches:

```bash
git branch --no-merged
```

---

# Common Errors

### Error

```text
error: Cannot delete branch 'feature-login' checked out
```

Reason:

You are trying to delete the branch you are currently using.

Solution:

```bash
git switch main
git branch -d feature-login
```

---

### Error

```text
error: The branch is not fully merged
```

Reason:

Git is protecting your work.

Solution:

If you are sure:

```bash
git branch -D feature-login
```

---

# Viva Questions

### Q1. What is a Git Branch?

**Answer:**

A Git branch is an independent line of development that allows developers to work on features or fixes without affecting the main branch.

---

### Q2. Does creating a branch copy the entire project?

**Answer:**

No. A branch is a lightweight pointer to a commit.

---

### Q3. Which command creates a branch?

```bash
git branch feature-login
```

---

### Q4. Which command switches branches?

```bash
git switch feature-login
```

---

### Q5. Which command creates and switches to a branch?

```bash
git switch -c feature-login
```

---

### Q6. Which command lists all local branches?

```bash
git branch
```

---

### Q7. How do you delete a merged branch?

```bash
git branch -d feature-login
```

---

### Q8. What is the difference between `-d` and `-D`?

**Answer:**

* `-d` deletes only merged branches.
* `-D` force deletes a branch even if it has not been merged.

---

### Q9. Which command shows the current branch?

```bash
git branch --show-current
```

---

### Q10. Why are Git branches lightweight?

**Answer:**

Because a branch is only a pointer to a commit, not a complete copy of the project.

---

# Interview One-Line Definition

> **A Git branch is a lightweight pointer to a commit that allows independent development of features, bug fixes, and experiments without affecting other branches.**
