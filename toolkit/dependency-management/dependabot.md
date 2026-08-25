# Set Up Dependabot

## Overview

Dependabot helps open source projects keep their dependencies up to date. It checks configured dependencies and can automatically open pull requests when updates are available.

It can also track dependencies used by GitHub Actions workflows.

## 1. Create the Configuration File

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

The configulation above checks for update to GitHub Actions and Python dependencies once a week. The `package-ecosystem` value tells Dependabot what type of dependencies to check.

## 3. Enable Dependabot in Repository Settings

Before Dependabot can manage dependency updates, check your repository's Dependabot settings.

Go to **Settings → Security and Quality → Advanced Security** and enable the Dependabot features available for your repository, such as:

- Dependabot alerts
- Dependabot security updates
- Dependabot version updates

The available options may vary depending on your repository and GitHub plan.

Once enabled, Dependabot can use the `.github/dependabot.yml` configulation to check for dependency updates.

## 4. Review Dependabot Pull Requests

Once configured, Dependabot will periodically check for available updates and create pull requests when appropriate.

Review these pull requests like any other contribution. Your project's CI workflows should run against the updates before merging.

### Recommend Practices

- Keep dependencies reasonably up to date
- Review Dependabot pull requests before merging
- Use CI to test dependency updates before merging
- Configure Dependabot only for the ecosystems your project uses

## References

- [Dependabot quickstart guide](https://docs.github.com/en/code-security/tutorials/secure-your-dependencies/dependabot-quickstart)
- [About the dependabot.yml file](https://docs.github.com/en/code-security/concepts/supply-chain-security/about-the-dependabot-yml-file)
- [Keeping your actions up to date with Dependabot](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/auto-update-actions)
