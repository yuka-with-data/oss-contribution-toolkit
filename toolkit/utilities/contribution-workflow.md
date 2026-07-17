# Contribution Full Workflow: Fork → Clone → PR

## 🔰IMPORTANT: First Rule

Before contributing to any open source repo:
> Always fork → then clone your fork (NOT the original repo)

## 1️⃣Clone your fork locally

In your terminal (inside your desired directory)

```bash
git clone https://github.com/YOUR-USERNAME/REPO_NAME.git
cd REPO_NAME
```

## 2️⃣Add the original repo as `upstream`

This lets you sync with the official project repo:

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/REPO_NAME.git
```

Check:

```bash
git remote -v
```

You should see:

- `origin` → your fork on Github
- `upstream` → original/official repo

## 3️⃣Sync with latest upstream code

Before starting work, always pull the latest changes from upstream:

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

Optional but recommended:

```bash
git push origin main
```

## 4️⃣Create a new branch for your work

⚠️ Never work directly on `main`:

```bash
git checkout -b my-feature-branch
```

Example:

```bash
git checkout -b fix-typo-in-readme
```

## 5️⃣Make your changes locally

- Edit files
- Test locally if needed
- Save changes

## 6️⃣Validate changes before commiting

Before staging/committing, make sure your changes pass the project's required checks.

### 🔍Check the respository first

Look for instructions in :

- `README.md`
- `CONTRIBUTING.md`
- CI configs (e.g., `.github/workflows/`)

Common validation tools include:

- `pre-commit` (linting, formatting, hooks)
- `pytest` (tests)
- `ESLint` (JS/TS linting)
- `Black` (Python formatting)

### If the project uses `pre-commit`

#### ▶ For small changes (recommended)

```bash
pre-commit run --files <changed-file>
```

#### ▶ For multiple files changed

```bash
pre-commit run --all-files
```

#### Tips

- Do NOT rely on `--all-files` for small PRs
- Always re-check after hooks run:

```bash
git status
git diff
```

- If pre-commit modifies files, re-stage them before commiting (if needed)

```bash
git add .
```

#### ⚠️ Important ruoles

- Never skip validation -- even for small changes
- Fix issues locally before commiting
- CI should confirm your work, not catch preventable mistakes

## 7️⃣Stage and commit your changes

⚠️ Make sure pre-commit passed before this step

```bash
git add .
git commit -m "Brief description of your changes"
```

## 8️⃣Push your branch to your fork

For the first time push, use `-u`

```bash
git push -u origin my-feature-branch
```

## 9️⃣Create a Pull Request (PR)

Go to your fork on GitHub:

- Click "Compare & pull request"
- Add a clear title and description

Set:

- Base repository: `ORIGINAL-OWNER/REPO_NAME`
- Base branch: `main`
- Head repository: `YOUR-USERNAME/REPO_NAME` (your fork)
- Compare: `my-feature-branch` (your feature branch)

Submit.

## 🔁After submitting PR

If reviewer asks for changes:

1. Make changes locally on the same branch
2. Stage and commit changes
3. Push to the same branch:

```bash
git add.
git commit -m "Address review comments"
git push
```

No new PR needed -- it updates the existing PR automatically.

## ✅PR gets merged

Once your PR is merged:

1. Switch back to main:

```bash
git checkout main
```

2. Fetch latest changes from upstream (official repo):

```bash
git fetch upstream
```

3. Rebase your local main onto upstream/main

```bash
git merge upstream/main
```

4. Push updated main to your fork (origin)

```bash
git push origin main
```

5. Delete your feature branch locally

```bash
git branch -d my-feature-branch
```

6. Delete your feature branch on Github

```bash
git push origin --delete my-feature-branch
```

7. Clean up stale remote references (optional)

```bash
git fetch --prume
```

## 🔄Keep your branch updated (important later)

If upstream changes while you work:

```bash
git fetch upstream
git checkout main
git merge upstream/main
git checkout my-feature-branch
git rebase main
git push --force
```

## 🧠Mental Model

```txt
Original Repo (upstream)
        ↑
        | PR
Your Fork (origin)
        ↑
        | push
Local Repo
```

## 📝Final Checklist

- [ ] Forked repo
- [ ] Cloned fork locally (not from original)
- [ ] Added upstream remote
- [ ] Created feature branch
- [ ] Made changes, staged, committed
- [ ] Pushed branch to fork with `-u`
- [ ] Opened PR
