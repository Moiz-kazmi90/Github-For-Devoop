# Merge Pull Request Method — Open Source Contribution

# What is Open Source Contribution?

**Open Source Contribution** means helping an open-source project by improving its code, documentation, tests, bugs, features, or other project resources.

Anyone can potentially contribute to an open-source project if the project allows external contributions.

Examples of contributions:

* Fixing bugs
* Adding features
* Improving documentation
* Adding tests
* Fixing typos
* Improving performance
* Improving accessibility
* Reporting bugs
* Reviewing Pull Requests

---

# What is the Merge Pull Request Method?

The **Merge Pull Request Method** is a common way to contribute to an open-source GitHub project.

The contributor creates changes in their own branch or fork, pushes those changes to GitHub, and creates a **Pull Request (PR)** to request that the project maintainers review and merge the changes.

**Simple Definition**

> **The Merge Pull Request Method is an open-source workflow where a contributor creates changes, pushes them to GitHub, opens a Pull Request, gets the changes reviewed, and finally merges them into the project's target branch.**

---

# Why is Pull Request Method Used?

Suppose you find a bug in an open-source project.

You should not normally directly modify the project's `main` branch.

Instead:

```text
Open Source Project
        ↓
Fork
        ↓
Clone
        ↓
Create Feature Branch
        ↓
Make Changes
        ↓
Commit
        ↓
Push
        ↓
Pull Request
        ↓
Code Review
        ↓
Approval
        ↓
Merge
```

This protects the main project from unreviewed code.

---

# Important Terms

## 1. Original Repository

The original project repository owned by the project maintainers.

Example:

```text
https://github.com/company/project
```

Usually called:

```text
upstream
```

---

## 2. Fork

A **fork** is your own GitHub copy of another repository.

Example:

```text
Original Repository

company/project

        ↓ Fork

Your Repository

moiz/project
```

You can push your changes to your fork without needing write permission to the original repository.

---

## 3. Clone

Clone downloads the repository to your computer.

```bash
git clone <repository-url>
```

---

## 4. Origin

In a fork workflow, `origin` usually points to **your fork**.

Example:

```text
origin → https://github.com/moiz/project.git
```

---

## 5. Upstream

`upstream` usually points to the **original project**.

Example:

```text
upstream → https://github.com/company/project.git
```

---

## 6. Feature Branch

A separate branch where you implement your contribution.

Example:

```text
feature/fix-login
```

---

## 7. Pull Request

A Pull Request asks the project maintainers to review your changes and potentially merge them into the original repository.

---

# Complete Open Source Workflow

```text
Original Repository
        ↓
       Fork
        ↓
   Your GitHub Fork
        ↓
      Clone
        ↓
Add Upstream
        ↓
Create Feature Branch
        ↓
Make Changes
        ↓
Run Tests
        ↓
Commit
        ↓
Push to Fork
        ↓
Create Pull Request
        ↓
Code Review
        ↓
Fix Requested Changes
        ↓
Push Again
        ↓
Approval
        ↓
Merge
```

---

# Step 1 — Find an Open Source Project

Find a project you understand and want to contribute to.

Before contributing, read:

```text
README.md
CONTRIBUTING.md
CODE_OF_CONDUCT.md
LICENSE
```

Pay special attention to:

```text
CONTRIBUTING.md
```

It may tell you:

* Branch naming rules
* Commit message rules
* Testing requirements
* Coding standards
* PR requirements
* Issue workflow

---

# Step 2 — Fork the Repository

On GitHub, click:

```text
Fork
```

You now have your own copy.

Example:

```text
Original:

open-source/project

Your Fork:

Moiz-kazmi90/project
```

---

# Step 3 — Clone Your Fork

Clone **your fork**, not necessarily the original repository.

```bash
git clone https://github.com/YOUR-USERNAME/project.git
```

Then:

```bash
cd project
```

---

# Step 4 — Check Remote

```bash
git remote -v
```

You may see:

```text
origin  https://github.com/YOUR-USERNAME/project.git
```

---

# Step 5 — Add Upstream

Add the original repository:

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git
```

Check:

```bash
git remote -v
```

Expected:

```text
origin    https://github.com/YOUR-USERNAME/project.git
upstream  https://github.com/ORIGINAL-OWNER/project.git
```

---

# Origin vs Upstream

Remember:

```text
origin
   ↓
Your Fork

upstream
   ↓
Original Project
```

This is one of the most important concepts in open-source contribution.

---

# Step 6 — Update Your Local Main

Before starting work:

```bash
git fetch upstream
```

Switch to main:

```bash
git switch main
```

Update it:

```bash
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

# Step 7 — Create a Feature Branch

Never make your contribution directly on `main`.

Create a new branch:

```bash
git switch -c fix/login-validation
```

Check:

```bash
git branch
```

---

# Good Branch Names

```text
feature/add-search
fix/login-validation
bugfix/navbar-error
docs/update-installation
test/add-auth-tests
refactor/user-service
```

Avoid:

```text
test
new
mybranch
changes
abc
```

---

# Step 8 — Make Your Changes

Now modify the project.

Example:

```text
src/
├── auth/
│   ├── login.js
│   └── validation.js
```

You fix a validation bug.

---

# Step 9 — Check Your Changes

Check status:

```bash
git status
```

Review exact changes:

```bash
git diff
```

Check staged changes:

```bash
git diff --staged
```

---

# Step 10 — Run Tests

Before creating a PR, run the project's tests.

For a Node.js project:

```bash
npm install
npm test
```

Depending on the project, you may also run:

```bash
npm run lint
```

or:

```bash
npm run build
```

Always follow the project's `CONTRIBUTING.md`.

---

# Step 11 — Stage Changes

```bash
git add .
```

Or stage specific files:

```bash
git add src/auth/validation.js
```

---

# Step 12 — Commit

Create a meaningful commit:

```bash
git commit -m "Fix login validation"
```

Good:

```text
Fix login validation
Add authentication tests
Update installation documentation
```

Bad:

```text
changes
update
final
done
```

---

# Step 13 — Push to Your Fork

```bash
git push -u origin fix/login-validation
```

Now your branch exists on your GitHub fork.

---

# Step 14 — Create Pull Request

Go to GitHub.

You should see an option to create a Pull Request.

The important direction is:

```text
Your Fork
    ↓
Your Branch
    ↓
Original Repository
    ↓
Target Branch
```

Example:

```text
Moiz/project
fix/login-validation
        ↓
original/project
main
```

---

# Important PR Concept

A Pull Request has:

```text
FROM:

your branch

TO:

target branch
```

Example:

```text
fix/login-validation
          ↓
        main
```

---

# What Should a Good PR Description Contain?

A good PR should explain:

## What changed?

```text
Fixed login validation.
```

## Why was it needed?

```text
Users could submit empty email fields.
```

## How was it fixed?

```text
Added server-side email validation.
```

## How was it tested?

```text
Added unit tests and ran npm test.
```

---

# Example PR Structure

```text
Title:

Fix login email validation

Description:

## What changed?
Added email validation to the login endpoint.

## Why?
Empty email values were accepted.

## Testing
- Added unit tests
- npm test passed

## Related Issue
Closes #123
```

---

# Step 15 — Code Review

Maintainers review your Pull Request.

They may:

```text
Approve
```

or:

```text
Request Changes
```

or:

```text
Comment
```

They may ask:

```text
Please add tests for invalid email addresses.
```

---

# Step 16 — Fix Review Comments

Make the requested changes locally.

```bash
git add .
git commit -m "Add email validation tests"
```

Push:

```bash
git push
```

The existing PR automatically updates.

You **do not create another PR**.

---

# Step 17 — CI Checks

Many open-source projects use CI.

Example:

```text
Pull Request
     ↓
GitHub Actions
     ↓
Lint
     ↓
Tests
     ↓
Build
     ↓
Security Checks
```

You may see:

```text
✓ Tests passed
✓ Build passed
✓ Lint passed
```

If CI fails, fix the problem and push again.

---

# Step 18 — Merge

After:

```text
Code Review ✓
CI Tests ✓
Maintainer Approval ✓
```

The maintainer can merge the Pull Request.

Possible merge methods include:

```text
Merge Commit
Squash and Merge
Rebase and Merge
```

---

# Merge Commit

Example:

```text
A ---- B ---- C
       \      /
        D ---- E
```

Git creates a merge commit that combines the histories.

---

# Squash and Merge

Suppose your PR has:

```text
Commit 1
Commit 2
Commit 3
Commit 4
```

Squash can combine them into:

```text
One Clean Commit
```

Example:

```text
Add login validation
```

This keeps the main branch history cleaner.

---

# Rebase and Merge

Your commits are replayed onto the target branch.

Example:

```text
main:

A ---- B ---- C

feature:

A ---- B ---- D ---- E
```

After rebase/merge, history can become:

```text
A ---- B ---- C ---- D' ---- E'
```

---

# Merge Method Comparison

| Method       | Result                   | Common Use                      |
| ------------ | ------------------------ | ------------------------------- |
| Merge Commit | Preserves branch history | Teams wanting full history      |
| Squash Merge | Combines PR commits      | Clean main history              |
| Rebase Merge | Linear history           | Teams preferring linear history |

---

# What Happens After Merge?

After the PR is merged:

```text
Feature Branch
      ↓
Merged
      ↓
Main
```

The feature branch may be deleted.

You can delete your local branch:

```bash
git switch main
git branch -d fix/login-validation
```

Delete remote branch:

```bash
git push origin --delete fix/login-validation
```

---

# Sync Your Fork After Merge

Update from upstream:

```bash
git fetch upstream
```

Switch main:

```bash
git switch main
```

Update:

```bash
git merge upstream/main
```

Push:

```bash
git push origin main
```

Now:

```text
Your Fork main
        =
Original Repository main
```

---

# Complete Command Workflow

```bash
# Clone your fork
git clone https://github.com/YOUR-USERNAME/project.git

# Enter project
cd project

# Add original repository
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git

# Check remotes
git remote -v

# Get latest upstream changes
git fetch upstream

# Switch to main
git switch main

# Update local main
git merge upstream/main

# Update your fork
git push origin main

# Create feature branch
git switch -c fix/login-validation

# Make changes

# Check changes
git status
git diff

# Stage
git add .

# Commit
git commit -m "Fix login validation"

# Push branch
git push -u origin fix/login-validation

# Create Pull Request on GitHub

# After review/fixes
git add .
git commit -m "Add validation tests"
git push
```

---

# What If You Don't Fork?

If you have direct write permission to the repository, you may not need a fork.

Workflow:

```text
Original Repository
        ↓
Clone
        ↓
Feature Branch
        ↓
Push
        ↓
Pull Request
        ↓
Review
        ↓
Merge
```

But for many external open-source contributions, the **fork workflow** is common.

---

# What If Your Branch Becomes Outdated?

Suppose:

```text
Your Branch
    ↓
Old
```

while:

```text
upstream/main
    ↓
New commits
```

Update:

```bash
git fetch upstream
```

Then:

```bash
git rebase upstream/main
```

or:

```bash
git merge upstream/main
```

Then push.

If you rebased a branch that was already pushed, you may need:

```bash
git push --force-with-lease
```

### Important

Prefer:

```bash
git push --force-with-lease
```

over:

```bash
git push --force
```

because `--force-with-lease` provides a safer check against overwriting someone else's newer remote work.

---

# Merge Conflict During Open Source Contribution

Suppose upstream changed:

```text
src/login.js
```

and you changed the same lines.

You may get:

```text
CONFLICT
```

Check:

```bash
git status
```

Open the conflicted file.

You may see:

```text
<<<<<<< HEAD
your code
=======
upstream code
>>>>>>> upstream/main
```

Choose the correct code and remove:

```text
<<<<<<<
=======
>>>>>>>
```

Then:

```bash
git add .
```

If using merge:

```bash
git commit
```

If using rebase:

```bash
git rebase --continue
```

Finally:

```bash
git push
```

If the branch was rebased and already pushed:

```bash
git push --force-with-lease
```

---

# Issue-Based Contribution

A professional open-source workflow often starts with an issue.

```text
Issue
  ↓
Discuss
  ↓
Assign
  ↓
Fork
  ↓
Branch
  ↓
Code
  ↓
Pull Request
  ↓
Review
  ↓
Merge
```

Example:

```text
Issue #250

"Login fails when email contains uppercase characters."
```

You fix it and create:

```text
fix/case-insensitive-email
```

PR:

```text
Fix case-insensitive email validation
```

---

# Linking PR to an Issue

You can use:

```text
Closes #250
```

or:

```text
Fixes #250
```

When the PR is merged, GitHub can automatically close the referenced issue.

---

# Good Open Source Contribution Rules

## 1. Read CONTRIBUTING.md

Always check project instructions first.

---

## 2. Don't Make Huge Unrelated Changes

If you are fixing login validation, don't also change:

```text
README
CSS
Database
Docker
CI
```

unless necessary.

Keep the PR focused.

---

## 3. Don't Change Formatting Unnecessarily

Avoid changing hundreds of lines just because your editor reformatted the file.

It makes review harder.

---

## 4. Write Tests

If your contribution changes behavior, add tests when appropriate.

---

## 5. Keep Commits Meaningful

Good:

```text
Fix email validation
Add login validation tests
```

---

## 6. Be Respectful During Review

Code review is about improving the project, not attacking the developer.

---

## 7. Don't Include Secrets

Never commit:

```text
.env
API keys
passwords
private keys
cloud credentials
```

---

# Common Beginner Mistakes

### Mistake 1

Working directly on `main`.

Better:

```bash
git switch -c feature/my-feature
```

---

### Mistake 2

Cloning the original repository without having permission to push.

Better:

```text
Fork → Clone Fork
```

---

### Mistake 3

Forgetting `upstream`.

Add:

```bash
git remote add upstream <original-repository-url>
```

---

### Mistake 4

Creating a new PR for every requested change.

Don't.

Simply:

```bash
git add .
git commit -m "Address review comments"
git push
```

The existing PR updates.

---

### Mistake 5

Using `git push --force` carelessly.

Prefer:

```bash
git push --force-with-lease
```

when force-pushing is actually required.

---

# Real-World Example

Imagine an open-source Node.js project.

You find Issue #100:

```text
"Password validation accepts passwords shorter than 8 characters."
```

You decide to fix it.

### Step 1

Fork repository.

### Step 2

Clone:

```bash
git clone <your-fork>
```

### Step 3

Add upstream:

```bash
git remote add upstream <original-repository>
```

### Step 4

Update:

```bash
git fetch upstream
git switch main
git merge upstream/main
```

### Step 5

Create branch:

```bash
git switch -c fix/password-validation
```

### Step 6

Fix code.

### Step 7

Run tests:

```bash
npm test
```

### Step 8

Commit:

```bash
git add .
git commit -m "Fix minimum password length validation"
```

### Step 9

Push:

```bash
git push -u origin fix/password-validation
```

### Step 10

Create PR:

```text
fix/password-validation
        ↓
original-project/main
```

### Step 11

Maintainer reviews.

### Step 12

They request tests.

Add tests:

```bash
git add .
git commit -m "Add password validation tests"
git push
```

### Step 13

CI passes.

### Step 14

Maintainer approves.

### Step 15

PR is merged.

### Step 16

Update local repository:

```bash
git switch main
git fetch upstream
git merge upstream/main
git push origin main
```

---

# Interview Questions

### Q1. What is open-source contribution?

**Answer:**

Contributing code, documentation, tests, bug fixes, or other improvements to a publicly available project.

---

### Q2. Why do we use forks?

**Answer:**

A fork gives contributors their own GitHub copy where they can push changes without requiring write access to the original repository.

---

### Q3. What is the difference between origin and upstream?

**Answer:**

In a fork workflow, `origin` normally points to your fork and `upstream` points to the original repository.

---

### Q4. Why should you create a feature branch?

**Answer:**

To isolate your contribution from the main branch and make the change easier to review.

---

### Q5. What is a Pull Request?

**Answer:**

A request to merge changes from one branch into another after review and testing.

---

### Q6. What happens when reviewers request changes?

**Answer:**

You modify the same branch, commit the fixes, and push them. The existing Pull Request automatically updates.

---

### Q7. What is the difference between Merge, Squash Merge, and Rebase Merge?

**Answer:**

* **Merge:** Preserves branch history and can create a merge commit.
* **Squash:** Combines PR commits into one commit.
* **Rebase:** Produces a linear history by replaying commits.

---

### Q8. Why should you read `CONTRIBUTING.md`?

**Answer:**

It contains project-specific rules for contributing, such as coding standards, tests, branch naming, commit format, and PR requirements.

---

# Scenario Questions

### Scenario 1

You don't have write permission to an open-source repository.

What should you do?

```text
Fork
 ↓
Clone Fork
 ↓
Branch
 ↓
Code
 ↓
Push
 ↓
Pull Request
```

---

### Scenario 2

A maintainer requests changes to your PR.

Should you create another PR?

**Answer:**

No. Modify the same branch, commit the changes, and push again.

---

### Scenario 3

Your branch is behind `upstream/main`.

What should you do?

```bash
git fetch upstream
git rebase upstream/main
```

or use merge:

```bash
git fetch upstream
git merge upstream/main
```

Follow the project's contribution rules.

---

### Scenario 4

You rebased an already-pushed PR branch.

Normal push is rejected.

What may be required?

```bash
git push --force-with-lease
```

---

# Quick Revision

```text
FORK
 ↓
CLONE
 ↓
ADD UPSTREAM
 ↓
FETCH UPSTREAM
 ↓
UPDATE MAIN
 ↓
CREATE FEATURE BRANCH
 ↓
CODE
 ↓
TEST
 ↓
COMMIT
 ↓
PUSH TO FORK
 ↓
CREATE PULL REQUEST
 ↓
CODE REVIEW
 ↓
FIX REQUESTED CHANGES
 ↓
CI PASSES
 ↓
APPROVAL
 ↓
MERGE
 ↓
SYNC FORK
```

---

# Most Important Commands

```bash
# Clone your fork
git clone <your-fork-url>

# Add original repository
git remote add upstream <original-repository-url>

# Check remotes
git remote -v

# Fetch original repository
git fetch upstream

# Update main
git switch main
git merge upstream/main

# Create feature branch
git switch -c feature/my-feature

# Check changes
git status
git diff

# Stage
git add .

# Commit
git commit -m "Add my contribution"

# Push
git push -u origin feature/my-feature

# Delete local branch after merge
git branch -d feature/my-feature

# Delete remote branch
git push origin --delete feature/my-feature
```

---

# One-Line Interview Definition

> **The Merge Pull Request Method is an open-source contribution workflow where a contributor forks or branches a project, makes and tests changes, pushes them to GitHub, creates a Pull Request, receives code review and CI checks, fixes requested changes, and finally has the contribution merged into the project's target branch.**
