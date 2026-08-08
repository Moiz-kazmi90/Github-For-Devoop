# GitHub Collaboration (`github-collaboration.md`)

# What is GitHub Collaboration?

**GitHub Collaboration** means multiple developers working together on the same software project using Git and GitHub.

Developers can:

* Work on different branches.
* Push their code to GitHub.
* Create Pull Requests.
* Review each other's code.
* Discuss changes.
* Resolve merge conflicts.
* Merge approved code into the main branch.

**Simple Definition**

> **GitHub Collaboration is a workflow where multiple developers use Git and GitHub to work, review, and merge code together safely.**

---

# Git vs GitHub

These are different things.

| Git                       | GitHub                       |
| ------------------------- | ---------------------------- |
| Version control system    | Cloud platform               |
| Works locally             | Works online                 |
| Tracks code history       | Hosts Git repositories       |
| Creates commits           | Hosts Pull Requests          |
| Creates branches          | Provides collaboration tools |
| Can work without internet | Usually requires internet    |

### Example

Git command:

```bash
git commit -m "Add login"
```

GitHub:

```text
Repository
    ↓
Pull Request
    ↓
Code Review
    ↓
Merge
```

---

# Why GitHub Collaboration is Important?

In a real company, many developers may work on the same project.

For example:

```text
Developer A → Authentication
Developer B → Payment
Developer C → Frontend
Developer D → Database
```

Everyone can work independently and later combine their work.

Without a proper collaboration workflow:

* Code can be overwritten.
* Conflicts can increase.
* Bugs can reach production.
* Developers may work on outdated code.
* It becomes difficult to know who changed what.

---

# Basic Collaboration Workflow

The common workflow is:

```text
GitHub Repository
       ↓
Clone Repository
       ↓
Create Branch
       ↓
Write Code
       ↓
Commit
       ↓
Push Branch
       ↓
Pull Request
       ↓
Code Review
       ↓
Changes Requested / Approved
       ↓
Merge
       ↓
Delete Branch
```

---

# Step 1: Clone Repository

Suppose your team has a GitHub repository.

Clone it:

```bash
git clone https://github.com/username/project.git
```

Move into the project:

```bash
cd project
```

Check remote:

```bash
git remote -v
```

---

# Step 2: Check Current Branch

```bash
git branch
```

You may see:

```text
* main
```

---

# Step 3: Update Local Repository

Before creating your feature branch:

```bash
git pull origin main
```

Or safer:

```bash
git fetch origin
git merge origin/main
```

---

# Step 4: Create a Feature Branch

Never directly develop a feature on `main` in a professional team unless the team's workflow specifically allows it.

Create a branch:

```bash
git switch -c feature/login
```

Check:

```bash
git branch
```

Example:

```text
* feature/login
  main
```

---

# Step 5: Write Your Code

Now implement your feature.

Example:

```text
feature/login

├── login.js
├── login.css
└── login.html
```

---

# Step 6: Check Your Changes

```bash
git status
```

Review exact changes:

```bash
git diff
```

---

# Step 7: Stage Changes

```bash
git add .
```

Or stage a specific file:

```bash
git add login.js
```

---

# Step 8: Commit Changes

```bash
git commit -m "Add login feature"
```

Good commit messages should clearly explain what changed.

Good:

```bash
git commit -m "Add JWT authentication"
```

Bad:

```bash
git commit -m "changes"
```

---

# Step 9: Push Feature Branch

```bash
git push origin feature/login
```

For the first push, you can use:

```bash
git push -u origin feature/login
```

`-u` sets the upstream branch.

After that:

```bash
git push
```

is usually enough.

---

# Step 10: Create Pull Request

After pushing, GitHub allows you to create a **Pull Request (PR)**.

A Pull Request means:

> "I have made changes on my branch. Please review them and consider merging them into another branch."

Example:

```text
feature/login
      ↓
Pull Request
      ↓
main
```

---

# What is a Pull Request?

A **Pull Request** is a GitHub feature used to propose changes and allow other developers to review those changes before merging.

PRs can contain:

* Code changes
* Description
* Comments
* Code review
* Review approvals
* Requested changes
* Automated CI checks

---

# Pull Request vs Git Pull

These are completely different.

### Pull Request

GitHub collaboration feature:

```text
feature/login → main
```

Used for:

* Code review
* Discussion
* Approval
* Merging

### Git Pull

Git command:

```bash
git pull
```

Used to:

* Download remote changes
* Merge them into your current branch

---

# Code Review

A reviewer checks:

* Is the code correct?
* Is it secure?
* Is it readable?
* Does it follow project standards?
* Are there unnecessary changes?
* Are tests included?
* Could this introduce bugs?

Example review:

```text
Reviewer:

"Please validate the email before saving the user."
```

Developer fixes it and pushes again:

```bash
git add .
git commit -m "Add email validation"
git push
```

The existing PR automatically updates.

---

# Pull Request Lifecycle

```text
Create PR
    ↓
CI Tests
    ↓
Code Review
    ↓
Changes Requested?
    ↓
Yes → Developer Fixes Code
    ↓
Push Again
    ↓
Review Again
    ↓
Approved
    ↓
Merge
```

---

# What Happens When You Push Again?

Suppose your PR already exists.

You make another change:

```bash
git add .
git commit -m "Fix validation"
git push
```

You **do not need to create another PR**.

The existing PR automatically receives the new commit.

---

# Merge Conflict

A merge conflict can happen when two developers modify the same part of the same file.

Example:

Developer A:

```javascript
const port = 3000;
```

Developer B:

```javascript
const port = 5000;
```

Git may not know which version to keep.

You may see:

```text
<<<<<<< HEAD
const port = 3000;
=======
const port = 5000;
>>>>>>> feature/login
```

You must manually decide which code should remain.

---

# Resolving a Merge Conflict

### Step 1

Open the conflicted file.

### Step 2

Find:

```text
<<<<<<<
=======
>>>>>>>
```

### Step 3

Choose the correct code.

### Step 4

Remove the conflict markers.

### Step 5

Stage the file:

```bash
git add .
```

### Step 6

Commit the resolution:

```bash
git commit -m "Resolve merge conflict"
```

### Step 7

Push:

```bash
git push
```

---

# Keeping Your Feature Branch Updated

Suppose `main` has new changes while you are working.

Fetch:

```bash
git fetch origin
```

Then update your branch.

Using merge:

```bash
git merge origin/main
```

Or using rebase:

```bash
git rebase origin/main
```

---

# Merge vs Rebase During Collaboration

## Merge

```bash
git fetch origin
git merge origin/main
```

Advantages:

* Doesn't rewrite existing commits.
* Safer for shared branches.

Disadvantage:

* Can create merge commits.

---

## Rebase

```bash
git fetch origin
git rebase origin/main
```

Advantages:

* Cleaner history.
* Linear history.

Disadvantage:

* Rewrites commit history.

### Important Rule

Avoid rebasing commits that other developers are already using unless your team explicitly follows a workflow that permits it.

---

# Fork-Based Collaboration

Sometimes you don't have direct write access to a repository.

You can use a **Fork**.

Workflow:

```text
Original Repository
        ↓
      Fork
        ↓
Your GitHub Repository
        ↓
Clone
        ↓
Create Branch
        ↓
Push
        ↓
Pull Request
        ↓
Original Repository
```

---

# What is a Fork?

A fork is your own GitHub copy of another repository.

Example:

```text
Original:

company/project
```

Your fork:

```text
moiz/project
```

You can modify your fork without having direct write access to the original repository.

---

# Fork vs Clone

| Fork                              | Clone                      |
| --------------------------------- | -------------------------- |
| GitHub-side copy                  | Local copy                 |
| Created on GitHub                 | Created on your computer   |
| Useful for external contributions | Used for local development |

---

# Origin vs Upstream

In fork-based workflows:

```text
origin
```

usually points to **your fork**.

```text
upstream
```

usually points to the **original repository**.

Example:

```bash
git remote -v
```

You may see:

```text
origin    https://github.com/moiz/project.git
upstream  https://github.com/company/project.git
```

---

# Add Upstream Remote

```bash
git remote add upstream https://github.com/company/project.git
```

Check:

```bash
git remote -v
```

---

# Sync Fork With Original Repository

Fetch original repository:

```bash
git fetch upstream
```

Update main:

```bash
git switch main
git merge upstream/main
```

Or:

```bash
git rebase upstream/main
```

Then update your fork:

```bash
git push origin main
```

---

# Team Collaboration Model

A company may use:

```text
main
 │
 ├── feature/login
 ├── feature/payment
 ├── feature/dashboard
 └── bugfix/auth
```

Developers work on separate branches.

When finished:

```text
feature/login
      ↓
Pull Request
      ↓
Code Review
      ↓
CI Tests
      ↓
main
```

---

# Branch Naming Convention

Use meaningful names.

Good:

```text
feature/login
feature/payment
feature/user-profile
bugfix/navbar
hotfix/payment-error
chore/update-dependencies
```

Bad:

```text
test
abc
mybranch
new
changes
```

---

# Protected Main Branch

Professional teams often protect important branches.

For example:

```text
main
```

may require:

* Pull Request
* Code review
* Passing CI tests
* No unresolved conflicts
* Required approvals

Developers may not be allowed to push directly to `main`.

---

# Why Protect Main?

Without protection:

```bash
git push origin main
```

could immediately put unreviewed code into the main branch.

Branch protection reduces this risk.

---

# CODEOWNERS

GitHub can use a `CODEOWNERS` file to define who should review certain files.

Example:

```text
/frontend/ @frontend-team
/backend/ @backend-team
```

This can automatically request reviews from responsible teams.

---

# GitHub Issues

Issues are used to track work.

Example:

```text
Issue #101

Add user authentication
```

Developer creates:

```text
feature/authentication
```

Then creates a PR.

The PR can reference the issue.

Example:

```text
Closes #101
```

When the PR is merged, GitHub can automatically close the issue.

---

# GitHub Actions in Collaboration

GitHub Actions can automatically run:

```text
Push
 ↓
Tests
 ↓
Lint
 ↓
Build
 ↓
Security Checks
```

This is called **CI (Continuous Integration)**.

Example:

```text
Developer
   ↓
Push
   ↓
GitHub
   ↓
GitHub Actions
   ↓
npm test
   ↓
npm run build
```

---

# Recommended Professional Workflow

```text
1. git clone
       ↓
2. git switch main
       ↓
3. git pull
       ↓
4. git switch -c feature/name
       ↓
5. Write Code
       ↓
6. git status
       ↓
7. git diff
       ↓
8. git add .
       ↓
9. git commit
       ↓
10. git push -u origin feature/name
       ↓
11. Create Pull Request
       ↓
12. Code Review
       ↓
13. CI Tests
       ↓
14. Fix Requested Changes
       ↓
15. Approval
       ↓
16. Merge
       ↓
17. Delete Feature Branch
```

---

# Important Commands

Clone:

```bash
git clone <repository-url>
```

Check remote:

```bash
git remote -v
```

Create branch:

```bash
git switch -c feature/login
```

Update branch:

```bash
git pull origin main
```

Check changes:

```bash
git diff
```

Stage:

```bash
git add .
```

Commit:

```bash
git commit -m "Add login feature"
```

Push:

```bash
git push -u origin feature/login
```

Fetch:

```bash
git fetch origin
```

Merge:

```bash
git merge origin/main
```

Rebase:

```bash
git rebase origin/main
```

Show branches:

```bash
git branch -a
```

Delete local branch:

```bash
git branch -d feature/login
```

---

# Best Practices

## 1. Never work directly on `main`

Use feature branches.

---

## 2. Pull Before Starting Work

```bash
git pull origin main
```

---

## 3. Keep Commits Small

Good:

```text
Add login API
Add password validation
Add login tests
```

Instead of:

```text
Complete entire project
```

---

## 4. Write Meaningful Commit Messages

Good:

```bash
git commit -m "Add JWT authentication"
```

Bad:

```bash
git commit -m "update"
```

---

## 5. Review Before Pushing

```bash
git diff
```

---

## 6. Don't Commit Secrets

Never commit:

```text
.env
passwords
API keys
private keys
credentials
```

Use `.gitignore`.

---

## 7. Keep PRs Small

Small PRs are easier to:

* Review
* Test
* Understand
* Merge

---

# Common Collaboration Problems

## Problem 1: Merge Conflict

Cause:

Two developers changed the same code.

Solution:

Resolve the conflict manually.

---

## Problem 2: Branch is Behind

Solution:

```bash
git fetch origin
git merge origin/main
```

or:

```bash
git rebase origin/main
```

---

## Problem 3: Accidentally Committed Secret

Do not simply delete the file and assume the secret is gone from Git history.

If the secret is real:

1. Revoke/rotate the secret immediately.
2. Remove it from the repository.
3. Clean Git history if necessary.

---

## Problem 4: Someone Pushed Directly to Main

Professional solution:

Use branch protection and require Pull Requests.

---

# GitHub Collaboration vs Shared Folder

| GitHub Collaboration | Shared Folder                |
| -------------------- | ---------------------------- |
| Version control      | Usually weak version control |
| Branches             | Usually no branches          |
| Pull Requests        | No PR workflow               |
| Code review          | Limited                      |
| Conflict management  | Difficult                    |
| Full commit history  | Usually limited              |

---

# Interview Questions

### Q1. What is GitHub Collaboration?

**Answer:**

It is a workflow where multiple developers use Git and GitHub to develop, review, test, and merge code safely.

---

### Q2. What is a Pull Request?

**Answer:**

A Pull Request is a GitHub request to merge changes from one branch into another after review and testing.

---

### Q3. Why should developers use feature branches?

**Answer:**

They isolate work so developers can work independently without directly affecting the main branch.

---

### Q4. What is the difference between Git Pull and Pull Request?

**Answer:**

`git pull` is a Git command for downloading and integrating remote changes.

A Pull Request is a GitHub collaboration mechanism for reviewing and merging code.

---

### Q5. What is a fork?

**Answer:**

A fork is a GitHub-side copy of another repository under your own account.

---

### Q6. What is the difference between `origin` and `upstream`?

**Answer:**

In a fork workflow, `origin` usually points to your fork, while `upstream` points to the original repository.

---

### Q7. Why protect the main branch?

**Answer:**

To prevent unreviewed or failing code from being directly pushed into an important branch.

---

### Q8. What happens after you push more commits to an existing PR?

**Answer:**

The existing Pull Request automatically updates with those new commits.

---

### Q9. How do you resolve a merge conflict?

**Answer:**

Edit the conflicted files, remove conflict markers, choose the correct code, stage the files, commit the resolution, and push.

---

### Q10. Why are small Pull Requests preferred?

**Answer:**

They are easier to review, test, understand, and merge.

---

# Scenario-Based Questions

### Scenario 1

You are working on login functionality.

Should you directly modify `main`?

**Answer:**

Usually no.

Create:

```bash
git switch -c feature/login
```

---

### Scenario 2

Your teammate pushed changes to `main` while you were working.

What should you do?

```bash
git fetch origin
git merge origin/main
```

Or use your team's approved rebase workflow:

```bash
git fetch origin
git rebase origin/main
```

---

### Scenario 3

Your PR has a merge conflict.

What should you do?

Resolve the conflict locally, test the project, commit the resolution, and push the branch.

---

### Scenario 4

You don't have permission to push to the original repository.

What workflow can you use?

```text
Fork
 ↓
Clone
 ↓
Feature Branch
 ↓
Push to Fork
 ↓
Pull Request
 ↓
Original Repository
```

---

# MCQs

### MCQ 1

What is mainly used for code review on GitHub?

A. Git Clone

B. Pull Request

C. Git Reset

D. Git Stash

**Answer: B**

---

### MCQ 2

What should normally contain production-ready code?

A. Feature branch

B. Temporary branch

C. Main branch

D. Stash

**Answer: C**

---

### MCQ 3

Which command creates and switches to a new branch?

A.

```bash
git branch -d feature
```

B.

```bash
git switch -c feature
```

C.

```bash
git merge feature
```

D.

```bash
git fetch feature
```

**Answer: B**

---

### MCQ 4

What is a fork?

A. Local commit

B. Git command

C. GitHub copy of a repository

D. Merge conflict

**Answer: C**

---

### MCQ 5

What usually points to your fork?

A. `HEAD`

B. `main`

C. `origin`

D. `stash`

**Answer: C**

---

# True / False

### 1.

Multiple developers can work on different branches of the same GitHub repository.

**True**

### 2.

A Pull Request and `git pull` are the same thing.

**False**

### 3.

A Pull Request can contain code review comments.

**True**

### 4.

A developer should always push directly to `main`.

**False**

### 5.

A fork is created on GitHub.

**True**

### 6.

A clone creates a local copy of a repository.

**True**

### 7.

Pushing additional commits to an existing PR creates a new PR automatically.

**False**

### 8.

Branch protection can require Pull Requests before merging.

**True**

### 9.

Merge conflicts can occur when developers modify the same part of a file.

**True**

### 10.

You should commit passwords and API keys to GitHub.

**False**

---

# Golden Interview Answer

If an interviewer asks:

**"Explain your GitHub collaboration workflow."**

A strong answer is:

> "I normally start by updating the main branch and creating a feature branch for my work. I make small, meaningful commits, review my changes with `git diff`, and push the feature branch to GitHub. Then I create a Pull Request, where CI checks and code review take place. If reviewers request changes, I update the same branch and push again. Once the PR is approved and all checks pass, it is merged into the main branch. For conflicts, I fetch the latest changes, resolve them locally, test the application, and push the resolution."

---

# Quick Revision

```text
Clone
 ↓
Pull latest code
 ↓
Create Feature Branch
 ↓
Code
 ↓
git status
 ↓
git diff
 ↓
git add
 ↓
git commit
 ↓
git push
 ↓
Pull Request
 ↓
Code Review
 ↓
CI Tests
 ↓
Resolve Changes/Conflicts
 ↓
Approval
 ↓
Merge
 ↓
Delete Branch
```

# Most Important Commands

```bash
git clone <url>

git switch main

git pull origin main

git switch -c feature/login

git status

git diff

git add .

git commit -m "Add login feature"

git push -u origin feature/login

git fetch origin

git merge origin/main

git push

git branch -d feature/login
```

> **Core concept to remember:**
> **Branch → Code → Commit → Push → Pull Request → Review → CI → Merge**
