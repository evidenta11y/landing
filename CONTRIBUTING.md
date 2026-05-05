# Contributing to the Evidenta11y Landing Page

Thanks for contributing! This guide walks through how to clone the repo and submit changes via pull request.

## Prerequisites

Before starting, make sure you have:

- Git installed (`git --version` to check)
- A GitHub account with access to the repo
- SSH keys set up with GitHub, or HTTPS with a personal access token
- A terminal/command line tool

---

## 1. Clone the Repo

Open your terminal, navigate to your home directory, and clone the repo:

```bash
cd ~
git clone https://github.com/evidenta11y/landing-page.git
cd landing-page
```

If you prefer SSH:

```bash
git clone git@github.com:evidenta11y/landing-page.git
cd landing-page
```

Verify you're connected to the right remote:

```bash
git remote -v
```

You should see `origin` pointing to the evidenta11y/landing-page repo.

---

## 2. Create and Checkout a Branch

Always work on a branch — never commit directly to `main`.

First, make sure your local `main` is up to date:

```bash
git checkout main
git pull origin main
```

Then create your branch. Use a descriptive name with a prefix like `feat/`, `fix/`, `chore/`, or `docs/`:

```bash
git checkout -b feat/update-hero-copy
```

The `-b` flag creates the branch and switches to it in one step. Confirm you're on the new branch:

```bash
git branch
```

The asterisk (`*`) should be next to your new branch name.

---

## 3. Make Your Updates

Edit files in your editor of choice (VS Code, Cursor, etc.). As you work, check what's changed:

```bash
git status              # see which files are modified
git diff                # see the actual line-by-line changes
```

When you're ready to save your work, stage and commit:

```bash
git add .                                    # stage all changes
# OR stage specific files:
git add src/components/Hero.tsx

git commit -m "Update hero headline and CTA copy"
```

**Commit message tips:**

- Keep the subject line under ~72 characters
- Use imperative mood ("Add button" not "Added button")
- Make multiple smaller commits rather than one giant one if the work is logically separable

You can run `git log --oneline` anytime to see your commit history.

---

## 4. Push to the Branch

Push your branch up to GitHub:

```bash
git push -u origin feat/update-hero-copy
```

The `-u` flag sets the upstream tracking, so future pushes from this branch only need `git push`.

If you make more changes after the initial push, just commit and push again:

```bash
git add .
git commit -m "Fix mobile spacing on hero"
git push
```

---

## 5. Create a Pull Request

Go to <https://github.com/evidenta11y/landing-page> in your browser. GitHub will usually show a yellow banner suggesting you open a PR for your recently pushed branch — click **"Compare & pull request"**.

If you don't see the banner:

1. Click the **Pull requests** tab
2. Click **New pull request**
3. Set `base: main` and `compare: feat/update-hero-copy`
4. Click **Create pull request**

**Fill out the PR thoughtfully:**

- **Title** — clear and specific (e.g., "Update hero copy and CTA on landing page")
- **Description** — explain *what* changed and *why*. Include screenshots or screen recordings for any visual changes.
- **Reviewers** — request review from a teammate
- **Labels** — add relevant ones if your repo uses them (e.g., `enhancement`, `bug`, `a11y`)
- **Linked issues** — reference any related issue with `Closes #123` or `Fixes #123` so it auto-closes on merge

Click **Create pull request**.

---

## 6. PR Review and Merge

### While waiting for review

If CI checks are configured, watch them run at the bottom of the PR. Fix any failures before pinging a reviewer.

### Responding to feedback

If a reviewer requests changes, make them locally on the same branch:

```bash
# make sure you're still on your branch
git checkout feat/update-hero-copy

# edit files, then:
git add .
git commit -m "Address review feedback: fix alt text on hero image"
git push
```

The PR updates automatically with the new commits. Reply to comments and click **"Re-request review"** when ready.

### Keeping your branch up to date

If `main` has moved forward while your PR sat open, sync it:

```bash
git checkout main
git pull origin main
git checkout feat/update-hero-copy
git merge main
# resolve any conflicts, then:
git push
```

### Merging

Once approved and all checks pass, merge the PR. On GitHub, click **Merge pull request**. Common merge strategies:

- **Squash and merge** — combines all your commits into one (cleanest history, good default for feature branches)
- **Rebase and merge** — keeps individual commits but linearizes them
- **Create a merge commit** — preserves the full branch history

Pick whichever matches your team's convention.

### Cleanup

After merging, delete the branch on GitHub (there's a button right after merging) and locally:

```bash
git checkout main
git pull origin main
git branch -d feat/update-hero-copy
```

You're done — and ready to start the next branch.

---

## Quick Reference Cheat Sheet

```bash
# 1. Clone
cd ~
git clone https://github.com/evidenta11y/landing-page.git && cd landing-page

# 2. Branch
git checkout main && git pull
git checkout -b feat/your-change

# 3. Make changes, then:
git add .
git commit -m "Descriptive message"

# 4. Push
git push -u origin feat/your-change

# 5. Open PR on github.com

# 6. After merge, clean up
git checkout main && git pull
git branch -d feat/your-change
```
