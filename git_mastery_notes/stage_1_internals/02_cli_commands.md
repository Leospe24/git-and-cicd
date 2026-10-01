# Stage 1: The Essential Git CLI

This is a quick-reference guide for the commands used to manipulate the Three Trees and navigate the Git timeline.

## 1. Repository Setup
```bash
# Initialize a brand new, empty Git repository in the current folder.
# This creates the hidden `.git` folder (The Vault).
git init

# Modern Best Practice: Rename the default branch from 'master' to 'main'
git branch -m main
```

## 2. Moving Through The Three Trees
```bash
# 1. Check the status of the Three Trees
# (Shows what is on your Desk vs. what is on the Loading Dock)
git status

# 2. See the exact lines of code you changed BEFORE staging them
# (Compares Working Directory to Staging Area)
git diff

# 3. See the exact lines of code you changed AFTER staging them, but before committing
# (Compares Staging Area to HEAD)
git diff --staged

# 4. Move a file from the Working Directory (Desk) to the Staging Area (Loading Dock)
git add <file_name>
git add .          # Adds EVERYTHING in the current directory

# 3. Move files from the Staging Area into the permanent Repository (The Vault)
git commit -m "A descriptive message of what you changed"
```

## 3. Viewing History
```bash
# View the full commit history (Author, Date, full 40-char Hash)
git log

# View a clean, condensed history (7-char Short Hash and Message only)
git log --oneline

# View the history alongside the actual code changes (diffs) made in each commit
git log -p
```

## 4. Time Travel (Break & Fix)
```bash
# THE DANGEROUS UNDO BUTTON: 
# Erase all commits after <commit_hash> and force the Working Directory to look exactly like that moment in time.
# WARNING: Do not use this on branches shared with other developers.
git reset --hard <commit_hash>

# THE ULTIMATE RESCUE TOOL:
# View the secret diary of everywhere the HEAD pointer has ever been.
# Use this to find the hash of a "deleted" commit so you can reset back to it.
git reflog
```
