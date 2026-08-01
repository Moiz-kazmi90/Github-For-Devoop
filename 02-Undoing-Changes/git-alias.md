# Git Alias (`git-alias.md`)

# What is Git Alias?

A **Git Alias** is a shortcut for a Git command.

Instead of typing a long Git command every time, you can create a short name (alias) and use it like a normal Git command.

**Simple Definition**

> **Git Alias is a shortcut that lets you run long Git commands with a short and easy command.**

---

# Why do we use Git Alias?

Many Git commands are long.

Example:

```bash
git status
```

Instead of typing this every time, you can create an alias:

```bash
git config --global alias.st status
```

Now you only need to type:

```bash
git st
```

Git automatically runs:

```bash
git status
```

---

# Why was Git Alias introduced?

Developers use Git many times every day.

Typing long commands repeatedly:

* Takes more time.
* Increases typing mistakes.
* Reduces productivity.

Git Alias was introduced to make Git commands:

* Faster
* Easier
* Shorter
* More productive

---

# How Does Git Alias Work?

Suppose you create:

```bash
git config --global alias.s status
```

Now:

```bash
git s
```

means

```bash
git status
```

Git automatically replaces the alias with the original command.

---

# Where Are Git Aliases Stored?

Aliases are stored in the Git configuration file.

There are two types:

## Global Alias

Available in **all repositories**.

Stored in:

```text
~/.gitconfig
```

---

## Local Alias

Available only inside the current Git repository.

Stored in:

```text
.git/config
```

---

# View All Aliases

```bash
git config --get-regexp alias
```

Example Output

```text
alias.st status
alias.co checkout
alias.br branch
alias.cm commit
```

---

# Creating an Alias (Using Git Config)

## Status Alias

```bash
git config --global alias.st status
```

Use

```bash
git st
```

---

## Branch Alias

```bash
git config --global alias.b branch
```

Use

```bash
git b
```

Instead of

```bash
git branch
```

---

## Checkout Alias

```bash
git config --global alias.co checkout
```

Use

```bash
git co
```

---

## Commit Alias

```bash
git config --global alias.cm commit
```

Use

```bash
git cm
```

---

## Commit with Message

```bash
git config --global alias.ci "commit -m"
```

Use

```bash
git ci "Initial Commit"
```

Git runs:

```bash
git commit -m "Initial Commit"
```

---

## Log Alias

```bash
git config --global alias.lg log
```

Use

```bash
git lg
```

---

## Pretty Log Alias

```bash
git config --global alias.graph "log --oneline --graph --decorate --all"
```

Use

```bash
git graph
```

---

# Creating Alias by Editing `.gitconfig` with Nano

Instead of using `git config`, you can directly edit the Git configuration file.

Open the global Git configuration file:

```bash
nano ~/.gitconfig
```

You may see something like:

```ini
[user]
    name = John
    email = john@example.com
```

Add an **[alias]** section:

```ini
[user]
    name = John
    email = john@example.com

[alias]
    st = status
    b = branch
    co = checkout
    cm = commit
    lg = log
```

Save the file.

---

# How to Save in Nano

After editing:

Press

```text
Ctrl + O
```

This means **Write Out (Save)**.

Press:

```text
Enter
```

to confirm the file name.

Exit Nano:

```text
Ctrl + X
```

Now test your alias:

```bash
git b
```

Git runs:

```bash
git branch
```

---

# Editing an Existing Alias

Open:

```bash
nano ~/.gitconfig
```

Suppose you have:

```ini
[alias]
    st = status
```

Change it to:

```ini
[alias]
    st = status -s
```

Save:

```text
Ctrl + O
Enter
Ctrl + X
```

Now:

```bash
git st
```

runs

```bash
git status -s
```

---

# Creating a Local Alias

Inside a repository:

```bash
git config alias.b branch
```

Notice:

There is **no `--global`**.

This alias works only in the current project.

---

# Difference Between Global and Local Alias

| Global Alias              | Local Alias                      |
| ------------------------- | -------------------------------- |
| Works in all repositories | Works only in current repository |
| Stored in `~/.gitconfig`  | Stored in `.git/config`          |
| Created with `--global`   | Created without `--global`       |

---

# Viewing One Alias

```bash
git config --get alias.b
```

Output

```text
branch
```

---

# Viewing All Global Aliases

```bash
git config --global --get-regexp alias
```

---

# Removing an Alias

Remove one alias:

```bash
git config --global --unset alias.b
```

Now:

```bash
git b
```

will no longer work.

---

# Remove All Aliases

You can manually delete the **[alias]** section from:

```bash
nano ~/.gitconfig
```

Save the file.

---

# Real Example

Create:

```bash
git config --global alias.s status
git config --global alias.b branch
git config --global alias.lg log
```

Now use:

```bash
git s
git b
git lg
```

Instead of:

```bash
git status
git branch
git log
```

This saves time every day.

---

# Most Useful Git Aliases

```bash
git config --global alias.s status
```

---

```bash
git config --global alias.st "status -s"
```

---

```bash
git config --global alias.b branch
```

---

```bash
git config --global alias.co checkout
```

---

```bash
git config --global alias.sw switch
```

---

```bash
git config --global alias.cm commit
```

---

```bash
git config --global alias.ci "commit -m"
```

---

```bash
git config --global alias.lg log
```

---

```bash
git config --global alias.graph "log --oneline --graph --decorate --all"
```

---

# Advantages

* Saves typing time.
* Easy to remember.
* Increases productivity.
* Reduces typing mistakes.
* Makes daily Git work faster.

---

# Disadvantages

* Other developers may not know your custom aliases.
* Very short alias names can be confusing if not documented.
* Aliases work only where they are configured.

---

# Important Notes

* Aliases do **not** create new Git commands.
* Git simply replaces the alias with the original command.
* Global aliases are available in every repository.
* Local aliases work only inside one repository.

---

# Quick Revision

Create alias:

```bash
git config --global alias.b branch
```

Use:

```bash
git b
```

---

Edit aliases manually:

```bash
nano ~/.gitconfig
```

---

Save in Nano:

```text
Ctrl + O
Enter
Ctrl + X
```

---

View all aliases:

```bash
git config --global --get-regexp alias
```

---

Remove alias:

```bash
git config --global --unset alias.b
```

---

# Viva Questions

### Q1. What is Git Alias?

**Answer:**

A Git Alias is a shortcut for a Git command that allows you to run long commands using short names.

---

### Q2. Why do we use Git Alias?

**Answer:**

To save time, reduce typing, and make Git commands easier to remember.

---

### Q3. How do you create the alias `b` for `branch`?

```bash
git config --global alias.b branch
```

---

### Q4. How do you edit aliases manually?

```bash
nano ~/.gitconfig
```

---

### Q5. Which section of `.gitconfig` stores aliases?

**Answer:**

```ini
[alias]
```

---

### Q6. How do you save changes in Nano?

**Answer:**

1. `Ctrl + O` (Save)
2. `Enter` (Confirm)
3. `Ctrl + X` (Exit)

---

### Q7. How do you view all aliases?

```bash
git config --global --get-regexp alias
```

---

### Q8. How do you delete the alias `b`?

```bash
git config --global --unset alias.b
```

---

# Interview One-Line Definition

> **Git Alias is a Git feature that allows you to create custom shortcuts for frequently used Git commands, making your workflow faster and more efficient.**
