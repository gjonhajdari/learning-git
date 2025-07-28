# 01 - Introduction & Setup

In this section, we will cover the basics of Git, its installation, and initial setup.

## Setup

### Install Git

1. **Windows**: Download the Git installer from [git-scm.com](https://git-scm.com/download/win) and run it.

2. **macOS**: Comes pre-installed, but you can install a newer version using Homebrew with the command:

```bash
brew install git
```

3. **Linux**: Use your package manager to install Git. For example, on Ubuntu:

```bash
sudo apt-get install git
```

### Verify Installation

After installation, verify that Git is installed correctly by running:

```bash
git --version
```

### Configure Git

Some initial configuration is necessary to use Git effectively.

```bash
# name and email are required for commits
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# (optional) use rebase by default when pulling changes
git config --global pull.rebase true

# (optional) vs code as default editor for commit messages
git config --global core.editor "code --wait"

# for neovim or helix, use:
# git config --global core.editor "nvim"
# git config --global core.editor "hx"

# set default branch name to main
git config --global init.defaultBranch main
```

## Creating a new repository

To create a new Git repository, you can either initialize a new repository in an existing directory or create a new directory for your repository.

```bash
# create a new directory and initialize a git repository
mkdir my-repo
cd my-repo
git init

# alternatively create a repository & folder
git init my-repo
cd my-repo
```