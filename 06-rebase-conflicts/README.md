# 06 - Handling Rebase Conflicts

Now that you understand merge conflicts, let's learn about rebase conflicts - they're similar but have important differences.

## Understanding Rebase Conflicts

When rebasing, Git applies your commits one by one onto the target branch. If any commit conflicts with changes in the target branch, the rebase stops and asks you to resolve it.

## Rebase Conflict vs Merge Conflict

### Merge Conflicts
- Happen once at the end
- Show changes from both branches
- Create a merge commit

### Rebase Conflicts  
- Can happen multiple times (once per conflicting commit)
- Show changes from current commit being applied
- Rewrite history cleanly

## Conflict Markers in Rebase

```
<<<<<<< HEAD (target branch - where you're rebasing TO)
Content from the target branch
=======
Content from your commit (being rebased)
>>>>>>> commit-hash (your commit being applied)
```

## Step-by-Step Conflict Resolution

### 1. Rebase Starts
```bash
git checkout my-feature
git rebase main
```

### 2. Conflict Occurs
```
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
error: could not apply abc123f... Add new feature
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
```

### 3. Check Status
```bash
git status
```
Shows:
- Files with conflicts
- Current rebase progress
- Next steps

### 4. Resolve Conflicts
Open conflicted files and fix them:
```bash
# Edit the files to resolve conflicts
# Remove conflict markers
# Keep the changes you want
```

### 5. Stage Resolved Files
```bash
git add resolved-file.txt
```

### 6. Continue Rebase
```bash
git rebase --continue
```

### 7. Repeat if More Conflicts
If there are more commits that conflict, repeat steps 4-6.

## Rebase Conflict Commands

### Check Rebase Status
```bash
git status
git rebase --show-current-patch
```

### Skip a Commit (if it's no longer needed)
```bash
git rebase --skip
```

### Abort and Start Over
```bash
git rebase --abort
```

### Continue After Resolving
```bash
git add .
git rebase --continue
```

## Practice Exercise: Intentional Conflict

### Setup
1. Create a file `config.txt` with:
   ```
   server_port=8080
   debug_mode=false
   ```

2. Commit this to main branch

3. Create branch `feature-config`:
   ```bash
   git checkout -b feature-config
   ```

4. Change `config.txt` to:
   ```
   server_port=3000
   debug_mode=true
   database_url=localhost
   ```

5. Commit the change

6. Switch to main and change `config.txt` to:
   ```
   server_port=8080
   debug_mode=false
   cache_enabled=true
   ```

7. Commit this change

### Rebase and Resolve
1. Switch to `feature-config`: `git checkout feature-config`
2. Rebase: `git rebase main`
3. Resolve the conflict by keeping both `database_url` and `cache_enabled`
4. Choose appropriate `server_port` and `debug_mode` values
5. Continue the rebase

## Tips for Rebase Conflicts

### Before Rebasing
```bash
# Make sure working directory is clean
git status

# Create a backup branch just in case
git branch backup-feature-xyz
```

### During Conflicts
- **Take your time** - understand what each side changed
- **Test the resolution** - make sure it still works
- **Keep commits focused** - don't add extra changes during resolution

### Understanding "Ours" vs "Theirs" in Rebase
- **Ours** (HEAD): The target branch (where you're rebasing TO)
- **Theirs**: Your commit being applied

This is **opposite** of merge conflicts!

### Using Merge Tools
```bash
# configure a merge tool (VS Code example)
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'

# use during conflicts
git mergetool
```

## Complex Rebase Scenarios

### Multiple Conflicts
If you have many commits and each one conflicts:
- Consider `git rebase -i main` to squash commits first
- Or use `git merge` instead if rebase becomes too complex

### When to Give Up on Rebase
```bash
# If rebase becomes too complicated
git rebase --abort

# Use merge instead
git checkout main
git merge feature-branch
```

## Best Practices

1. **Rebase early and often** - smaller conflicts are easier
2. **Keep commits small** - fewer conflicts per commit
3. **Test after resolving** - make sure code still works
4. **Don't force complex rebases** - merge is sometimes better
5. **Use `--force-with-lease`** instead of `--force` when pushing

Remember: The goal is clean history, but not at the cost of spending hours resolving conflicts!
