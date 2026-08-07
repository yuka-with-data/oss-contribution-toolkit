# Set Up Dependabot

## Overview

Dependabot helps open source projects keep their dependencies up to date. It checks configured dependencies and can automatically open pull requests when updates are available.

It can also track dependencies used by GitHub Actions workflows.

## 1. Create the Configulation File

Create the following file in the repository:

```bash
.github/dependabot.yml
```

## 2. Add a Basic Configulation

For example:

```yml
version: 2

updates:
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "weekly"

  - package-ecosystem: "pip"
    directory: "/"
    schedule:
      interval: "weekly"
```

The configulation above checks for update to GitHub Actions and Python dependencies once a week. The `package-ecosystem` value tels Dependabot what type of dependencies to check.

## 3. Review Dependabot Pull Requests

Once configured, Dependabot will periodically check for available udpates and create pull requests when appropriate.

Review these pull requests like any other contribution. Your project's CI workflows should run against the updates before merging.

### Recommend Practices

- Keep dependencies resonably up to date
- Review Dependabot pull requests before merging
- Use CI to test dependency updates before mering
- Configure Dependabot only for the ecosystems your project uses

## References

- [Dependabot quickstart guide](https://docs.github.com/en/code-security/tutorials/secure-your-dependencies/dependabot-quickstart)
- [About the dependabot.yml file](https://docs.github.com/en/code-security/concepts/supply-chain-security/about-the-dependabot-yml-file)
- [Keeping your actions up to date with Dependabot](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/auto-update-actions)
