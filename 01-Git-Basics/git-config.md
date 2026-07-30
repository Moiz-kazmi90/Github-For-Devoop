# Git Configuration

Git configuration stores your identity, which is attached to every commit.

---

# Configure Username

```bash
git config --global user.name "Your Name"
```

Example:

```bash
git config --global user.name "Moiz Kazmi"
```

---

# Configure Email

```bash
git config --global user.email "your-email@example.com"
```

Example:

```bash
git config --global user.email "moiz@example.com"
```

---

# Verify Configuration

Display all configurations:

```bash
git config --list
```

---

# Check Username

```bash
git config user.name
```

---

# Check Email

```bash
git config user.email
```

---

# Global Configuration

Applies to all repositories.

```bash
git config --global user.name "Your Name"
```

---

# Local Configuration

Applies only to the current repository.

```bash
git config user.name "Your Name"
```

---

# Remove Username

```bash
git config --global --unset user.name
```

---

# Remove Email

```bash
git config --global --unset user.email
```

---

# Edit Git Configuration

```bash
git config --global --edit
```

---

# Git Configuration File

Linux:

```text
~/.gitconfig
```

Windows:

```text
C:\Users\Username\.gitconfig
```

---

# Summary

Git configuration allows you to set your identity and preferences. Every commit contains the configured username and email.