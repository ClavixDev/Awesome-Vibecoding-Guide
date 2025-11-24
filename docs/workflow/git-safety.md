# Git Safety for AI-Assisted Development

Why Git is your ultimate safety net when coding with AI. This guide focuses on preventing AI coding disasters—for detailed workflow strategies, see [Git Strategies](./git-strategies.md).

## The Problem: AI Can Break Everything at Once

AI coding tools are powerful. The latest models can regenerate large chunks of code in seconds. That's their strength—but it means:

- **One bad prompt can break multiple files simultaneously**
- Without version control, there's no undo button
- "AI just rewrote my entire component and now nothing works"

The solution isn't avoiding AI—it's using Git as your safety net.

---

## The 15-Minute Setup (Non-Negotiable)

Before writing any code with AI assistance:

```bash
# Initialize Git
git init
git add .
git commit -m "Initial working state"

# Create remote backup (GitHub, GitLab, etc.)
git remote add origin https://github.com/yourusername/project.git
git push -u origin main
```

**That's it.** One command and you have a restore point. Skip this step and you're building a house of cards.

---

## The Daily Safety Workflow

### Morning: Create a Feature Branch

```bash
git checkout -b feature/todays-work
```

This isolates today's AI experiments from your stable code.

### Before ANY Major AI Prompt

```bash
git add .
git commit -m "Before AI regeneration - working"
```

**This is critical.** Every commit before an AI operation gives you a guaranteed restore point.

### If AI Breaks Something

```bash
git reset --hard HEAD
```

**One command and the chaos is gone.** You're back to the last working state.

### End of Day

```bash
git push origin feature/todays-work
```

Your work is backed up. Tomorrow, you can continue or merge to main.

---

## Three Critical Mistakes to Avoid

### 1. Working Directly on Main (Production Branch)

**The Problem:** You push AI-generated code directly to main, it breaks production, clients are affected.

**The Fix:**
```bash
# Always create feature branches
git checkout -b feature/new-functionality

# Test thoroughly on branch
# Only merge when verified working
git checkout main
git merge feature/new-functionality
```

### 2. Storing Secrets in AI Tool Settings Only

**The Problem:** You configure API keys in your AI tool's settings. You switch tools or the platform has issues—now you've lost access to your own project's secrets.

**The Fix:**
```bash
# Create .env.example (commit this - no actual values)
DATABASE_URL=
API_KEY=
STRIPE_SECRET=

# Create .env (never commit - add to .gitignore)
DATABASE_URL=postgres://actual/connection
API_KEY=sk-actual-key
STRIPE_SECRET=sk_live_actual
```

Add to `.gitignore`:
```
.env
.env.local
.env.production
```

Now your secrets are documented AND secure.

### 3. Downloading Projects Without Git History

**The Problem:** You export from an AI platform using "Download ZIP". No history, no recovery options.

**The Fix:**
- Always `git clone` repositories
- When exporting from AI platforms, immediately initialize Git
- Push to remote before making any AI changes

---

## AI-Specific Safety Patterns

### Branch Per AI Session

**Pattern:** One AI conversation = One feature branch

```bash
# Starting new AI session for user authentication
git checkout -b feat/user-authentication

# All AI-generated code goes here
# Multiple commits as you iterate

# When feature is complete and tested
git checkout main
git merge feat/user-authentication
git push origin main

# Clean up
git branch -d feat/user-authentication
```

**Benefits:**
- Clear rollback boundaries
- Easy to discard entire AI session if it went wrong
- Context isolation per feature
- Safe experimentation

### Safety Commits Before AI Operations

**The Rule:** Commit BEFORE asking AI to regenerate code.

```bash
# Working state
git add .
git commit -m "Working: user form complete"

# Now ask AI to refactor/regenerate
# If it breaks...
git reset --hard HEAD
# Back to working state instantly
```

**Commit frequency guidelines:**
- Every 30-60 minutes of work
- Before any "regenerate this file" prompt
- Before any "refactor" request
- After every successfully working feature

### Recovery Speed Targets

| Recovery Type | Target Time | Method |
|--------------|-------------|--------|
| Emergency rollback | < 2 minutes | `git reset --hard [hash]` |
| Feature revert | < 1 minute | `git revert [hash]` |
| File recovery | Instant | `git checkout HEAD -- file.js` |

---

## Quick Reference: Recovery Commands

| Situation | Command |
|-----------|---------|
| AI just broke everything | `git reset --hard HEAD` |
| Find last good state | `git log --oneline` |
| Undo last commit (keep changes) | `git reset --soft HEAD~1` |
| Revert specific commit | `git revert [hash]` |
| Restore single file | `git checkout HEAD -- path/to/file` |
| See what changed | `git diff` |
| Nuclear option (reset to known good) | `git reset --hard [good-hash]` then `git push --force` |

---

## Recommended Branch Structure

```
main (production)
  └── dev (integration - optional for solo)
       ├── feat/user-login
       ├── feat/dashboard
       ├── fix/auth-bug
       └── hotfix/critical-issue
```

**Branch naming conventions:**
- `feat/` - New features
- `fix/` - Bug fixes
- `hotfix/` - Critical production fixes
- `refactor/` - Code improvements
- `content/` - Content updates

---

## The Safety Checklist

### Before Starting Any AI Coding Session

- [ ] Git repository initialized
- [ ] Remote backup configured (GitHub/GitLab)
- [ ] Feature branch created
- [ ] Initial commit made

### During Development

- [ ] Commit before major AI prompts
- [ ] Test after each AI-generated change
- [ ] Push to remote at end of session
- [ ] Don't store secrets in AI tool settings only

### When Something Breaks

- [ ] Don't panic—Git has your back
- [ ] Check `git log --oneline` for last good commit
- [ ] Use `git reset --hard HEAD` for quick recovery
- [ ] If needed, `git reset --hard [specific-hash]`

---

## Why This Matters

> "The developers moving fastest aren't skipping Git. They're using it as their safety net."

With proper Git workflow:

- **No fear of "breaking everything"**—you can always recover
- **Experiment freely with AI**—bad results are easily undone
- **Instant recovery from bad prompts**—one command
- **Clear history of what AI generated**—for learning and debugging

Git isn't overhead when coding with AI. It's the foundation that makes fearless AI-assisted development possible.

---

**Related Documentation:**
- [Git Strategies](./git-strategies.md) - Detailed two-phase workflow for development and maintenance
- [Phase 2: Development](./phase-2-development.md) - Development workflow
- [Quickstart](../quickstart/README.md) - Getting started with Git and project setup
- [Troubleshooting](../troubleshooting/README.md) - Recovery patterns and debugging

**Back to:** [Workflow Overview](./README.md)
