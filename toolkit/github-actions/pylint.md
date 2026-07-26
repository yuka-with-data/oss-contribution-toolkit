# Pylint GitHub Action

Pylint is a static analysis tool for Python that detect errors, enforce coding standards, and improve code quality.

Integrating Pylint with GitHub Actions allows every push and pull request to be automatically checked for common issues before code is merged.

## 1. Install Pylint

Install Pylint in your Python environment:

```bash
pip install pylint
```

If your project uses dependency management, consider adding Pylint as a development dependency so contributors use the same version.

## 2. Add the GitHub Actions Workflow

Create the workflow file inside the `.github/workflow/` directory:

```txt
.github/workflows/pylint.yml
```

>[!NOTE]
> If the `.github/workflows/` directory does not exist, create it first.

This workflow automatically runs Pylint whenever changes are pushed or pull request is opened. It sets up a Python environment, installs Pylint, and analyzes your project's Python files for potential issues.

Example:

```yml
name: Pylint

on:
  push:

  pull_request:
    branches: [main]

jobs:
  pylint:
    runs-on: ubuntu-latest

    strategy:
      matrix:
        python-version: ["3.12"]

    steps:
      - name: Checkout repository
        uses: actions/checkout@v7

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}

      - name: Install Pylint
        run: |
          python -m pip install --upgrade pip
          pip install pylint

      - name: Run Pylint
        run: |
          pylint $(git ls-files '*.py')
```

During the initial setup, allowing the workflow to run on every push can help identify existing issues across the repository.

Once your project is stable, consider limiting the workflow to the `main` branch and pull requests to reduce unnecessary workflow runs.

## 3. Fix Existing Issues

Run Pylint locally before pushing changes:

```bash
pylint $(git ls-files '*.py')
```

Review the reported issues and update your code accordingly.

Common issues include:

- Missing module, class, or function docstrings
- Unused imports or variables
- Naming convention violations
- Import ordering

Depending on your project, some rules may be configured differently or intentionally disabled.

## 4. Verify the Workflow

Before pushing changes, run Pylint locally to confirm your Python files pass the configured checks.

If the command completes successfully, push your changes to GitHub.

GitHub Actions will automatically run the same Pylint workflow. Confirm that the workflow passes in the **Actions** tab before merging the pull request.

Running Pylint locally first helps catch issues early and reduces unnecessary CI failures.

## Benefits

- Improves overall code quality
- Detects common Python issues early
- Encourages consistent coding standards
- Reduces review time for maintainers
- Provides contributors with immediate feedback
