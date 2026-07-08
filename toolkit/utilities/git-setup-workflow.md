# Git + Github Local to Remote Setup Workflow

## 1️⃣Initialize Git Locally
```bash
cd path/to/your/project
git init
```
- Create a `.git` folder
- Start tracking your project

## 2️⃣Add files and Commit Your Changes
```bash
git add .
git commit -m "Initial commit"
```

## 3️⃣Add Github Remote
Go to Github → Create a new repository → Copy the remote URL
```bash
git remote add origin https://github.com/USERNAME/REPO_NAME.git
```
- `origin` is the default name for your remote repo
- Replace with your actual Github URL

## 4️⃣Pull from Remote (If repo is not empty)
```bash
git pull origin main --allow-unrelated-histories
```
- Use this if Github already has files like README or LICENSE.

## 5️⃣Push Your Local Code to Github (First time)
```bash
git push -u origin main
```
- `-u` sets upstream tracking
- After this, you can use `git push`

## 6️⃣Verify Remote Connection
```bash
git remote -v
```
Expected output:
```
origin  https://github.com/USERNAME/REPO_NAME.git (fetch)
origin  https://github.com/USERNAME/REPO_NAME.git (push)
```

## 7️⃣Create a New Branch (Recommended)
After setting up your repository, always create a separate branch for development instead of using `main` directory.
```bash
git checkout -b feature-branch-name
```

## 🧠 After the Initial Setup (Daily Workflow)
```bash
git add .
git commit -m "your message"
git push
git pull
```

## ⚡ Notes
- Use `main` or `master` depending on repo default branch
- Always check branch with:
```bash
git branch
```
- If repo is empty, Step 4 is not needed.