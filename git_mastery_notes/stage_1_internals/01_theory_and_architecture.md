# Stage 1: Git Internals & Architecture

This document serves as the foundational theory for understanding Git as a DevOps engineer. Instead of memorizing commands, understanding these architectural concepts allows you to debug and rescue repositories when things go wrong.

## 1. What is Git? (The Snapshot Model)
Most beginners think Git stores changes (diffs) like a list of instructions: "Add line 1, delete line 2". 
**This is incorrect.** 
Git is a **snapshot-based filesystem**. Every time you commit, Git takes a picture of what all your files look like at that exact millisecond. If a file didn't change, Git doesn't copy it again; it just creates a link to the previous identical file to save space. 

## 2. The "Three Trees" Architecture
To understand how files move from your keyboard into the permanent Git history, you must understand the Three Trees.

1. **The Working Directory (Your Desk):**
   This is your computer's normal filesystem. When you open a file in VS Code and type, you are modifying the Working Directory. Git sees these changes but does not track them permanently yet.

2. **The Staging Area / Index (The Loading Dock):**
   This is a temporary holding zone. Before you can permanently save a snapshot, you must explicitly tell Git exactly which files should be included in the next save. You "stage" them.

3. **The Repository / HEAD (The Vault):**
   This is the permanent history (`.git` folder). When you commit, Git takes everything currently on the Staging Area, seals it into a snapshot, assigns it a unique 40-character SHA-1 Hash, and stores it in the Vault. 

## 3. The `HEAD` Pointer
`HEAD` is simply a **sticky note** that tells Git where you currently are in the timeline. 
Normally, `HEAD` points to the latest commit you made on your current branch. However, you can detach this sticky note and stick it on an older commit to "time travel" backward and view your code exactly as it looked in the past.

## 4. The Safety Net: `reflog`
When you use destructive commands (like `git reset --hard`) to delete commits, the commits are not actually deleted from your hard drive immediately. 
Git keeps a secret, chronological diary of every single time the `HEAD` pointer moved. This diary is called the **Reference Log (reflog)**. As long as you can find a commit's hash in the reflog, you can always recover "deleted" work.
