# Git Amend (`git-amend.md`)

# What is `git commit --amend`?

`git commit --amend` is a Git command used to **modify the most recent commit**.

It allows you to:

* Change the last commit message.
* Add forgotten files to the last commit.
* Update the latest commit without creating a new commit.

**Simple Definition**

> **`git commit --amend` replaces the latest commit with a new updated commit.**

---

# Why do we use Git Amend?

Sometimes after committing, you realize:

* You forgot to add a file.
* You made a small mistake.
* The commit message has a typo.
* You want to update the last commit.

Instead of creating another unnecessary commit, you can modify the previous one.

---

# Why was Amend introduced?

Without amend, developers would have to create extra commits.

Example:

First commit:

```bash
git commit -m "Add login feature"
```

Then you realize you forgot `login.css`.

Normally:

```bash
git add login.css
git commit -m "Add login css"
```

History becomes:

```text
A ---- B ---- C
              |
              Add login feature
              Add login css
```

Two commits for one small change.

Using amend:

```bash
git add login.css
git commit --amend
```

History becomes:

```text
A ---- B ---- C
              |
              Updated login feature
```

Cleaner history.

---

# Basic Syntax

```bash
git commit --amend
```

---

# Changing the Last Commit Message

Suppose:

Current commit:

```bash
git commit -m "Add logn feature"
```

Mistake:

```
logn
```

should be:

```
login
```

Run:

```bash
git commit --amend -m "Add login feature"
```

Now the latest commit message is changed.

---

# Adding Forgotten Files to Last Commit

Example:

You committed:

```bash
git add app.js
git commit -m "Add dashboard"
```

Later you remember:

```
style.css
```

was missing.

Add file:

```bash
git add style.css
```

Amend:

```bash
git commit --amend --no-edit
```

Now the file is added to the previous commit.

---

# What does `--no-edit` mean?

Normally amend opens the editor to change the commit message.

Example:

```bash
git commit --amend
```

Git asks:

```
Update commit message?
```

Using:

```bash
git commit --amend --no-edit
```

means:

> Keep the old commit message and only update files.

---

# Changing Commit Message Only

Command:

```bash
git commit --amend -m "New message"
```

Example:

Before:

```
Fix bug
```

After:

```
Fix authentication bug
```

---

# Amend Workflow

Example:

Initial commit:

```text
A ---- B ---- C (HEAD)
```

Run:

```bash
git commit --amend
```

Result:

```text
A ---- B ---- D (HEAD)
```

Important:

Commit C is replaced by commit D.

The old commit gets a new hash.

---

# Important Concept: Commit Hash Changes

Before:

```
Commit C

Hash:
abc123
```

After amend:

```
Commit D

Hash:
xyz789
```

Why?

Because Git commit hash depends on:

* Commit message
* Files
* Parent commit
* Author information

Any change creates a new hash.

---

# Amend and Staging Area

Amend uses the staging area.

Example:

Current commit:

```
A ---- B
```

Modified file:

```
app.js
```

Stage:

```bash
git add app.js
```

Amend:

```bash
git commit --amend
```

Git takes staged changes and combines them with the previous commit.

---

# Amend Without Changing Files

Change only message:

```bash
git commit --amend -m "Correct message"
```

---

# Amend After Push

Important rule:

> Avoid amending commits that are already pushed to shared branches.

Example:

You pushed:

```
A ---- B ---- C
```

Then:

```bash
git commit --amend
```

History becomes:

```
A ---- B ---- D
```

Remote still has C.

Now histories are different.

You need:

```bash
git push --force
```

Force push can overwrite other developers' work.

---

# When is Amend Safe?

Safe:

* Before pushing.
* On your local branch.
* Private feature branch.

Example:

```text
feature-login (only you)
```

---

# When Should You Avoid Amend?

Avoid:

* Main branch.
* Production branch.
* Shared team branches.

Because it rewrites history.

---

# Difference Between Amend and New Commit

| Amend                   | New Commit          |
| ----------------------- | ------------------- |
| Updates previous commit | Creates new commit  |
| Keeps history clean     | Adds another commit |
| Changes commit hash     | Keeps old commits   |
| Best before push        | Safe after push     |

---

# Difference Between Amend and Reset

| Amend                      | Reset                     |
| -------------------------- | ------------------------- |
| Modifies latest commit     | Moves HEAD                |
| Used for small corrections | Used for changing history |
| Uses staging area          | Changes branch pointer    |

---

# Difference Between Amend and Revert

| Amend                       | Revert                  |
| --------------------------- | ----------------------- |
| Changes latest local commit | Creates new undo commit |
| Rewrites history            | Preserves history       |
| Usually before push         | Safe after push         |

---

# Difference Between Amend and Restore

| Amend           | Restore                |
| --------------- | ---------------------- |
| Updates commit  | Restores files         |
| Changes history | Does not create commit |

---

# Real-World Examples

## Example 1: Forgot README File

You committed:

```bash
git commit -m "Add project"
```

Forgot README.

Solution:

```bash
git add README.md
git commit --amend --no-edit
```

---

## Example 2: Wrong Commit Message

Before:

```
Fix user authentcation
```

After:

```bash
git commit --amend -m "Fix user authentication"
```

---

## Example 3: Wrong File Added

You accidentally added:

```
password.txt
```

before committing.

You can remove it from staging:

```bash
git reset password.txt
```

Then:

```bash
git commit --amend
```

---

# Common Errors

## Error 1

```
You have nothing to amend
```

Reason:

There is no previous commit.

Solution:

Create a commit first.

---

## Error 2

```
Updates were rejected
```

Reason:

You amended a pushed commit.

Solution:

Avoid force push on shared branches.

---

# Interview Questions

### Q1. What is `git commit --amend`?

**Answer:**

It modifies the latest commit by changing its message or adding new staged changes.

---

### Q2. Does amend create a new commit?

**Answer:**

Technically yes. It replaces the old commit with a new commit having a different hash.

---

### Q3. Why does commit hash change after amend?

**Answer:**

Because commit content and metadata changed.

---

### Q4. When should you use amend?

**Answer:**

Before pushing, when correcting your latest local commit.

---

### Q5. Is amend safe after pushing?

**Answer:**

No, because it rewrites history.

---

### Q6. How do you add forgotten files to the last commit?

```bash
git add file.txt
git commit --amend --no-edit
```

---

### Q7. How do you change only the commit message?

```bash
git commit --amend -m "New message"
```

---

# Interview Scenarios

### Scenario 1

You committed code but forgot one file.

What will you do?

Answer:

```bash
git add forgotten-file
git commit --amend --no-edit
```

---

### Scenario 2

You pushed a commit to main and want to amend it.

Should you?

Answer:

No. Use a new commit or revert because main is shared.

---

### Scenario 3

Your last commit message has a spelling mistake.

Solution:

```bash
git commit --amend -m "Correct message"
```

---

# Quick Revision

Modify last commit:

```bash
git commit --amend
```

---

Change message:

```bash
git commit --amend -m "message"
```

---

Add forgotten files:

```bash
git add file
git commit --amend --no-edit
```

---

Remember:

```
Amend = Modify Last Commit

Before Push  → Safe

After Push   → Dangerous
```

---

# One-Line Interview Definition

> **`git commit --amend` is a Git command used to modify the most recent commit by updating its message or adding staged changes, mainly used to clean up local commit history before pushing.**
