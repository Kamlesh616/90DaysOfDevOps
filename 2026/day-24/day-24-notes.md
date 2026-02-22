
# 🔥 Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry-Pick

---

# ✅ Task 1 – Git Merge

## 🔹 Fast-Forward Merge

When `main` has no new commits and `feature-login` is ahead:

```bash
git switch main
git merge feature-login
```

Git simply moves the `main` pointer forward.

### 📌 What is a Fast-Forward Merge?

A fast-forward merge happens when there are no new commits on the target branch.  
Git just moves the branch pointer forward — no merge commit is created.

---

## 🔹 Merge Commit Scenario

If:

- `feature-signup` has commits  
- `main` also has new commits  

Then:

```bash
git merge feature-signup
```

Git creates a **merge commit**.

### 📌 When does Git create a merge commit?

When both branches have diverged (both have new commits).

---

## 🔹 Merge Conflict

Occurs when the same line is modified in both branches.

Example conflict markers:

```bash
<<<<<<< HEAD
Main branch change
=======
Feature branch change
>>>>>>> feature-branch
```

You must manually resolve and commit.

### 📌 What is a Merge Conflict?

When Git cannot automatically decide which change to keep.

---

# ✅ Task 2 – Git Rebase

## 🔹 Rebase feature-dashboard onto main

```bash
git switch feature-dashboard
git rebase main
```

---

## 🔹 What Does Rebase Do?

Rebase **moves your branch commits** and replays them on top of another branch.

It rewrites commit history.

---

## 🔹 History Comparison

### Merge:
```
main ----o----o
             \ 
              o--o (feature)
```

### Rebase:
```
main ----o----o----o----o
```

Rebase creates a **linear history**.

---

## 📌 Answers

### What does rebase do?

Reapplies commits from one branch onto another base.

### How is history different?

Merge → Preserves branch structure.  
Rebase → Cleaner, linear history.

### Why never rebase shared commits?

Because rebase rewrites history.  
If already pushed, it causes conflicts for collaborators.

### When use rebase vs merge?

- Rebase → Clean up local commits before merging.
- Merge → When working in shared branches.

---

# ✅ Task 3 – Squash Merge

## 🔹 Squash Merge

```bash
git merge --squash feature-profile
git commit -m "Add profile feature"
```

Only **one commit** added to main.

---

## 🔹 Regular Merge

```bash
git merge feature-settings
```

Adds all commits + possible merge commit.

---

## 📌 Answers

### What does squash merging do?

Combines all feature branch commits into a single commit.

### When use squash merge?

- When feature branch has many small commits.
- When you want clean history.

### Trade-off?

You lose detailed commit history of that branch.

---

# ✅ Task 4 – Git Stash

## 🔹 Save Work-In-Progress

```bash
git stash
```

## 🔹 List Stashes

```bash
git stash list
```

## 🔹 Apply Latest Stash

```bash
git stash pop
```

## 🔹 Apply Specific Stash

```bash
git stash apply stash@{1}
```

---

## 📌 Answers

### Difference: stash pop vs apply?

- `pop` → Applies and removes stash.
- `apply` → Applies but keeps stash.

### When use stash?

- Emergency bug fix
- Switching branches quickly
- Temporary work storage

---

# ✅ Task 5 – Cherry-Pick

## 🔹 Cherry-Pick a Specific Commit

```bash
git log --oneline
git cherry-pick <commit-hash>
```

Only that commit is applied to current branch.

---

## 📌 Answers

### What does cherry-pick do?

Applies a specific commit from one branch onto another.

### When use cherry-pick?

- Apply hotfix to production branch.
- Bring specific fix without merging full feature.

### What can go wrong?

- Conflicts
- Duplicate changes
- Confusing history

---

# 🧠 Key Learnings

| Concept | Purpose |
|----------|----------|
| Merge | Combine branches |
| Rebase | Rewrite & linearize history |
| Squash | Clean commit history |
| Stash | Temporary save work |
| Cherry-pick | Apply specific commit |

---

# 🚀 DevOps Reality

In real-world teams:

- Feature branches → merged into main
- Rebase → clean local commits before PR
- Squash → keep history readable
- Stash → context switching
- Cherry-pick → urgent production fixes

---

# 💪 Growth Level

You now understand:

- How branches combine  
- How history is shaped  
- How to fix conflicts  
- How to handle emergency workflows  

This is no longer beginner Git.

You’re operating at **intermediate DevOps Git level** now 🔥

---

✅ Day 24 Completed – Advanced Git Workflows Mastered
