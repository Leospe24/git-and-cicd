# Stage 2: Branching & Merging (Team DevOps)

## 1. What is a Branch?
A branch is NOT a copy of your files. A branch is simply a lightweight, movable pointer (a sticky note) that sits on a specific commit. 
When you create a branch, Git creates a new sticky note. When you switch branches, Git physically updates your Working Directory to match the exact snapshot that the sticky note is pointing to.

## 2. Why do we Branch?
In a team environment, `main` represents production. You never experiment on `main`. Branches give you an isolated sandbox to build features or fix bugs without affecting the stable codebase. 

## 3. What is Merging?
Merging is the act of combining the history of two branches. 
When you are on `main` and you merge a feature branch, Git looks at the changes made in the feature branch and applies them to `main`.

## 4. The "Fast-Forward" Merge
If `main` has not changed at all since you created your feature branch, Git doesn't need to do any complex math to combine them. It simply slides the `main` sticky note forward to catch up with the feature branch. This is called a "Fast-forward" merge, and it results in both branches pointing to the exact same commit ID.
