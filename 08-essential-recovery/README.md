# 08 - Essential Recovery Techniques

Everyone makes mistakes with Git. Here's how to fix the most common ones.

## Common "Oops" Scenarios

### 1. Unstaging Files

Remove files from staging area without losing changes:

```bash
# unstage a specific file
git reset HEAD filename.txt

# unstage all files
git reset HEAD
```

### 2. Discarding Local Changes

Throw away uncommitted changes:

```bash
# discard changes in a specific file
git checkout -- filename.txt

# discard all uncommitted changes (be careful!)
git checkout -- .
```

### 3. Fixing the Last Commit

#### Adding Forgotten Files
```bash
# add the forgotten file
git add forgotten-file.txt

# amend the last commit (don't do this if already pushed!)
git commit --amend --no-edit
```

#### Fixing Commit Message
```bash
# change the last commit message
git commit --amend -m "Corrected commit message"
```

## Understanding Git Reset

### Soft Reset
Move the branch pointer but keep changes staged:
```bash
git reset --soft HEAD~1
```

### Hard Reset
**⚠️ DANGEROUS**: Permanently delete changes:
```bash
git reset --hard HEAD~1
```

### When to Use Each
- **Soft reset**: Want to recommit with changes
- **Hard reset**: Want to completely undo commits (be very careful!)

## Stashing: Temporary Storage

Save work temporarily without committing:

```bash
# save current changes
git stash

# save with a message
git stash save "work in progress on login feature"

# list all stashes
git stash list

# apply most recent stash
git stash pop

# apply specific stash
git stash apply stash@{1}

# delete a stash
git stash drop stash@{0}
```

### When to Use Stash
- Need to quickly switch branches
- Want to pull latest changes but have uncommitted work
- Experimenting and want to save progress

## Practice Exercises

### Exercise 1: Unstaging Practice
1. Create and modify two files
2. Add both to staging
3. Unstage one file
4. Commit only the staged file

### Exercise 2: Stash Workflow
1. Start working on a file (don't commit)
2. Stash your changes
3. Switch to another branch
4. Come back and apply your stash

### Exercise 3: Amend Commit
1. Make a commit
2. Realize you forgot to add a file
3. Add the file and amend the commit

## Safety Tips

### Before Destructive Operations
```bash
# create a backup branch
git branch backup-before-reset

# or check what will be affected
git log --oneline -5
```

### Golden Rules
1. **Never** use `--hard` reset on shared branches
2. **Never** amend commits that have been pushed
3. **Always** double-check `git status` before destructive operations
4. When in doubt, create a backup branch first

## Getting Help

```bash
# if you're lost, check status
git status

# see what files have been modified
git diff

# see what's staged
git diff --staged
```
