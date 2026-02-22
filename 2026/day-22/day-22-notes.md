
# 📘 Day 22 – Introduction to Git: Your First Repository

---

# ✅ Task 1 – Install and Configure Git

## 🔹 Verify Git Installation

```bash
git --version
```

If installed, it shows the Git version.

---

## 🔹 Set Your Identity

```bash
git config --global user.name "Kamlesh"
git config --global user.email "your-email@example.com"
```

---

## 🔹 Verify Configuration

```bash
git config --list
```

or

```bash
git config user.name
git config user.email
```

---

# ✅ Task 2 – Create Your Git Project

## 🔹 Create Project Folder

```bash
mkdir devops-git-practice
cd devops-git-practice
```

## 🔹 Initialize Git Repository

```bash
git init
```

Creates a hidden `.git/` directory.

---

## 🔹 Check Repository Status

```bash
git status
```

Shows:
- Untracked files
- Staged files
- Changes not staged
- Current branch

---

## 🔹 Explore `.git/` Directory

```bash
ls -la .git
```

Contains:
- `HEAD` → points to current branch
- `config` → repo config
- `objects/` → stores commits & blobs
- `refs/` → branch references

⚠️ If you delete `.git/`, the project is no longer a Git repository.

---

# ✅ Task 3 – Create Git Commands Reference

## 📄 File: `git-commands.md`

```markdown
# Git Commands Reference

## Setup & Config

### git --version
Check installed Git version  
Example: git --version

### git config --global user.name
Set global username  
Example: git config --global user.name "Kamlesh"

### git config --list
View Git configuration  
Example: git config --list

---

## Basic Workflow

### git init
Initialize a new repository  
Example: git init

### git add
Stage changes  
Example: git add git-commands.md

### git commit
Save staged changes to repository  
Example: git commit -m "Add initial Git commands reference"

---

## Viewing Changes

### git status
Show working directory status  
Example: git status

### git log
View commit history  
Example: git log

### git diff
See changes not yet staged  
Example: git diff
```

---

# ✅ Task 4 – Stage and Commit

## 🔹 Stage File

```bash
git add git-commands.md
```

## 🔹 Check What’s Staged

```bash
git status
```

## 🔹 Commit

```bash
git commit -m "Initial commit: Add Git commands reference"
```

## 🔹 View History

```bash
git log
```

---

# ✅ Task 5 – Build Commit History

Edit `git-commands.md` and add more commands:

Examples to add:

```markdown
### git log --oneline
Compact commit history  
Example: git log --oneline

### git restore
Discard working directory changes  
Example: git restore file.txt

### git rm
Remove file from repo  
Example: git rm file.txt
```

---

Repeat:

```bash
git status
git diff
git add .
git commit -m "Add restore and rm commands"
```

Do this at least 3 times.

---

## 🔹 Compact History View

```bash
git log --oneline
```

Example output:

```
a1b2c3d Add restore and rm commands
d4e5f6g Update viewing changes section
h7i8j9k Initial commit
```

Clean commit history = Good DevOps habit.

---

# 📄 File: `day-22-notes.md`

```markdown
# Day 22 Notes – Understanding Git Workflow

## 1. Difference between git add and git commit?

git add → Moves changes to staging area.
git commit → Saves staged changes permanently to repository.

---

## 2. What does the staging area do?

The staging area allows you to choose exactly what changes go into the next commit.
It prevents accidental commits and gives better control.

---

## 3. What does git log show?

It shows:
- Commit hash
- Author
- Date
- Commit message

---

## 4. What is the .git/ folder?

.git/ contains all version history, branches, and metadata.
If deleted, the project loses all Git tracking and history.

---

## 5. Working Directory vs Staging Area vs Repository

Working Directory → Where you edit files.
Staging Area → Where changes are prepared for commit.
Repository → Where committed snapshots are permanently stored.
```

---

# 🧠 What You Learned Today

- Git tracks changes, not files.
- The staging area gives fine-grained control.
- Clean commit messages matter.
- `git status` is your best friend.
- `.git/` is the heart of your repository.

---

