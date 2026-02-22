
# 🔁 Day 25 – Git Reset vs Revert & Branching Strategies

---

# ✅ Task 1 – Git Reset (Hands-On Observations)

Assume commit history:

```
A → B → C (HEAD)
```

---

## 🔹 git reset --soft HEAD~1

```bash
git reset --soft HEAD~1
```

Result:
- Moves HEAD back to B
- Changes from C stay **staged**
- No files lost

---

## 🔹 git reset --mixed HEAD~1 (default)

```bash
git reset --mixed HEAD~1
```

Result:
- Moves HEAD back to B
- Changes from C stay in working directory
- Changes are **unstaged**

---

## 🔹 git reset --hard HEAD~1

```bash
git reset --hard HEAD~1
```

Result:
- Moves HEAD back to B
- Changes from C are completely deleted
- Working directory reset

---

## 📌 Answers

### Difference Between --soft, --mixed, --hard

| Option | Moves HEAD | Keeps Changes | Keeps Staged |
|--------|------------|--------------|--------------|
| --soft | ✅ | ✅ | ✅ |
| --mixed | ✅ | ✅ | ❌ |
| --hard | ✅ | ❌ | ❌ |

---

### Which is destructive?

`--hard` is destructive because it permanently deletes uncommitted changes.

---

### When to Use?

- `--soft` → Fix last commit message or combine commits  
- `--mixed` → Unstage changes  
- `--hard` → Discard local work  

---

### Should You Reset Pushed Commits?

❌ No.  
Reset rewrites history and breaks collaboration.

---

# ✅ Task 2 – Git Revert

Assume:

```
X → Y → Z
```

## 🔹 Revert Commit Y

```bash
git revert <commit-hash-of-Y>
```

Result:
- Creates a **new commit**
- That commit reverses changes from Y
- Y still exists in history

---

## 📌 Answers

### Difference Between reset and revert?

- `reset` → Moves branch pointer, rewrites history  
- `revert` → Creates new commit that undoes changes  

---

### Why is revert safer?

Because it does NOT rewrite history.

Safe for shared branches.

---

### When Use Revert vs Reset?

- Revert → Undo changes in shared/public branches  
- Reset → Fix local commits before pushing  

---

# ✅ Task 3 – Reset vs Revert Summary

| Feature | git reset | git revert |
|----------|------------|-------------|
| What it does | Moves branch pointer | Creates inverse commit |
| Removes commit from history? | Yes | No |
| Safe for shared branches? | No | Yes |
| When to use | Local cleanup | Undo public commit |

---

# ✅ Task 4 – Branching Strategies

---

## 🌊 GitFlow

### How It Works

Branches:
- main
- develop
- feature/*
- release/*
- hotfix/*

### Flow

```
main
  ↑
release
  ↑
develop ← feature
```

### Used For

Large teams with scheduled releases.

### Pros
- Structured
- Clear release cycle

### Cons
- Complex
- Too heavy for small teams

---

## 🚀 GitHub Flow

### How It Works

- Single `main` branch
- Feature branches
- Pull Requests → merge to main

### Flow

```
main ← feature-branch
```

### Used For

Startups & continuous deployment teams.

### Pros
- Simple
- Fast
- Easy collaboration

### Cons
- No formal release structure

---

## 🌳 Trunk-Based Development

### How It Works

- Everyone commits to `main`
- Very short-lived branches (or none)

### Flow

```
main ← small frequent commits
```

### Used For

High-performance CI/CD environments.

### Pros
- Minimal merge conflicts
- Fast integration

### Cons
- Requires strong discipline & testing

---

# 📌 Strategy Questions

### Which for Startup?

👉 GitHub Flow (fast shipping)

### Which for Large Team with Releases?

👉 GitFlow (structured control)

### Example Open Source Strategy

Most open-source projects (like Kubernetes) use:

👉 GitHub Flow style with protected main branch + PR reviews

---

# 🔐 Bonus: git reflog

```bash
git reflog
```

Shows all recent Git actions — even after reset.

Your safety net.

---

# 🧠 Key Learnings

- Reset rewrites history.
- Revert preserves history.
- Never reset pushed commits.
- Branching strategy depends on team size & release model.
- `reflog` can save you from disasters.

---

# 💪 DevOps Growth Level

You now understand:

- Undoing mistakes safely  
- History rewriting  
- Public vs private workflows  
- Real-world branching strategies  

This is professional Git knowledge 🔥

---

✅ Day 25 Completed – Git Recovery & Branching Strategies Mastered
