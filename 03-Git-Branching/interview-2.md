# Git Interview Questions - Part 2

## Advanced, Scenario, Puzzle, FAANG Level & Quiz (Questions 51–100)

> This part focuses on **real interview scenarios**, advanced concepts, debugging situations, Git internals, and practical problems related to Branch, Switch, Checkout, and Merge.

---

# Advanced Level Questions (Q51–Q65)

### Q51. Why are Git branches implemented as pointers instead of complete copies?

### Q52. What happens internally when you run:

```bash
git branch feature-login
```

### Q53. Explain the relationship between a branch reference and a commit object.

### Q54. What happens internally when you run:

```bash
git switch feature-login
```

### Q55. How does Git know which files should change when switching branches?

### Q56. Explain the difference between HEAD pointing to a branch and HEAD pointing directly to a commit.

### Q57. What is the role of the index (staging area) during branch switching?

### Q58. What happens if you try to switch branches with uncommitted changes?

### Q59. How does Git prevent data loss during branch switching?

### Q60. Why is `git checkout` considered a multi-purpose command?

### Q61. Why is separating `git checkout` into `git switch` and `git restore` better?

### Q62. Explain the internal process of a merge operation.

### Q63. What is a merge base and why is it important?

### Q64. Why can Git automatically merge some files but not others?

### Q65. Why do large teams prefer short-lived feature branches?

---

# Real-World Scenario Questions (Q66–Q80)

### Q66. A developer accidentally commits directly to the main branch. How would you fix the workflow?

---

### Q67. You created a feature branch but your teammate pushed changes to main. How do you update your branch?

---

### Q68. Your team has 50 developers. Which branching strategy would you recommend and why?

---

### Q69. A developer deletes a branch before merging. How can you recover the work?

---

### Q70. You switched branches and Git says your local changes will be overwritten. What should you do?

---

### Q71. Your merge creates conflicts in 20 files. How will you resolve them safely?

---

### Q72. Production has a bug after merging a feature branch. What steps will you take?

---

### Q73. A developer uses force push after rewriting branch history. Other developers have problems. How do you recover?

---

### Q74. You need to bring only one commit from another branch. Would you use merge?

---

### Q75. A feature branch is six months old and has hundreds of commits. What problems can occur?

---

### Q76. Two developers frequently modify the same file. How can the team reduce conflicts?

---

### Q77. You accidentally merged the wrong branch into main. How would you undo it safely?

---

### Q78. A junior developer asks why branches are needed. How would you explain with a real example?

---

### Q79. Your company wants a clean production history. Would you use normal merge or `--no-ff` merge?

---

### Q80. A developer says:

"Branch deletion deletes my code."

How would you explain whether this is true or false?

---

# Puzzle-Based Questions (Q81–Q90)

## Puzzle 1

Current history:

```text
A ---- B ---- C (main)
              \
               D ---- E (feature)
```

Command:

```bash
git switch main
git merge feature
```

Questions:

1. Is fast-forward possible?
2. Will Git create a merge commit?
3. Draw the final graph.

---

## Puzzle 2

History:

```text
A ---- B ---- C ---- D (main)

       \
        E ---- F (feature)
```

Both branches changed the same file.

Questions:

1. What type of merge will happen?
2. Why can Git not automatically merge?
3. What must the developer do?

---

## Puzzle 3

Command:

```bash
git checkout abc123
```

Questions:

1. Is HEAD attached to a branch?
2. What Git state is created?
3. How can you save new work permanently?

---

## Puzzle 4

A developer runs:

```bash
git branch new-feature
```

Then checks:

```bash
git branch
```

Question:

Why is the developer still on the old branch?

---

## Puzzle 5

A branch contains:

```text
A ---- B ---- C ---- D
```

The branch pointer is deleted.

Questions:

1. Are commits immediately deleted?
2. Can Git recover them?
3. Which Git feature helps?

---

# FAANG-Level Interview Questions (Q91–Q95)

### Q91. Design a Git branching strategy for a company with 1000 developers.

---

### Q92. Explain why Git branches scale better than traditional version control branches.

---

### Q93. How would you handle a situation where two teams are developing conflicting features on the same codebase?

---

### Q94. Explain Git merge from an internal object-model perspective.

---

### Q95. Compare Git Flow, GitHub Flow, and Trunk-Based Development.

---

# Debugging Questions (Q96–Q100)

### Q96. You see this error:

```text
Your local changes would be overwritten by checkout
```

How do you fix it?

---

### Q97. You see:

```text
CONFLICT (content): Merge conflict in app.js
```

What steps do you perform?

---

### Q98. You accidentally created a branch from the wrong branch. How do you fix it?

---

### Q99. You merged a feature branch but forgot to pull the latest main changes first. What problems can happen?

---

### Q100. Your Git history is full of unnecessary merge commits. How would you improve it?

---

# Final Interview Quiz

## Multiple Choice Questions

### MCQ 1

A branch in Git is:

A. A complete project copy
B. A pointer to a commit
C. A separate database
D. A backup folder

**Answer: B**

---

### MCQ 2

Which command creates and switches a branch?

A. git branch -c
B. git switch -c
C. git merge -c
D. git create branch

**Answer: B**

---

### MCQ 3

Which command shows commit history graph?

A. git graph
B. git history
C. git log --graph
D. git branch graph

**Answer: C**

---

### MCQ 4

A merge conflict occurs when:

A. Git is broken
B. Internet is unavailable
C. Git cannot automatically combine changes
D. Branch is deleted

**Answer: C**

---

### MCQ 5

Which command aborts a merge?

A. git stop merge
B. git merge --abort
C. git cancel
D. git reset merge

**Answer: B**

---

# True / False

1. Git branches are lightweight references.

**True**

---

2. `git switch` creates commits automatically.

**False**

---

3. `git merge` combines branches.

**True**

---

4. `git checkout` can move to old commits.

**True**

---

5. Fast-forward merge creates a merge commit.

**False**

---

6. Merge conflicts are always Git errors.

**False**

---

7. A deleted branch always deletes commits immediately.

**False**

---

8. HEAD represents the current location in Git.

**True**

---

9. `git branch feature` automatically switches to feature.

**False**

---

10. Short-lived branches reduce merge conflicts.

**True**

---

# Interview Closing Revision

Remember these core concepts:

```
Branch  → Creates independent development line

Switch  → Move between branches

Checkout → Old multi-purpose command

Merge   → Combine branch histories

Conflict → Manual decision required

HEAD    → Current Git position
```

---

**End of Git Interview Guide (Questions 1–100)**

