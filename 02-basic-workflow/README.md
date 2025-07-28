# 02 - Basic Git Workflow

In this section, we'll learn the core Git workflow that you'll use every day as a developer.

## Understanding File States

Files in a Git repository can be in one of several states:

- **Untracked**: Git doesn't know about the file yet
- **Staged**: File is ready to be committed
- **Committed**: File is saved in Git's history

## Basic Commands

### Check Repository Status

Always start by checking what's happening in your repository:

```bash
git status
```

### Adding Files to Staging Area

```bash
# add a specific file
git add filename.txt

# add all files in current directory
git add .

# add all files in the repository
git add -A
```

### Creating Commits

```bash
# commit with a message
git commit -m "Add new feature"

# commit with a detailed message (opens editor)
git commit
```

### Viewing Commit History

```bash
# basic log
git log

# compact one-line format
git log --oneline

# with visual graph
git log --oneline --graph

# limit to last 5 commits
git log -5
```

## Practice Exercise

1. Create a new file called `index.html`
2. Check the status with `git status`
3. Add the file to staging with `git add index.html`
4. Check status again
5. Commit with message "Add index page"
6. View the commit history

## Writing Good Commit Messages

- Start with a verb (Add, Fix, Update, Remove)
- Keep the first line under 50 characters
- Use present tense
- Be descriptive but concise

Examples:
- ✅ "Add user authentication system"
- ✅ "Fix navigation menu on mobile devices"
- ❌ "stuff"
- ❌ "fixed bug"
