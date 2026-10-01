# Stage 2: Branching CLI Commands

## 1. Creating & Navigating Branches
```bash
# List all local branches (the one with the * is your current branch)
git branch

# Create a new branch (but stay on the current one)
git branch <branch_name>

# Switch to a different branch
git checkout <branch_name>
# (Modern alternative): git switch <branch_name>

# Create a new branch AND switch to it in one command
git checkout -b <branch_name>
# (Modern alternative): git switch -c <branch_name>
```

## 2. Merging Branches
```bash
# Step 1: ALWAYS switch to the branch that is RECEIVING the code (usually main)
git checkout main

# Step 2: Merge the feature branch INTO your current branch
git merge <branch_name>
```

## 3. Housekeeping
```bash
# Delete a branch after it has been successfully merged
git branch -d <branch_name>

# FORCE delete a branch (if you want to throw away the experiment)
git branch -D <branch_name>
```
