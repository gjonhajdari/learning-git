# 03 - Branching Essentials

Branching allows you to work on different features without affecting the main codebase.

## Why Use Branches?

- Work on features in isolation
- Collaborate with team members safely
- Experiment without breaking working code
- Organize work by feature/bug/task

## Basic Branching Commands

### Creating and Switching Branches

```bash
# create a new branch
git branch feature-login

# switch to the branch
git checkout feature-login

# create and switch in one command
git checkout -b feature-login

# newer syntax (Git 2.23+)
git switch -c feature-login
```

### Viewing Branches

```bash
# list local branches
git branch

# list all branches (local and remote)
git branch -a

# see current branch
git branch --show-current
```

### Merge Workflow (Traditional Approach)

```bash
# switch back to main branch
git checkout main
git pull origin main

# integrate your feature branch using merge
git merge feature-login
```

This creates a merge commit that combines the changes from both branches.

*In the next section, we'll learn what happens when Git can't automatically merge branches - conflicts are a normal part of development that every developer needs to understand.*

## Understanding Integration Methods

### Fast-Forward Integration
When no new commits exist on the target branch, Git simply moves the pointer forward. This happens naturally with both merge and rebase.

### Merge Commit Integration
When both branches have new commits, merge creates a merge commit to combine the changes. This preserves the branching history.

*In the next section, we'll compare this with rebase, which creates linear history by replaying commits. Both approaches have their place in modern Git workflows.*

## Practice Exercise

1. Create a new branch called `add-navbar`
2. Switch to the new branch
3. Create a file called `navbar.html`
4. Add and commit the file
5. Switch back to `main`
6. Merge the `add-navbar` branch
7. View the commit history with `git log --oneline --graph`

## Branch Naming Conventions

- `feature/user-auth` - for new features
- `bugfix/login-error` - for bug fixes
- `hotfix/security-patch` - for urgent fixes
- Use descriptive names, not just `test` or `temp`
