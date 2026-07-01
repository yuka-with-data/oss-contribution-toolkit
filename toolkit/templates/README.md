# Templates
This directory contains reusable templates for pull requests, issues, and reviews.

To enable these templates in a GitHub repository, copy them into the following structure:

```txt
.github/
├── ISSUE_TEMPLATE/
│   ├── bug-report.md
│   ├── feature-request.md
│   └── documentation.md
└── pull_request_template.md
```

**Important:**
- The pull request template **must** be named `pull_request_template.md` for GitHub to detect it automatically.
- Issue templates **must** be placed inside the `.github/ISSUE_TEMPLATE/` directory.
- You may choose descriptive filenames for issue templates (such as `bug_report.md` or `feature_request.md`), but each template should have a unique filename.

## Included Templates
- `pull-request-template.md` – Template for submitting pull requests.
- `issue-bug-report.md` – Template for reporting bugs.
- `issue-feature-request.md` – Template for proposing new features.
- `issue-documentation.md` – Template for suggesting documentation improvements.
- `review-checklist.md` – A reference checklist for reviewing pull requests.