
# 🖥️ Day 26 – GitHub CLI (gh): Manage GitHub from Your Terminal

---

# ✅ Task 1 – Install & Authenticate

## 🔹 Install GitHub CLI

Official website:
https://cli.github.com/

Mac:
```bash
brew install gh
```

Windows:
```bash
winget install GitHub.cli
```

Linux:
```bash
sudo apt install gh
```

---

## 🔹 Authenticate

```bash
gh auth login
```

Options:
- GitHub.com or Enterprise
- HTTPS or SSH
- Login via browser or token

---

## 🔹 Verify Login

```bash
gh auth status
```

Shows:
- Logged-in user
- Authentication method
- Active account

---

## 📌 What authentication methods does gh support?

- Browser-based OAuth login
- Personal Access Token (PAT)
- SSH authentication
- GitHub Enterprise authentication

---

# ✅ Task 2 – Working with Repositories

---

## 🔹 Create New Repo (Public with README)

```bash
gh repo create devops-test-repo --public --add-readme
```

---

## 🔹 Clone Using gh

```bash
gh repo clone username/devops-test-repo
```

---

## 🔹 View Repo Details

```bash
gh repo view
```

Or specific repo:

```bash
gh repo view username/repo-name
```

---

## 🔹 List All Your Repositories

```bash
gh repo list
```

---

## 🔹 Open Repo in Browser

```bash
gh repo view --web
```

---

## 🔹 Delete Repo (Careful!)

```bash
gh repo delete username/devops-test-repo
```

---

# ✅ Task 3 – Issues

---

## 🔹 Create Issue

```bash
gh issue create --title "Bug in login" --body "Login fails on invalid input" --label bug
```

---

## 🔹 List Open Issues

```bash
gh issue list
```

---

## 🔹 View Specific Issue

```bash
gh issue view 1
```

---

## 🔹 Close Issue

```bash
gh issue close 1
```

---

## 📌 How could gh issue be used in automation?

- Auto-create issues from monitoring alerts
- Create issues from CI failures
- Generate bug reports via scripts
- Bulk close stale issues

Using:
```bash
gh issue create --json
```

Machine-readable output for scripts.

---

# ✅ Task 4 – Pull Requests

---

## 🔹 Create Branch, Commit & Push

```bash
git checkout -b feature-cli-test
echo "Test" >> test.txt
git add .
git commit -m "Add test file"
git push origin feature-cli-test
```

---

## 🔹 Create PR from Terminal

```bash
gh pr create --fill
```

Auto-fills title & body from commit message.

---

## 🔹 List Open PRs

```bash
gh pr list
```

---

## 🔹 View PR Details

```bash
gh pr view 1
```

---

## 🔹 Merge PR

```bash
gh pr merge 1
```

---

## 📌 What merge methods does gh pr merge support?

- Merge commit
- Squash merge
- Rebase merge

Example:
```bash
gh pr merge 1 --squash
gh pr merge 1 --rebase
```

---

## 📌 How to review someone else's PR?

```bash
gh pr checkout 2
gh pr review 2 --approve
gh pr review 2 --comment -b "Looks good!"
gh pr review 2 --request-changes -b "Fix formatting"
```

---

# ✅ Task 5 – GitHub Actions (Preview)

---

## 🔹 List Workflow Runs

```bash
gh run list
```

---

## 🔹 View Specific Workflow Run

```bash
gh run view <run-id>
```

---

## 📌 How are gh run & gh workflow useful in CI/CD?

- Monitor pipeline status from terminal
- Debug failed jobs
- Re-run failed workflows
- Automate deployment checks
- Integrate with DevOps scripts

---

# ✅ Task 6 – Useful gh Tricks

---

## 🔹 gh api (Raw GitHub API)

```bash
gh api repos/username/repo-name
```

Used for:
- Custom automation
- Advanced scripting
- Accessing unsupported features

---

## 🔹 gh gist

Create Gist:

```bash
gh gist create file.txt
```

List Gists:

```bash
gh gist list
```

---

## 🔹 gh release

Create Release:

```bash
gh release create v1.0.0
```

List Releases:

```bash
gh release list
```

---

## 🔹 gh alias (Shortcuts)

Create alias:

```bash
gh alias set co "pr checkout"
```

Use:

```bash
gh co 12
```

---

## 🔹 gh search repos

```bash
gh search repos devops
```

Search GitHub directly from terminal.

---

# 🧠 Key Learnings

- gh reduces browser dependency.
- Perfect for DevOps automation.
- Works well inside CI/CD pipelines.
- Supports JSON output for scripting.
- Helps manage repos at scale.

---

# 📌 Add to git-commands.md

Add new section:

## GitHub CLI

```bash
gh auth login
gh auth status
gh repo create
gh repo clone
gh repo list
gh repo delete
gh issue create
gh issue list
gh issue close
gh pr create
gh pr list
gh pr merge
gh run list
gh api
gh gist create
gh release create
gh alias set
```

---

# 💪 DevOps Level Up

You can now:

- Create repos without browser
- Manage PRs fully from terminal
- Handle issues programmatically
- Monitor CI/CD workflows
- Automate GitHub at scale

This is real DevOps workflow 🔥

---

✅ Day 26 Completed – GitHub CLI Mastered
