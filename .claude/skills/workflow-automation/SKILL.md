# Workflow Automation

Automate development workflows using Git Hooks, scripts, and automated testing.

## What This Skill Does

This skill teaches Claude Code to build professional, safe workflow automations:

- **Git Hooks** — pre-commit, post-commit, pre-push hooks for quality gates
- **Scripts** — shell scripts, Node.js scripts for repetitive tasks
- **Automated Testing** — run tests on file changes, validate before deploy
- **CI/CD Basics** — GitHub Actions workflows, deployment scripts

## When to Use

- Setting up pre-commit hooks (linting, formatting, type-checking)
- Creating post-commit hooks (notifications, auto-deploy)
- Building automation scripts for repetitive tasks
- Setting up GitHub Actions for CI/CD

## Examples

### Pre-commit Hook: Lint & Format
```bash
#!/bin/sh
# .git/hooks/pre-commit
npx lint-staged
```

### Post-push Hook: Deploy to GitHub Pages
```bash
#!/bin/sh
# .git/hooks/post-push
git subtree push --prefix docs origin gh-pages
```

### GitHub Actions: Auto-test on Push
```yaml
name: Test
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm ci
      - run: npm test
```

## Guidelines

1. **Always make hooks executable** — `chmod +x .git/hooks/<hook-name>`
2. **Use husky for portable hooks** — shared across team via package.json
3. **Keep hooks fast** — slow hooks frustrate developers
4. **Never skip hooks silently** — if a hook fails, explain why clearly
5. **Test hooks locally** before sharing with the team
6. **Use lint-staged** for pre-commit — only check changed files, not entire repo
