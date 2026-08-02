# Git Interview Questions - Part 1

## Beginner, Intermediate & Advanced (Questions 1–50)

> These questions cover **Git Branch, Switch, Checkout, and Merge**. They are suitable for university viva, internships, DevOps interviews, remote jobs, and software engineering interviews.

---

# Beginner Level (Q1–Q25)

### Q1. What is Git?

### Q2. What is a Git repository?

### Q3. What is a Git branch?

### Q4. Why do we create branches?

### Q5. Does creating a branch copy the whole project?

### Q6. Which command lists all local branches?

### Q7. Which command creates a new branch?

### Q8. Which command switches to another branch?

### Q9. What is the difference between `git branch` and `git switch`?

### Q10. What is the purpose of `git checkout`?

### Q11. Why did Git introduce `git switch`?

### Q12. What is `HEAD` in Git?

### Q13. Which branch is usually the default branch?

### Q14. What does the `*` symbol mean in the output of `git branch`?

### Q15. Which command creates and switches to a branch in one step?

### Q16. What is `git merge`?

### Q17. Why do we use `git merge`?

### Q18. Which branch should you switch to before merging?

### Q19. What is a merge commit?

### Q20. What is a fast-forward merge?

### Q21. What is a merge conflict?

### Q22. Which command cancels an unfinished merge?

### Q23. Which command shows the current branch?

### Q24. Can Git automatically merge every change?

### Q25. Which command deletes a merged branch?

---

# Intermediate Level (Q26–Q40)

### Q26. Explain the difference between `git switch` and `git checkout`.

### Q27. Explain the difference between `git branch` and `git merge`.

### Q28. Explain the difference between a local branch and a remote branch.

### Q29. What happens internally when you create a branch?

### Q30. Why are Git branches called lightweight?

### Q31. What happens to HEAD when you switch branches?

### Q32. Can two branches point to the same commit? Explain.

### Q33. Why does Git sometimes create a merge commit?

### Q34. When does Git perform a fast-forward merge?

### Q35. Explain the difference between a fast-forward merge and a three-way merge.

### Q36. Why do merge conflicts happen?

### Q37. How do you resolve a merge conflict?

### Q38. What happens if you delete a branch after merging it?

### Q39. Explain Detached HEAD.

### Q40. What happens if you make commits in Detached HEAD state?

---

# Advanced Level (Q41–Q50)

### Q41. How does Git store branches internally?

### Q42. Explain the relationship between HEAD, branch pointers, and commits.

### Q43. Why is Git branch creation almost instant?

### Q44. Explain how Git determines the merge base.

### Q45. How does Git decide whether to perform a fast-forward merge or a three-way merge?

### Q46. Why do many companies use `git merge --no-ff`?

### Q47. What are the advantages and disadvantages of merge commits?

### Q48. Explain the complete lifecycle of a feature branch from creation to deletion.

### Q49. If a merge conflict occurs in multiple files, what steps would you follow to resolve it safely?

### Q50. Compare `git branch`, `git switch`, `git checkout`, and `git merge` in one interview answer.

---

# Rapid Fire Round

* Branch or Folder?
* Branch or Commit?
* Branch or Tag?
* Switch or Checkout?
* Merge or Rebase?
* Merge or Cherry-pick?
* Fast-forward or Three-way Merge?
* HEAD or Branch?
* Local Branch or Remote Branch?
* Merge Commit or Normal Commit?

---

# Quick Quiz (MCQs)

### MCQ 1

Which command creates a new branch?

A. `git switch`

B. `git merge`

C. `git branch`

D. `git checkout`

---

### MCQ 2

Which command switches to another branch?

A. `git add`

B. `git switch`

C. `git merge`

D. `git commit`

---

### MCQ 3

Which command combines two branches?

A. `git merge`

B. `git reset`

C. `git restore`

D. `git revert`

---

### MCQ 4

Which command creates and switches to a branch?

A. `git switch`

B. `git checkout`

C. `git switch -c`

D. `git branch`

---

### MCQ 5

Which command cancels an unfinished merge?

A. `git reset`

B. `git merge --abort`

C. `git restore`

D. `git revert`

---

# True / False

1. A Git branch is a complete copy of the project.

2. `git switch` changes the current branch.

3. `git checkout` can restore files.

4. `git merge` always creates a merge commit.

5. Two branches can point to the same commit.

6. Git can automatically resolve every merge conflict.

7. `git branch` automatically switches to the new branch.

8. `git switch -c` creates and switches to a new branch.

9. HEAD normally points to the current branch.

10. A merged branch can be safely deleted if it is no longer needed.

---

# Puzzle Round

### Puzzle 1

Initial history:

```text
A ---- B ---- C (main)
```

You run:

```bash
git switch -c feature-login
```

Then make two commits:

```text
A ---- B ---- C (main)
               \
                D ---- E (feature-login)
```

Questions:

* Which branch contains commits D and E?
* Has `main` changed?
* Where is HEAD?

---

### Puzzle 2

History:

```text
A ---- B ---- C (main)
               \
                D ---- E (feature-login)
```

Run:

```bash
git switch main
git merge feature-login
```

Questions:

* Will Git perform a fast-forward merge or a three-way merge?
* Will a merge commit be created?
* What will the final history look like?

---

### Puzzle 3

History:

```text
A ---- B ---- C (main)
```

Run:

```bash
git checkout B
```

Questions:

* Is HEAD attached to a branch?
* What state is Git in?
* Can you make commits here?

---

# Interview Tips

* Always explain **what** the command does before explaining **how** it works.
* Mention **HEAD**, **branch pointers**, and **working directory** when answering advanced questions.
* Use simple examples when explaining merge conflicts.
* For team projects, recommend `git switch` instead of `git checkout` for branch switching.
* When discussing merges, explain both **fast-forward** and **three-way merge** because interviewers frequently ask about both.

---

**End of Part 1 (Questions 1–50)**

The next file (**`interview-part2.md`**) should cover:

* Scenario-based questions
* FAANG-level questions
* Advanced Git internals
* More puzzles
* More MCQs
* More True/False
* Real-world debugging interview questions
