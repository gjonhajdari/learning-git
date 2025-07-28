# Git Workshop - Intermediate Beginner Level

A comprehensive 2-hour Git workshop designed for developers with basic Git knowledge who want to become productive team collaborators.

## Who This Workshop Is For

### Prerequisites
This workshop assumes you have:
- **Basic command line familiarity** - comfortable navigating directories and running commands
- **Some Git exposure** - you've heard of `git add`, `git commit`, and repositories
- **Development experience** - you write code and understand the need for version control
- **Text editor skills** - comfortable editing files (VS Code, Vim, etc.)

### What You Should Know Coming In
You should have at least **tried** Git before, even if you're not confident with it:
- Created a repository or cloned one
- Made a commit (even if you googled how to do it)
- Understand that Git tracks changes to files
- Know that branches exist (even if you haven't used them much)

### What You DON'T Need to Know
- Advanced Git commands (rebase, cherry-pick, etc.)
- How Git works internally
- Complex merge conflict resolution
- Professional Git workflows
- GitHub/GitLab advanced features

## Workshop Goals

By the end of this workshop, you will:
- **Confidently use** the core Git workflow for daily development
- **Understand both merge and rebase** and when to use each approach
- **Prefer rebase for cleaner history** while knowing when merge is appropriate
- **Resolve conflicts** in both merge and rebase scenarios
- **Collaborate with teammates** using modern Git workflows
- **Recover from common mistakes** that everyone makes
- **Follow professional practices** that create maintainable project history

## Workshop Structure

This workshop is designed to take 2 hours and assumes participants have some familiarity with basic Git commands but need to solidify fundamentals and learn team collaboration skills.

### Hour 1: Solidifying Fundamentals + Branching (60 minutes)
- **Quick Review & Gap Check** (10 minutes)
- **Branching Essentials** (20 minutes) - includes basic merge workflow
- **Understanding Merge Conflicts** (20 minutes) - hands-on conflict resolution
- **Rebase vs Merge: Modern Git Practices** (10 minutes) - comparison and when to use each

### Hour 2: Advanced Integration + Team Collaboration (60 minutes)
- **Handling Rebase Conflicts** (15 minutes) - rebase-specific conflict resolution
- **Working with Remotes** (20 minutes) - both merge and rebase workflows
- **Essential "Undo" Operations** (15 minutes)
- **Professional Git Practices** (10 minutes) - rebase-first approach

## Getting Started

### Pre-Workshop Setup
Before the workshop begins, ensure you have:
1. **Git installed** on your machine (`git --version` should work)
2. **A text editor or IDE** (VS Code recommended for conflict resolution)
3. **A GitHub account** (free - we'll use this for remote collaboration)
4. **A terminal/command prompt** you're comfortable using

### Quick Setup Verification
Run these commands to verify you're ready:
```bash
# verify git installation
git --version

# check if you have basic config (if not, we'll fix this in section 1)
git config --global user.name
git config --global user.email
```

If Git isn't installed or configured, don't worry - we'll cover this in the first section.

### Workshop Environment
- Work in a **dedicated folder** for practice (we'll create this together)
- Have your **terminal and text editor** ready
- **Ask questions** throughout - this is interactive!

## Workshop Sections

Each section builds upon the previous one. Work through them in order:

1. **[Introduction & Setup](01-intro/)** - Git installation and basic configuration
2. **[Basic Git Workflow](02-basic-workflow/)** - Core commands: add, commit, status, log
3. **[Branching Essentials](03-branching-essentials/)** - Creating, switching, and integrating branches (merge basics)
4. **[Understanding Merge Conflicts](04-merge-conflicts/)** - Resolving conflicts when branches clash
5. **[Rebase vs Merge](05-rebase-vs-merge/)** - Understanding both approaches, why rebase is often preferred
6. **[Handling Rebase Conflicts](06-rebase-conflicts/)** - Resolving conflicts during rebase operations
7. **[Working with Remotes](07-working-with-remotes/)** - GitHub collaboration with both merge and rebase workflows
8. **[Essential Recovery Techniques](08-essential-recovery/)** - Fixing common mistakes
9. **[Professional Git Practices](09-professional-practices/)** - Modern team workflows with rebase emphasis

## Learning Approach

This is a **hands-on workshop** - not a lecture! For each section:

1. **Read** the README file (5 minutes)
2. **Follow along** with live demonstrations
3. **Practice** the commands in your own repository
4. **Ask questions** immediately when confused


### If You Get Stuck
- **Don't panic** - everyone gets confused with Git sometimes
- **Ask for help** immediately - don't suffer in silence  
- **Check `git status`** - it's your best friend for understanding what's happening
- **Remember**: every expert was once a beginner who made these same mistakes

## Workshop Goals

By the end of this workshop, you will be able to:
- Use the essential Git workflow confidently
- Create and merge branches safely
- Resolve basic merge conflicts
- Collaborate with team members using remotes
- Recover from common Git mistakes
- Follow professional Git practices

## Additional Resources

### Git Cheat Sheet (Modern Git Practices)
```bash
# Daily workflow (rebase-first approach)
git status              # check repository status
git add <file>          # stage changes
git commit -m "..."     # commit changes
git push --force-with-lease  # upload rebased changes safely
git pull --rebase       # download changes with clean history

# Branching & Integration
git branch              # list branches
git checkout -b <name>  # create and switch to branch
git rebase main         # preferred: update branch with latest main
git merge main          # alternative: traditional merge approach
git rebase -i HEAD~3    # interactive rebase (squash, edit)

# Conflict Resolution (both types)
git rebase --continue   # continue after resolving rebase conflicts
git rebase --abort      # abort rebase and return to original state
# (merge conflicts work with standard git add + git commit)

# Recovery & Investigation
git reset HEAD <file>   # unstage file
git checkout -- <file> # discard changes
git stash              # temporarily save work
git reflog             # find "lost" commits
```

### Why This Approach?
- **Rebase for feature work** = clean, linear history
- **Merge for integration** = preserve feature context
- **Best of both worlds** = readable history + proper attribution


---

*This workshop is based on real-world Git usage patterns and focuses on practical skills you'll use daily as a developer.*
