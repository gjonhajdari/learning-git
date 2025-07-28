# Advanced Git Topics (For Future Learning)

*These topics are beyond the 2-hour workshop scope but are valuable for continued Git mastery.*

## Topics Covered in Advanced Workshops

### Advanced History Management
- **Interactive Rebase** (`git rebase -i`)
  - Squashing commits
  - Reordering commits
  - Editing commit messages
  - Splitting commits

- **Cherry Picking** (`git cherry-pick`)
  - Selecting specific commits
  - Applying changes across branches
  - Handling cherry-pick conflicts

### Advanced Recovery & Investigation
- **Git Reflog** (`git reflog`)
  - Recovering "lost" commits
  - Understanding HEAD movement
  - Emergency recovery techniques

- **Git Bisect** (`git bisect`)
  - Binary search for bugs
  - Automated bisect with scripts
  - Finding when issues were introduced

### Advanced Git Features
- **Git Worktrees** (`git worktree`)
  - Multiple working directories
  - Working on multiple branches simultaneously
  - Managing linked worktrees

- **Git Hooks**
  - Pre-commit hooks
  - Pre-push hooks
  - Server-side hooks
  - Automated workflows

- **Git Tags** (`git tag`)
  - Semantic versioning
  - Release management
  - Lightweight vs annotated tags

### Advanced Conflict Resolution
- **Rerere** (Reuse Recorded Resolution)
  - Automating conflict resolution
  - Training Git to remember solutions
  - Reducing repetitive conflict work

- **Merge Strategies**
  - Ours vs theirs
  - Custom merge drivers
  - Three-way merge understanding

### Performance & Maintenance
- **Git Internals**
  - Objects, trees, and blobs
  - Understanding the .git directory
  - How Git stores data

- **Repository Maintenance**
  - Garbage collection
  - Repository optimization
  - Large file handling (Git LFS)

## When to Learn These Topics

### After 3-6 Months of Regular Git Use:
- Interactive rebase
- Cherry picking
- Advanced remote operations

### After 6-12 Months:
- Git reflog and recovery
- Bisect for debugging
- Git hooks for automation

### For Team Leads/Maintainers:
- Advanced merge strategies
- Repository maintenance

## Learning Resources

Most of these topics were taken from [Learn Git - The Full Course](https://youtu.be/rH3zE7VlIMs?si=-sutSv-lgZFbU-Xy) on YouTube, which covers advanced Git topics in detail.

---

*Remember: Master the basics first! These advanced topics build on the foundation covered in the main workshop.*
