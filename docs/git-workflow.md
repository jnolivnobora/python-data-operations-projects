# Git Workflow

## Overview

Every project in this portfolio follows a consistent Git workflow
modeled on professional software delivery. No code ever goes directly
to `main` without a branch, a commit, and a pull request — even
when working solo.

This habit matters for your role. In a data operations team, every
change to a script, a config file, or a SQL query is tracked. If a
validation rule changes and causes a downstream error, the team needs
to know exactly what changed, who changed it, and why. Git is the
audit trail that makes that possible.

---

## Branch naming convention

| Type | Pattern | Example |
|------|---------|---------|
| New feature | `feature/short-description` | `feature/csv-ingestion` |
| Bug fix | `fix/short-description` | `fix/date-validation-edge-case` |
| Documentation | `docs/short-description` | `docs/update-readme` |
| Test | `test/short-description` | `test/add-reconciliation-tests` |
| Chore / setup | `chore/short-description` | `chore/add-gitignore` |
| Refactor | `refactor/short-description` | `refactor/extract-validation-helpers` |

Rules:

- Always use lowercase and hyphens — never spaces or underscores
- Keep branch names short and descriptive
- One branch per feature or fix — never mix unrelated changes

---

## Commit message convention

Follow the Conventional Commits format:

```
<type>: <short description in present tense>

[optional body explaining why, not what]
```

### Types

| Type | When to use |
|------|------------|
| `feat` | Adding a new feature or capability |
| `fix` | Fixing a bug or incorrect behavior |
| `docs` | Documentation only changes |
| `test` | Adding or updating tests |
| `chore` | Setup, config, dependencies, gitignore |
| `refactor` | Code restructuring without behavior change |
| `style` | Formatting only — no logic change |

### Examples

```
feat: add duplicate loan ID detection
fix: correct date format validation for YYYY-MM-DD edge case
docs: update README with usage instructions and sample output
test: add pytest for null field checks in required field validator
chore: add .gitignore and requirements.txt
refactor: extract validation logic into separate helper functions
feat: generate exception report as Excel with openpyxl
feat: add CSV ingestion with pandas and encoding detection
```

Rules:

- Use present tense: "add" not "added", "fix" not "fixed"
- Keep the first line under 72 characters
- Explain the why in the body if the what is not obvious
- One logical change per commit — do not bundle unrelated changes

---

## The full workflow loop

Use this loop for every feature, fix, or change. Never skip steps.

```bash
# Step 1: Start from an up-to-date main branch
git checkout main
git pull origin main

# Step 2: Create a feature branch
git checkout -b feature/your-feature-name

# Step 3: Write your code, tests, and documentation

# Step 4: Check what changed
git status
git diff

# Step 5: Stage your changes
git add .
# Or stage specific files:
git add src/validator.py tests/test_validator.py

# Step 6: Commit with a clear message
git commit -m "feat: add required field validation for loan records"

# Step 7: Push the branch to GitHub
git push origin feature/your-feature-name

# Step 8: Open a Pull Request on GitHub
# Go to your repo → Compare & pull request → fill in the description

# Step 9: Review the PR against the Definition of Done checklist

# Step 10: Merge the PR on GitHub

# Step 11: Pull the merged changes back to your local main
git checkout main
git pull origin main

# Step 12: Delete the feature branch locally
git branch -d feature/your-feature-name
```

---

## Pull request description template

Use this for every pull request:

```
## What this PR does
[1–2 sentences describing the change in plain language]

## Why
[Business or learning reason for this change]

## Changes made
- [File or module changed and what was added or fixed]
- [Another file changed and why]

## How to test
1. [Command to run]
2. [Expected output]

## Definition of Done checklist
- [ ] Code works as expected
- [ ] Tests pass
- [ ] No secrets or real data committed
- [ ] README updated
- [ ] Errors handled with clear messages
- [ ] Logging added where useful
- [ ] Acceptance criteria are satisfied
```

---

## Linking Issues to pull requests

When you open a PR, reference the GitHub Issue it closes:

```
Closes #3
Closes #4
```

GitHub will automatically close those Issues when the PR is merged.
This keeps your Kanban board clean and creates a traceable link
between the work item and the code that delivered it.

---

## Commit frequency

Commit often — at least once per coding session, and whenever a
logical unit of work is complete. Do not wait until the entire
feature is done before your first commit.

Good commit frequency looks like:

```
chore: add project folder structure and .gitignore
feat: add read_csv_file function with pathlib
feat: add write_csv_file function
test: add tests for read_csv_file happy path
test: add tests for FileNotFoundError edge case
docs: add module docstring to file_utils.py
feat: add logger_config.py with console and file handlers
docs: update README with setup and run instructions
```

Each commit is a checkpoint you can return to if something breaks.

---

## .gitignore rules

Every project must have a `.gitignore` that excludes at minimum:

```
# Virtual environment
.venv/

# Python cache
__pycache__/
*.pyc
*.pyo

# Environment variables — NEVER commit this
.env

# OS files
.DS_Store
Thumbs.db

# Test output
.pytest_cache/
.coverage

# Generated reports (not source)
reports/
*.log

# Jupyter notebook checkpoints
.ipynb_checkpoints/

# Database files (unless sample)
*.db
*.sqlite
```

---

## Common Git mistakes and how to avoid them

| Mistake | How to avoid |
|---------|-------------|
| Committing `.env` with real secrets | Always add `.env` to `.gitignore` before the first commit |
| Pushing directly to `main` | Always create a branch first — make it a reflex |
| Vague commit messages like "fix stuff" | Always use the Conventional Commits format |
| One giant commit with everything | Commit after each logical unit of work |
| Forgetting to pull before branching | Always run `git pull origin main` before `git checkout -b` |
| Committing `__pycache__/` or `.venv/` | Check your `.gitignore` before the first commit in every project |
| Not linking Issues to PRs | Use `Closes #N` in every PR description |

---

## Useful Git commands reference

```bash
# See what branch you are on and what has changed
git status

# See the commit history
git log --oneline

# See what changed in a specific file
git diff src/validator.py

# Undo changes to a file before staging
git checkout -- src/validator.py

# Unstage a file you accidentally staged
git restore --staged src/validator.py

# See all local branches
git branch

# Delete a local branch after it is merged
git branch -d feature/branch-name

# See all remote branches
git branch -r

# Fetch latest changes without merging
git fetch origin

# Check your remote connections
git remote -v
```
