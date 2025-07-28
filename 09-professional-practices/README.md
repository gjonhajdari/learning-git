# 09 - Professional Git Practices

Learn the habits and practices that will make you a better team player, with emphasis on rebase-first workflows.

## Writing Professional Commit Messages

### Conventional Commit Format
```
<type>: <description>

[optional body]

[optional footer]
```

### Common Types
- `feat:` - new feature
- `fix:` - bug fix
- `docs:` - documentation changes
- `style:` - formatting, missing semicolons, etc.
- `refactor:` - code change that neither fixes a bug nor adds a feature
- `test:` - adding missing tests
- `chore:` - updating grunt tasks, build tools, etc.

### Good Examples
```
feat: add user authentication system

fix: resolve navbar alignment on mobile devices

docs: update API documentation for user endpoints

refactor: extract email validation into utility function
```

### Bad Examples
```
fixed stuff
updates
asdf
final version
```

More details on [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

## Understanding .gitignore

Prevent certain files from being tracked by Git:

```bash
# create .gitignore file
touch .gitignore
```

### Common Patterns
```gitignore
# OS generated files
.DS_Store
Thumbs.db

# IDE files
.vscode/
.idea/
*.swp
*.swo

# Language specific
node_modules/
*.pyc
__pycache__/
target/
*.class

# Environment files
.env
.env.local

# Build outputs
dist/
build/
*.log
```

### Global gitignore
```bash
# set up global gitignore for your machine
git config --global core.excludesfile ~/.gitignore_global
```

## Branch Management

### Keeping Branches Clean
```bash
# delete merged branch
git branch -d feature-branch

# force delete unmerged branch (be careful!)
git branch -D feature-branch

# delete remote branch
git push origin --delete feature-branch
```

### Staying Up to Date with Rebase
```bash
# before starting new work
git checkout main
git pull --rebase origin main
git checkout -b new-feature

# regularly sync your branch (recommended daily)
git checkout main
git pull --rebase origin main
git checkout new-feature
git rebase main
```

## Code Review Preparation

### Before Creating Pull Request
1. **Self-review your changes**
   ```bash
   git diff main...your-branch
   ```

2. **Clean up commit history** (if needed)
   ```bash
   # squash multiple commits into one
   git rebase -i HEAD~3
   ```

3. **Test your changes**
   - Run tests
   - Check that code still compiles
   - Test the feature manually

4. **Update documentation**
   - README files
   - Code comments
   - API documentation

## Team Workflow Best Practices

### Daily Rebase Workflow
1. Start each day with `git pull --rebase`
2. Create feature branches for all work
3. Rebase feature branches against main regularly
4. Commit frequently with clear messages
5. Use `git push --force-with-lease` for rebased branches
6. Create pull requests for code review

### When to Use Rebase vs Merge
- **Rebase**: Feature branches, personal work, updating branches
- **Merge**: Integrating completed features, shared branches
- **Rule of thumb**: Rebase before sharing, merge when integrating

### Communication
- Reference issue numbers in commits: `fix: resolve login bug (#123)`
- Use descriptive branch names: `feature/user-profile-page`
- Write clear pull request descriptions
- Respond promptly to code review feedback

## Working with Large Teams

### When to Rebase vs Merge
- **Rebase**: Clean up personal branches before merging
- **Merge**: Preserve history for important milestones

### Handling Conflicts in Team Settings
1. Communicate before working on same files
2. Pull frequently to minimize conflicts
3. Resolve conflicts quickly when they occur
4. Ask for help if conflicts are complex

## Practice Exercise

1. Set up a proper `.gitignore` file for your project type
2. Practice writing conventional commit messages
3. Create a feature branch with 2-3 commits
4. Clean up the commit history before "submitting for review"
5. Delete the feature branch after merging

## Tools and Integrations

### Git Hooks (Advanced)
- Pre-commit hooks for code formatting
- Pre-push hooks for running tests
- Commit message hooks for enforcing standards

### Popular Git clients
- **GitKraken** - visual Git client
- **SourceTree** - free Git client
- **VS Code** - built-in Git integration
- **GitHub Desktop** - simple GitHub integration
- **lazygit** - terminal-based Git client (the GOAT)
