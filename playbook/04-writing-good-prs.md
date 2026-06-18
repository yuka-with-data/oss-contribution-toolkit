# Writing Good Pull Requests (PRs)
A pull request (PR) is more than a code submission. It is a way to communicate your changes to maintainers and reviewers.

A well-crafted PR can make reviews faster and improve the chances of a smooth merge.

## Keep Changes Forcused
Each PR should solve a single problem whenever possible.

Good examples:
- Fixing a specific bug
- Improving documentation
- Updating an example
- Adding a small feature

Avoid combining multiple unrelated changes into the same PR.

# Write a Clear Title
Your **PR title** should briefly describe the change.

Example:
- "Fix typo in installation guide"
- "Update Python version in documentation"
- "Add validation for empty user input"

Reviewers should understand the purpose of the PR at a glance.

## Explain What Changed
If the repository provides a pull request template, follow it when writing your PR description. Templates are designed to give maintainers the information they need and help keep contributions consistent.

In general, your **PR description**, should answer a few simple questions:
- What changed?
- Why was the change needed?
- How was it tested?

Keep the explanation concise and easy to follow.

## Reference Related Issues
In your PR addresses an existing issue, reference it in the description.

This helps maintainers understand the context and track project progress.

## Make Reviews Easier
Before submitting:
- Review your own changes
- Remove unnecessary files or edits
- Make sure you are not committing files that do not belong in the PR
- Check project guidelines
- Ensure any required tests pass
- Verify that automated checks (CI), such as builds, linting, or test workflows, complete successfully if the project uses them

Small, clean PRs are easier to review than large, complex ones.