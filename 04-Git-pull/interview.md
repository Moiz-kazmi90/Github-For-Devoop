# Git Pull & Git Fetch Interview Guide (`interview.md`)

> **Topics Covered**
>
> * Git Pull
> * Git Fetch
> * Beginner Questions
> * Intermediate Questions
> * Advanced Questions
> * Conceptual Questions
> * Scenario-Based Questions
> * FAANG-Level Questions
> * Puzzle Questions
> * MCQs
> * True / False

---

# Beginner Level (Q1-Q15)

### Q1. What is `git pull`?

---

### Q2. What is `git fetch`?

---

### Q3. What is the main difference between `git pull` and `git fetch`?

---

### Q4. Which command updates your local branch automatically?

---

### Q5. Which command only downloads changes?

---

### Q6. Which command is safer before reviewing code?

---

### Q7. Which command contacts the remote repository?

---

### Q8. What is the default remote name in Git?

---

### Q9. What does this command do?

```bash
git pull origin main
```

---

### Q10. What does this command do?

```bash
git fetch origin
```

---

### Q11. Does `git fetch` modify your working directory?

---

### Q12. Does `git pull` perform a merge?

---

### Q13. Which command is used before starting work every morning?

---

### Q14. What is a remote-tracking branch?

---

### Q15. Can `git pull` create merge conflicts?

---

# Intermediate Level (Q16-Q30)

### Q16. Explain how `git pull` works internally.

---

### Q17. Explain how `git fetch` works internally.

---

### Q18. Why is `git pull` considered a shortcut?

---

### Q19. Why do many companies recommend `git fetch`?

---

### Q20. Explain the difference between local branches and remote-tracking branches.

---

### Q21. What happens to `origin/main` after `git fetch`?

---

### Q22. What happens to `main` after `git fetch`?

---

### Q23. What happens if your teammate pushes code while you are working?

---

### Q24. Why can `git pull` produce merge conflicts?

---

### Q25. Explain `git pull --rebase`.

---

### Q26. When should you use `git fetch` instead of `git pull`?

---

### Q27. What happens if you run `git pull` with uncommitted changes?

---

### Q28. How can you avoid merge conflicts before using `git pull`?

---

### Q29. Why does `git fetch` not create merge commits?

---

### Q30. Which Git command updates remote-tracking branches?

---

# Advanced Level (Q31-Q40)

### Q31. Explain the internal process of `git pull`.

---

### Q32. Explain the relationship between `git fetch`, `FETCH_HEAD`, and `origin/main`.

---

### Q33. Why does `git fetch` not change HEAD?

---

### Q34. Explain why `git pull` is equivalent to `git fetch` followed by `git merge`.

---

### Q35. Explain the advantages and disadvantages of `git pull --rebase`.

---

### Q36. Why do experienced developers prefer reviewing fetched commits before merging?

---

### Q37. Explain how Git determines whether a merge commit is required after a pull.

---

### Q38. How would you safely update a production branch?

---

### Q39. Explain the risks of blindly running `git pull` every hour.

---

### Q40. Compare `git fetch`, `git pull`, and `git clone`.

---

# Conceptual Questions (Q41-Q50)

### Q41. Why did Git create two separate commands instead of only one?

---

### Q42. If `git pull` already downloads changes, why does `git fetch` exist?

---

### Q43. Why is reviewing incoming commits important?

---

### Q44. Explain Remote → Local synchronization.

---

### Q45. Explain the role of `origin/main`.

---

### Q46. Does `git fetch` rewrite history?

---

### Q47. Does `git pull` rewrite history?

---

### Q48. Can `git fetch` create merge conflicts?

---

### Q49. Can `git pull` change your working tree?

---

### Q50. Explain the safest workflow for a team project.

---

# Scenario-Based Questions (Q51-Q60)

### Q51.

Your teammate pushed five commits.

You want to inspect them before updating your branch.

Which command will you use?

---

### Q52.

You accidentally ran `git pull` and now have merge conflicts.

How do you proceed?

---

### Q53.

You have local changes that are not committed.

Can you safely run `git pull`?

---

### Q54.

Your manager says:

"Never use git pull directly on production."

Why might they say this?

---

### Q55.

A developer says:

"`git fetch` updated my project."

Is this statement correct?

---

### Q56.

You fetched changes but your code didn't change.

Why?

---

### Q57.

Your teammate asks whether they should always use `git pull`.

What advice would you give?

---

### Q58.

A CI/CD pipeline should only inspect remote commits.

Would you use `git fetch` or `git pull`?

---

### Q59.

You accidentally merged unwanted remote commits.

Which command would have been safer?

---

### Q60.

Your local branch is behind GitHub by ten commits.

Describe the safest way to update it.

---

# Puzzle Questions (Q61-Q65)

## Puzzle 1

Local:

```text
A ---- B ---- C (main)
```

Remote:

```text
A ---- B ---- C ---- D ---- E
```

Run:

```bash
git fetch
```

Questions:

* Which branch moves?
* Does HEAD move?
* Does your working directory change?

---

## Puzzle 2

Using the same history, run:

```bash
git pull
```

Questions:

* Which commits are downloaded?
* Will main move?
* Will the working directory change?

---

## Puzzle 3

Local:

```text
A ---- B ---- C
```

Remote:

```text
A ---- B ---- C ---- D
```

You modify `app.js` locally but don't commit.

Then run:

```bash
git pull
```

What may happen?

---

## Puzzle 4

After `git fetch`, you see:

```text
origin/main

↓

A ---- B ---- C ---- D
```

while

```text
main

↓

A ---- B ---- C
```

How do you update `main`?

---

## Puzzle 5

You fetched changes yesterday.

Today, another developer pushed new commits.

Do you need another fetch?

Why?

---

# FAANG-Level Questions (Q66-Q75)

### Q66.

Design a workflow for a company with 500 developers using `git fetch`.

---

### Q67.

Why do large companies often discourage automatic merges?

---

### Q68.

Explain why CI systems commonly use `git fetch`.

---

### Q69.

How would you update hundreds of repositories safely?

---

### Q70.

Explain the difference between `FETCH_HEAD` and `HEAD`.

---

### Q71.

How does Git optimize network usage during fetch?

---

### Q72.

How would you reduce merge conflicts in a large team?

---

### Q73.

Explain why `git pull --rebase` creates a cleaner history.

---

### Q74.

Compare Merge Workflow vs Rebase Workflow.

---

### Q75.

How would you teach a junior developer the safest update workflow?

---

# Multiple Choice Questions

### MCQ 1

Which command only downloads commits?

A. `git merge`

B. `git pull`

C. `git fetch`

D. `git switch`

**Answer:** C

---

### MCQ 2

`git pull` is equivalent to:

A. `git add + git commit`

B. `git fetch + git merge`

C. `git fetch + git reset`

D. `git push + git merge`

**Answer:** B

---

### MCQ 3

Which command updates your working directory?

A. `git fetch`

B. `git branch`

C. `git pull`

D. `git tag`

**Answer:** C

---

### MCQ 4

Which branch is updated after `git fetch`?

A. `HEAD`

B. `main`

C. `origin/main`

D. `master`

**Answer:** C

---

### MCQ 5

Which command is safer before reviewing incoming commits?

A. `git pull`

B. `git fetch`

C. `git merge`

D. `git push`

**Answer:** B

---

# True / False

1. `git fetch` changes your working directory.

**False**

---

2. `git pull` performs a merge by default.

**True**

---

3. `git fetch` updates remote-tracking branches.

**True**

---

4. `git pull` can create merge conflicts.

**True**

---

5. `git fetch` automatically updates your local branch.

**False**

---

6. `git pull` downloads commits from a remote repository.

**True**

---

7. `git fetch` is useful for reviewing changes before merging.

**True**

---

8. `git pull` always creates a merge commit.

**False**

---

9. `origin/main` is a remote-tracking branch.

**True**

---

10. `git clone` and `git fetch` perform the same job.

**False**

---

# Rapid Fire Interview

* Fetch or Pull?
* Pull or Clone?
* Fetch or Merge?
* Remote Branch or Local Branch?
* HEAD or FETCH_HEAD?
* origin/main or main?
* Pull or Pull --rebase?
* Merge or Rebase?
* Tracking Branch or Remote Branch?
* Why is `git fetch` considered safer?

---

# Final Interview Tip

A strong interview answer is:

> **"`git fetch` downloads changes from the remote repository without affecting my current branch, allowing me to review them first. `git pull` is essentially `git fetch` followed by `git merge`, so it immediately updates my local branch and may create merge conflicts. In team environments, I prefer `git fetch` for safety and `git pull` when I want to update my branch directly."**
