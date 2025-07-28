# 04 - Rebase vs Merge: Modern Git Practices

Understanding both merge and rebase approaches, and why rebase is often the preferred choice for modern development workflows.

## Understanding Both Approaches

### Merge: The Traditional Way
When you use `git merge`, you preserve the branching history and create merge commits:

```
* d4f6b2a Merge branch 'feature-login'
|\
| * a1b2c3d Add login validation
| * e4f5g6h Create login form
|/
* h7i8j9k Fix navbar styling
```

**Merge is good when:**
- You want to preserve the context of feature development
- Multiple people worked on the branch
- You're integrating a completed feature into main
- Working with public/shared repositories

### Rebase: The Modern Preference
Rebase rewrites history to create a clean, linear timeline:

```
* a1b2c3d Add login validation
* e4f5g6h Create login form  
* h7i8j9k Fix navbar styling
```

**Rebase is preferred when:**
- You want clean, readable project history
- Working on personal feature branches
- Updating your branch with latest changes
- Preparing code for review

## Recommended Workflow: Rebase-First Approach

### Step 1: Update Main Branch
```bash
git checkout main
git pull origin main
```

### Step 2: Rebase Your Feature Branch (Recommended)
```bash
git checkout feature-login
git rebase main
```

### Step 3: Push with Force-with-Lease
```bash
# For rebased branches, use force-with-lease for safety
git push --force-with-lease origin feature-login
```

### Alternative: Traditional Merge Approach
```bash
git checkout feature-login
git merge main  # Creates merge commit
git push origin feature-login  # No force needed
```

## When to Use Each Approach

### Prefer Rebase When:
- ✅ Working on personal feature branches
- ✅ Updating your branch with latest main
- ✅ You want clean, linear history
- ✅ Preparing for code review
- ✅ You're the only one working on the branch

### Use Merge When:
- ✅ Integrating completed features into main
- ✅ Multiple people are working on the same branch
- ✅ You want to preserve feature development context
- ✅ Working with public/shared branches
- ✅ Following team conventions that prefer merge

## Both Approaches in Practice

### The Rebase-First Daily Workflow (Recommended)
```bash
# Morning routine
git checkout main
git pull --rebase origin main

# Start new feature
git checkout -b feature-awesome
# ... work and commit ...

# Stay up-to-date (daily)
git checkout main
git pull --rebase origin main
git checkout feature-awesome
git rebase main

# When feature is ready
git push --force-with-lease origin feature-awesome
# Create pull request for review
# Maintainer merges via PR (often squash merge)
```

### Traditional Merge Workflow
```bash
# Morning routine
git checkout main
git pull origin main

# Start new feature
git checkout -b feature-awesome
# ... work and commit ...

# Stay up-to-date (when needed)
git checkout feature-awesome
git merge main

# When feature is ready
git push origin feature-awesome
# Create pull request for review
```

## Rebase Commands

### Interactive Rebase (Advanced)
```bash
# rebase last 3 commits interactively
git rebase -i HEAD~3

# rebase against main branch
git rebase -i main
```

### Abort if Things Go Wrong
```bash
git rebase --abort
```

### Continue After Resolving Conflicts
```bash
# after fixing conflicts
git add .
git rebase --continue
```

## Practice Exercise: Compare Both Approaches

### Setup
1. Create a new branch `feature-about`
2. Make 2-3 commits on this branch
3. Switch to main and make a commit there
4. Now we'll try both approaches...

### Exercise A: Rebase Approach (Try This First)
1. Go to `feature-about`: `git checkout feature-about`
2. Rebase onto main: `git rebase main`
3. Examine the history: `git log --oneline --graph`
4. Notice the clean, linear history

### Exercise B: Merge Approach (For Comparison)
1. Create another branch: `git checkout -b feature-contact`
2. Make 2-3 commits on this branch
3. Switch to main: `git checkout main`
4. Merge the branch: `git merge feature-contact`
5. Examine the history: `git log --oneline --graph`
6. Notice the merge commit and branching visualization

### Discussion Questions
- Which history is easier to read?
- Which approach would be better for code review?
- When might you prefer the merge approach?

## The Golden Rules of Rebase

### ⚠️ NEVER rebase public branches
```bash
# NEVER do this:
git checkout main
git rebase some-branch  # DON'T!
```

### ⚠️ NEVER rebase shared branches
If others are working on the branch, don't rebase it.

### ✅ DO rebase your personal feature branches
```bash
# This is good:
git checkout my-feature
git rebase main
```

## Rebase vs Merge Summary

| Scenario | Command | Why |
|----------|---------|-----|
| Update feature branch | `git rebase main` | Clean history |
| Integrate to main | `git merge feature` | Preserve feature context |
| Daily sync | `git pull --rebase` | Avoid merge commits |
| Shared branch updates | `git merge` | Don't rewrite shared history |

## Common Rebase Workflow

```bash
# Start of day - update main
git checkout main
git pull origin main

# Update your feature branch
git checkout feature-xyz
git rebase main

# Continue working...
git add .
git commit -m "Add new functionality"

# Before pushing for the first time
git push -u origin feature-xyz

# After making more commits
git push --force-with-lease origin feature-xyz
```

This workflow keeps your branch up-to-date and creates clean, linear history that's easy to understand and review.
