# Git Interview Questions

## Topic: `git reset`, `git restore`, and `git revert`

---

# Beginner Level

### Q1. What is `git restore`?

### Q2. What is `git reset`?

### Q3. What is `git revert`?

### Q4. Which command is used to restore a file?

### Q5. Which command moves HEAD?

### Q6. Which command creates a new commit?

### Q7. Which command is safest after pushing commits?

### Q8. Which command changes commit history?

### Q9. Which command restores deleted tracked files?

### Q10. Which command unstages files?

### Q11. What is the default mode of `git reset`?

### Q12. Explain `HEAD` in Git.

### Q13. What is the staging area?

### Q14. What is the working directory?

### Q15. What is the Git repository?

---

# Intermediate Level

### Q16. Explain the difference between `git reset --soft`, `--mixed`, and `--hard`.

### Q17. Why was `git restore` introduced?

### Q18. Why is `git revert` considered safer than `git reset`?

### Q19. What happens internally when `git revert` is executed?

### Q20. Can `git restore` recover an untracked file?

### Q21. Does `git reset` delete commits forever?

### Q22. What happens if you run `git reset --hard`?

### Q23. What happens to staged files after `git reset --mixed`?

### Q24. Can `git revert` revert multiple commits?

### Q25. What happens if the reverted commit causes merge conflicts?

### Q26. Explain how `git restore --staged` works.

### Q27. When should you avoid using `git reset --hard`?

### Q28. Which command is best for local development?

### Q29. Which command is best for shared repositories?

### Q30. Can `git revert` be reverted?

---

# Advanced Level

### Q31. Explain how Git changes the commit graph after `git revert`.

### Q32. Why does `git reset` rewrite history?

### Q33. What exactly changes when HEAD moves?

### Q34. Explain how Git stores commits internally.

### Q35. Does `git restore` affect Git objects?

### Q36. Explain how reflog helps after `git reset --hard`.

### Q37. Can a lost commit be recovered?

### Q38. Explain the difference between branch pointer and HEAD.

### Q39. What happens if you run `git reset --hard` while having untracked files?

### Q40. How does Git know which commit to revert?

### Q41. Explain detached HEAD and its relation with reset.

### Q42. Why does Git recommend `git revert` after pushing?

### Q43. Explain why reset is dangerous on shared branches.

### Q44. Explain the internal workflow of `git revert`.

### Q45. Explain how Git generates a reverse patch during revert.

---

# Conceptual Questions

### Q46. Why doesn't `git revert` remove the original commit?

### Q47. Why is rewriting Git history dangerous?

### Q48. Why is preserving history important?

### Q49. Why should beginners prefer `git restore` over `git checkout`?

### Q50. Why is `git reset --hard` called destructive?

### Q51. Why is `git revert` considered an audit-friendly command?

### Q52. Why is every Git command designed differently instead of one undo command?

### Q53. Why can Git restore deleted files?

### Q54. Why can't Git restore untracked files?

### Q55. Why does `git revert` need a commit ID?

---

# Real-World Scenario Questions

### Scenario 1

You edited ten files.

Only one file should go back to the previous version.

Which command will you use?

---

### Scenario 2

You committed the wrong code.

The commit has **not** been pushed.

What will you do?

---

### Scenario 3

You pushed buggy code to GitHub.

Fifty developers already pulled it.

How will you fix it?

---

### Scenario 4

A junior developer accidentally ran:

```bash
git reset --hard
```

How would you recover the lost commit?

---

### Scenario 5

You accidentally staged 200 files.

How do you unstage them without deleting your work?

---

### Scenario 6

A production deployment failed because of yesterday's commit.

Management wants the previous version immediately.

Which Git command is safest?

---

### Scenario 7

You committed API keys.

The repository has not been pushed.

Which command would you choose?

---

### Scenario 8

You committed sensitive data.

The repository has already been pushed.

What steps should you take?

---

### Scenario 9

You deleted a tracked file accidentally.

How do you recover it?

---

### Scenario 10

You modified a file but want to keep only half the changes.

Would `git restore` be the correct choice?

Why?

---

# Puzzle-Based Questions

### Puzzle 1

History

```
A → B → C → D
```

HEAD points to D.

You run:

```bash
git reset --soft HEAD~2
```

Questions:

* Which commit becomes HEAD?
* Which commits disappear from the branch?
* Are your file changes still available?
* Are they staged?

---

### Puzzle 2

History

```
A → B → C
```

Run

```bash
git revert B
```

Questions:

* Is Commit B removed?
* What will the new history look like?

---

### Puzzle 3

You execute

```bash
git restore app.js
```

Questions:

* Does HEAD move?
* Is a commit created?
* Does Git history change?

---

### Puzzle 4

History

```
A → B → C
```

You run

```bash
git reset --hard A
```

Questions:

* Which commits disappear from the branch?
* Can they still be recovered?

---

### Puzzle 5

Two developers cloned the same repository.

Developer A runs:

```bash
git reset --hard HEAD~3
git push --force
```

Developer B already has those commits.

Question:

What problems will Developer B face?

---

# Command Prediction Questions

Predict the output.

### Question 1

```
git reset --soft HEAD~1
```

---

### Question 2

```
git reset --mixed HEAD~1
```

---

### Question 3

```
git reset --hard HEAD~1
```

---

### Question 4

```
git restore app.js
```

---

### Question 5

```
git restore --staged app.js
```

---

### Question 6

```
git revert HEAD
```

---

# True or False

1. `git revert` deletes commits.

2. `git restore` creates commits.

3. `git reset --hard` deletes local changes.

4. `git reset` moves HEAD.

5. `git revert` is recommended after pushing.

6. `git restore` changes Git history.

7. `git reset --soft` keeps staged changes.

8. `git reset --mixed` unstages files.

9. `git restore` can restore tracked files.

10. `git revert` preserves commit history.

---

# Multiple Choice Questions

### MCQ 1

Which command creates a new commit?

A. git restore

B. git reset

C. git revert

D. git clean

---

### MCQ 2

Which reset mode removes commits while keeping staged changes?

A. --hard

B. --soft

C. --mixed

D. restore

---

### MCQ 3

Which command is safest after pushing?

A. reset

B. restore

C. revert

D. checkout

---

### MCQ 4

Which command changes HEAD?

A. revert

B. restore

C. reset

D. add

---

### MCQ 5

Which command unstages files?

A. reset

B. restore --staged

C. Both A and B

D. revert

---

# FAANG-Level Questions

### Q1

Design a safe rollback strategy for a production system using Git.

---

### Q2

How would you recover after an accidental force push?

---

### Q3

Why does Git prefer immutable commits instead of modifying old commits?

---

### Q4

Explain the relationship between Git objects, commits, trees, blobs, and reset.

---

### Q5

Explain why `git revert` is preferred in regulated industries like banking and healthcare.

---

### Q6

How would you safely remove a bad deployment while preserving the complete audit trail?

---

### Q7

How would you undo the last five commits in a production branch without affecting other developers?

---

### Q8

A teammate force-pushed rewritten history. How would you diagnose and recover your local work?

---

# Mini Quiz

1. Which command is safest for public repositories?

2. Which command rewrites history?

3. Which command restores files?

4. Which command moves HEAD?

5. Which command creates a reverse commit?

6. Which command should never be used casually after pushing?

7. Which reset mode is the default?

8. Which command is used for local cleanup?

9. Which command is used for production rollback?

10. Which command can unstage files without deleting your work?

---

# Rapid Fire (Interview Round)

* Difference between reset and revert?
* Difference between restore and reset?
* Difference between restore and checkout?
* Difference between soft and hard reset?
* Can revert be reverted?
* Does restore move HEAD?
* Does reset create commits?
* Does revert remove commits?
* Can restore recover untracked files?
* Which command would you choose after pushing bad code?

---

# Bonus Whiteboard Question

Draw the following after each command:

Initial History

```
A → B → C → D (HEAD)
```

Now show the commit graph after:

1. `git reset --soft HEAD~1`

2. `git reset --mixed HEAD~1`

3. `git reset --hard HEAD~1`

4. `git revert HEAD`

5. `git restore app.js`

Explain:

* Which commit is HEAD?
* Which commits remain?
* Which files changed?
* Was history rewritten?
* Was a new commit created?
