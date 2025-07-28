# 07 - Working with Remotes

Remote repositories allow you to collaborate with others and backup your work. We'll also cover the rebase workflow for clean collaboration.

## What are Remotes?

- Remote repositories are versions of your project hosted elsewhere (GitHub, GitLab, etc.)
- `origin` is the default name for your main remote repository
- You can have multiple remotes for different purposes

## Cloning Existing Projects

```bash
# clone a repository
git clone https://github.com/username/repo-name.git

# clone into a specific directory
git clone https://github.com/username/repo-name.git my-project

# clone into the current directory
git clone https://github.com/username/repo-name.git .
```

## Basic Remote Commands

### Checking Remote Information
```bash
# list remotes
git remote

# list remotes with URLs
git remote -v

# show detailed remote info
git remote show origin
```

### Adding Remotes
```bash
# add a new remote
git remote add origin https://github.com/username/repo.git

# add upstream remote (for forks)
git remote add upstream https://github.com/original/repo.git
```

## Push and Pull Workflow

### Pushing Changes
```bash
# push to origin remote, main branch
git push origin main

# set upstream tracking (first time)
git push -u origin main

# push current branch (after tracking is set)
git push
```

### Pulling Changes with Rebase
```bash
# get latest changes with rebase (cleaner history)
git pull --rebase origin main

# pull current branch with rebase (after tracking is set)
git pull --rebase
```

### Understanding Fetch vs Pull vs Pull --rebase
```bash
# fetch downloads changes but doesn't merge
git fetch origin

# pull does fetch + merge (creates merge commits)
git pull origin main

# pull --rebase does fetch + rebase (cleaner history)
git pull --rebase origin main
```

## Rebase Workflow with Remotes

### Daily Team Workflow
```bash
# Start of day - get latest changes
git checkout main
git pull --rebase origin main

# Update your feature branch
git checkout my-feature
git rebase main

# Continue working and push when ready
git push --force-with-lease origin my-feature
```

## Practice Exercise

1. Create a repository on GitHub
2. Connect your local repository to GitHub:
   ```bash
   git remote add origin https://github.com/yourusername/your-repo.git
   ```
3. Push your changes:
   ```bash
   git push -u origin main
   ```
4. Make a change on GitHub (edit a file directly)
5. Pull the changes locally:
   ```bash
   git pull
   ```

## Common Remote Workflows

### Contributing to Your Own Project
1. Make changes locally
2. Commit changes
3. Push to your repository

### Working with Team Repository
1. Pull latest changes
2. Create feature branch
3. Make changes and commit
4. Push feature branch
5. Create pull request

## Troubleshooting

### Authentication Issues
- Use personal access tokens instead of passwords
- Set up SSH keys for easier authentication

### Push Rejected
If push is rejected, usually means remote has newer commits:
```bash
git pull
# resolve any conflicts
git push
```
