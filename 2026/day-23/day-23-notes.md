
# 🌿 Day 23 – Git Branching & Working with GitHub

---

# ✅ Task 1 – Understanding Branches

## 1️⃣ What is a branch in Git?

A branch is an independent line of development that points to a specific commit.  
It allows you to work on features or fixes without affecting the main code.

---

## 2️⃣ Why use branches instead of committing everything to main?

- Prevent breaking stable code  
- Enable parallel feature development  
- Make collaboration easier  
- Keep production branch clean  

---

## 3️⃣ What is HEAD in Git?

HEAD is a pointer to the current branch and commit you are working on.

Example:
If you're on `main`, HEAD points to the latest commit on `main`.

---

## 4️⃣ What happens to files when you switch branches?

Git updates your working directory to match the snapshot of the branch you switch to.

- Files may appear/disappear
- File content may change
- Uncommitted changes can block switching

---

# ✅ Task 2 – Branching Commands (Hands-On)

## 🔹 List Branches

```bash
git branch
```

---

## 🔹 Create New Branch

```bash
git branch feature-1
```

---

## 🔹 Switch to Branch

```bash
git checkout feature-1
```

or modern way:

```bash
git switch feature-1
```

---

## 🔹 Create & Switch in One Command

```bash
git checkout -b feature-2
```

Modern alternative:

```bash
git switch -c feature-2
```

---

## 🔹 Difference: `git switch` vs `git checkout`

- `git switch` → Only for switching branches (clear purpose)
- `git checkout` → Older command (switch branches + restore files)

`git switch` is safer and more readable.

---

## 🔹 Make Commit on feature-1

```bash
git switch feature-1
echo "Feature work" >> feature.txt
git add feature.txt
git commit -m "Add feature-1 implementation"
```

---

## 🔹 Switch Back to main

```bash
git switch main
```

The commit from `feature-1` will NOT be visible on `main`.

---

## 🔹 Delete Branch

```bash
git branch -d feature-2
```

Force delete (if needed):

```bash
git branch -D feature-2
```

---

## 🔹 Add These to `git-commands.md`

Add branching section with:

- git branch
- git branch <name>
- git switch
- git switch -c
- git checkout -b
- git branch -d

Commit your updates with clear messages.

---

# ✅ Task 3 – Push to GitHub

## 🔹 Create Repository on GitHub

Do NOT initialize with README.

---

## 🔹 Connect Local Repo to Remote

```bash
git remote add origin https://github.com/yourusername/devops-git-practice.git
```

Verify:

```bash
git remote -v
```

---

## 🔹 Push Main Branch

```bash
git push -u origin main
```

---

## 🔹 Push Feature Branch

```bash
git push -u origin feature-1
```

Now both branches should appear on GitHub.

---

## 🔹 What is origin vs upstream?

- **origin** → Default name for your remote repository.
- **upstream** → Refers to the original repository you forked from.

Example:
- Your fork → origin  
- Original repo → upstream  

---

# ✅ Task 4 – Pull from GitHub

## 🔹 Make Change on GitHub (Web UI)

Edit a file and commit directly.

---

## 🔹 Pull Changes Locally

```bash
git pull origin main
```

---

## 🔹 Difference Between fetch and pull

- `git fetch` → Downloads changes but does NOT merge.
- `git pull` → Fetch + Merge in one step.

`pull = fetch + merge`

---

# ✅ Task 5 – Clone vs Fork

## 🔹 Clone a Public Repository

```bash
git clone https://github.com/user/repo.git
```

Creates local copy.

---

## 🔹 Fork Repository on GitHub

Click **Fork** → Creates your own copy on GitHub.

Then clone your fork:

```bash
git clone https://github.com/yourusername/repo.git
```

---

## 🔹 Difference Between Clone and Fork

| Clone | Fork |
|-------|------|
| Git command | GitHub feature |
| Copies repo locally | Copies repo to your GitHub account |
| No new remote repo created | Creates new remote repo |

---

## 🔹 When to Clone vs Fork?

- Clone → When you just want a local copy.
- Fork → When you want to contribute to someone else's repo.

---

## 🔹 Keep Fork in Sync

Add upstream remote:

```bash
git remote add upstream https://github.com/original/repo.git
```

Fetch updates:

```bash
git fetch upstream
git merge upstream/main
```

---

# 🧠 What You Learned Today

- Branches isolate development work.
- HEAD tracks current position.
- main should stay stable.
- GitHub remotes connect local and cloud repos.
- Forking is collaboration workflow.
- `fetch` is safer than `pull` when reviewing changes.

---

# 🚀 DevOps Growth Check

You now understand:

- Local version control
- Branch-based workflow
- Remote repositories
- Collaboration basics

That’s real-world Git foundation 🔥

---

✅ Day 23 Completed – Branching & GitHub Integration Mastered
