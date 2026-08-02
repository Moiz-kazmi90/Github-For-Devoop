# Git Merge Conflicts (`merge-conflicts.md`)

# What is a Merge Conflict?

A **Merge Conflict** happens when Git **cannot automatically combine changes** from two branches.

Git stops the merge and asks the developer to resolve the conflict manually.

**Simple Definition**

> **A merge conflict occurs when Git cannot decide which version of the code should be kept because the same part of a file was changed differently in two branches.**

---

# Why do Merge Conflicts happen?

Git can automatically merge most changes.

Example:

Developer A changes:

```text
login.html
```

Developer B changes:

```text
payment.html
```

Since they changed different files, Git merges automatically.

But if both developers modify the **same line** of the **same file**, Git cannot decide which change is correct.

This creates a **merge conflict**.

---

# Why was Merge Conflict introduced?

Git does **not guess** which code is correct.

Imagine:

Developer A writes:

```javascript
console.log("Login Successful");
```

Developer B writes:

```javascript
console.log("Welcome User");
```

Both changed the same line.

If Git automatically picked one version, the other developer's work could be lost.

Instead, Git stops and asks you to decide.

This protects your code.

---

# Real-Life Example

Suppose two developers are working on the same file.

Developer A

```text
feature-login
```

Developer B

```text
main
```

Both edit:

```text
app.js
```

Both save different code.

Now:

```bash
git merge feature-login
```

Git cannot merge automatically.

Conflict occurs.

---

# Example Repository

Initial History

```text
A ----- B ----- C (main)
               \
                D ----- E (feature-login)
```

Both branches modified:

```text
app.js
```

Now merge:

```bash
git switch main
git merge feature-login
```

Git reports:

```text
Auto-merging app.js
CONFLICT (content): Merge conflict in app.js
Automatic merge failed.
```

---

# Understanding Conflict Markers

Git opens the file like this:

```text
<<<<<<< HEAD
console.log("Hello");
=======
console.log("Welcome");
>>>>>>> feature-login
```

Meaning:

```text
<<<<<<< HEAD
```

Current branch (`main`).

---

```text
=======
```

Separates both versions.

---

```text
>>>>>>> feature-login
```

Incoming branch.

---

# How to Resolve the Conflict

Choose the correct code.

Example:

```javascript
console.log("Hello");
console.log("Welcome");
```

Or

```javascript
console.log("Welcome");
```

Or

```javascript
console.log("Hello");
```

Remove all conflict markers:

```text
<<<<<<<
=======
>>>>>>>
```

Save the file.

---

# Complete Conflict Resolution Steps

## Step 1

Merge:

```bash
git switch main
git merge feature-login
```

---

## Step 2

Git reports conflict.

---

## Step 3

Open the conflicted file.

---

## Step 4

Find:

```text
<<<<<<<
=======
>>>>>>>
```

---

## Step 5

Edit the file manually.

---

## Step 6

Save the file.

---

## Step 7

Stage the resolved file.

```bash
git add app.js
```

---

## Step 8

Complete the merge.

```bash
git commit
```

Git creates the merge commit.

---

# Checking Which Files Have Conflicts

```bash
git status
```

Example:

```text
both modified: app.js
```

---

# Abort the Merge

If you do not want to continue:

```bash
git merge --abort
```

Git returns to the state before the merge started.

---

# Conflict Example

Main Branch

```javascript
function login() {
    console.log("Login");
}
```

Feature Branch

```javascript
function login() {
    console.log("Welcome User");
}
```

After merge:

```text
<<<<<<< HEAD
console.log("Login");
=======
console.log("Welcome User");
>>>>>>> feature-login
```

Resolve:

```javascript
function login() {
    console.log("Welcome User");
}
```

Save.

Stage.

Commit.

Done.

---

# Types of Merge Conflicts

## 1. Content Conflict

Both branches change the same line.

Example:

```text
app.js
```

Most common conflict.

---

## 2. Delete vs Modify

Main deleted a file.

Feature modified the same file.

Git asks what should happen.

---

## 3. Rename Conflict

Both branches rename the same file differently.

Example:

Main:

```text
login.js
```

Feature:

```text
auth.js
```

---

## 4. File Location Conflict

One branch moves a file.

The other edits it.

Git needs your decision.

---

# Preventing Merge Conflicts

* Pull the latest changes before starting work.

```bash
git pull
```

---

* Merge frequently.

---

* Keep branches small.

---

* Communicate with your team.

---

* Work on different files when possible.

---

* Commit regularly.

---

# Useful Commands

Check status

```bash
git status
```

---

Start merge

```bash
git merge feature-login
```

---

Abort merge

```bash
git merge --abort
```

---

View merge history

```bash
git log --oneline --graph
```

---

Continue after resolving

```bash
git add .
git commit
```

---

# Merge Conflict Workflow

```text
Create Branch

↓

Develop Feature

↓

Commit

↓

Switch to Main

↓

Merge

↓

Conflict?

↓

YES

↓

Edit File

↓

git add

↓

git commit

↓

Merge Complete
```

---

# Merge Conflict vs Git Rebase Conflict

| Merge Conflict       | Rebase Conflict         |
| -------------------- | ----------------------- |
| Happens during merge | Happens during rebase   |
| Creates merge commit | Rewrites commits        |
| Keeps branch history | Creates cleaner history |

---

# Real-World Scenario

Developer A changes:

```javascript
const PORT = 3000;
```

Developer B changes:

```javascript
const PORT = 5000;
```

Both edit the same line.

Git cannot choose automatically.

Developer reviews the requirement, keeps the correct value, saves the file, stages it, and completes the merge.

---

# Advantages of Merge Conflicts

Although conflicts are inconvenient, they are useful because they:

* Prevent accidental loss of code.
* Force developers to review conflicting changes.
* Keep project history accurate.

---

# Common Mistakes

### Mistake 1

Leaving conflict markers in the file.

Wrong:

```text
<<<<<<< HEAD
=======
>>>>>>>
```

Always remove them.

---

### Mistake 2

Forgetting to stage the resolved file.

Correct:

```bash
git add app.js
```

---

### Mistake 3

Forgetting the final commit.

After resolving:

```bash
git commit
```

---

# Important Notes

* A merge conflict is **not an error in Git**.
* It simply means Git needs your decision.
* Read the code carefully before choosing a version.
* Test the application after resolving conflicts.

---

# Quick Revision

Start merge:

```bash
git merge feature-login
```

---

Check conflicts:

```bash
git status
```

---

Resolve file manually.

---

Stage:

```bash
git add app.js
```

---

Complete merge:

```bash
git commit
```

---

Abort merge:

```bash
git merge --abort
```

---

# Viva Questions

### Q1. What is a Merge Conflict?

**Answer:**

A merge conflict occurs when Git cannot automatically merge changes because the same part of a file was modified differently in two branches.

---

### Q2. Why do merge conflicts happen?

**Answer:**

Because two branches modify the same line or overlapping parts of a file, and Git cannot determine which version should be kept.

---

### Q3. Which command checks conflicted files?

```bash
git status
```

---

### Q4. Which command cancels an unfinished merge?

```bash
git merge --abort
```

---

### Q5. How do you complete a merge after resolving conflicts?

```bash
git add .
git commit
```

---

### Q6. What do the conflict markers mean?

* `<<<<<<< HEAD` → Current branch
* `=======` → Separator
* `>>>>>>> feature-login` → Incoming branch

---

### Q7. Can Git automatically solve every merge conflict?

**Answer:**

No. When changes overlap, Git requires the developer to resolve the conflict manually.

---

# Interview One-Line Definition

> **A Git merge conflict occurs when Git cannot automatically combine changes from different branches because the same code has been modified in incompatible ways, requiring manual resolution by the developer.**
