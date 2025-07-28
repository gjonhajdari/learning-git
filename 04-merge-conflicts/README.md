# 04 - Understanding Merge Conflicts

Merge conflicts are a normal part of collaborative development. Here's how to understand and resolve them confidently.

## When Do Conflicts Occur?

- Two branches modify the same line in a file
- One branch deletes a file while another modifies it
- Two branches add files with the same name

## Anatomy of a Conflict

When a conflict occurs, Git marks the conflicted areas in your file:

```
<<<<<<< HEAD
Your current branch changes
=======
Changes from the other branch
>>>>>>> branch-name
```

## Conflict Markers Explained

- `<<<<<<< HEAD` - Start of your current branch's changes
- `=======` - Separator between the two versions
- `>>>>>>> branch-name` - End of the other branch's changes

## Resolving Conflicts

### Step 1: Identify Conflicted Files
```bash
git status
```

### Step 2: Open and Edit Conflicted Files
1. Look for conflict markers
2. Decide which changes to keep
3. Remove conflict markers
4. Save the file

### Step 3: Stage and Commit Resolution
```bash
# add resolved files
git add conflicted-file.txt

# commit the merge
git commit -m "Resolve merge conflict in conflicted-file.txt"
```

## Using VS Code for Conflicts

VS Code provides helpful buttons when you open a conflicted file:
- **Accept Current Change** - keep your version
- **Accept Incoming Change** - keep the other branch's version
- **Accept Both Changes** - keep both versions
- **Compare Changes** - see differences side by side

## Practice Exercise: Create Your First Conflict

Let's intentionally create a merge conflict to practice resolving it safely.

### Setup
1. Make sure you're in your practice repository
2. Ensure you're on the main branch: `git checkout main`
3. Create a file called `team.md`:
   ```bash
   echo "# Our Team

Lead Developer: Alice" > team.md
   git add team.md
   git commit -m "Add team file with Alice as lead"
   ```

### Create Conflicting Branches
1. Create first branch:
   ```bash
   git checkout -b update-team-bob
   echo "# Our Team

Lead Developer: Bob
Backend Developer: Alice" > team.md
   git add team.md
   git commit -m "Update team with Bob as lead"
   ```

2. Go back and create second branch:
   ```bash
   git checkout main
   git checkout -b update-team-carol
   echo "# Our Team

Lead Developer: Carol
Frontend Developer: Alice" > team.md
   git add team.md
   git commit -m "Update team with Carol as lead"
   ```

### Create the Conflict
1. Switch to main: `git checkout main`
2. Merge first branch: `git merge update-team-bob` (should work fine)
3. Try to merge second branch: `git merge update-team-carol` (conflict!)

### What You'll See
```
Auto-merging team.md
CONFLICT (content): Merge conflict in team.md
Automatic merge failed; fix conflicts and then commit the result.
```

## Tips for Avoiding Conflicts

- **Pull latest changes frequently** - `git pull` before starting work
- **Make smaller, focused commits** - easier to resolve conflicts
- **Communicate with team** about file changes
- **Use different files when possible** - parallel development
- **Coordinate on shared files** - talk before both editing same sections

## When Conflicts Are Actually Good

Conflicts aren't always bad - they often indicate:
- **Two people improving the same area** - collaboration happening!
- **Important decisions need to be made** - which approach is better?
- **Code review opportunity** - discuss the changes before merging

## Advanced Conflict Resolution

### Using Git Merge Tools
```bash
# Set up VS Code as merge tool
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'

# Use during conflicts
git mergetool
```

### Cherry-picking from Each Side
```bash
# Keep only the current branch version
git checkout --ours conflicted-file.txt

# Keep only the incoming branch version  
git checkout --theirs conflicted-file.txt
```

### Aborting a Merge
```bash
# If things get too complicated
git merge --abort
```

This returns you to the state before you started the merge.
