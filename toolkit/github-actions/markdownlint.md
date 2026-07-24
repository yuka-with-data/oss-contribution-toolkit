# Markdownlint GitHub Workflow

`Markdownlint` helps maintain consistent Markdown formatting across a repository. For documentation-heavy projects, adding markdownlint to GitHub Actions allows formatting issues to be detected automatically during pull requests.

## 1. Install markdownlint-cli2

[`markdownlint-cli2`](https://github.com/DavidAnson/markdownlint-cli2) is a fast Markdown linting tool from David Anson. Install it as a development dependency:

```bash
npm install markdownlint-cli2 --save-dev
```

This creates:

- `package.json`
- `package-lock.json`

Commit both files, but **DO NOT** commit `note_modules/`.

>[!IMPORTANT]
> Add `node_modules/` to `.gitignore` file before committing changes.

## 2. Add Markdownlint Configulation

Create configulation file at the **project root**:

```txt
.markdownlint-cli2.jsonc
```

Example:

```jsonc
{
  "config": {
    // Disable rules that do not fit project style.
    "MD013": false
  }
}
```

Only disable rules when there is a project-specific reason.

## 3. Create GitHub Actions Workflow

Create the workflow file inside the `.github/workflows/` directory:

```bash
.github/workflows/markdownlint.yml
```

If the `.github/workflows/` directory does not exist, create it first.

This file defines when the markdownlint check runs and the steps GitHub Actions should execute.

Example:

```yml
name: Markdown Lint

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  markdownlint:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v7

      - name: Run markdownlint-cli2
        uses: DavidAnson/markdownlint-cli2-action@v24.0.0
        with:
          globs: |
            **/*.md
```

## 4. Fix Existing Markdown Issues

After adding the workflow, run markdownlint locally to find and automatically fix supporting formatting issues before pushing changes.

Run:

```bash
npx markdownlint-cli2 --fix "**/*.md"
```

This applies available automatic fixes, such as:

- MD022 & 032: Missing blank lines around headings and lists
- MD034: Bare URL formatting
- MD047: Missing trailing newlines

Some rules cannot be fixed automatically and require manual reviews and changes.

Review the changes before committing:

```bash
git diff
git status
```

Make sure the changes are only expected Markdown formatting updates.

## 5. Verify the Workflow

Before pushing any changes, run markdownlint locally to confirm that all Markdown files pass the configured rules:

```bash
npx markdownlint-cli2 "**/*.md"
```

If the command completes without errors, push your changes to GitHub.

GitHub Actions will run the same markdownlint check automatically. Confirm that the workflow passes in the **Actions** tab before merging the pull request.

Running the check locally first helps catch formatting issues early and avoids unnecessary CI failures.

1. Fix locally.
2. Verify locally.
3. Push changes.
4. Let GitHub Actions confirm the same check in CI.

It also reinforces a good OSS contributor habit: **do not rely only on CI to discover simple formatting issues.**
