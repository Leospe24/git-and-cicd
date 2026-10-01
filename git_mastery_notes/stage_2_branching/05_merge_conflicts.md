# Break & Fix: Merge Conflicts

## 1. What is a Merge Conflict?
A merge conflict happens when Git cannot automatically merge two branches because the **exact same line** in the same file was modified differently in both branches (or one person modified it and another deleted it). 

Instead of guessing which version is correct and potentially breaking your code, Git safely pauses the merge, modifies the file to show you both versions, and asks you (the human) to make the final decision.

## 2. Anatomy of a Conflict
When a conflict occurs, Git injects raw text symbols into your file to separate the competing changes:

```text
<<<<<<< HEAD
(Your changes on the current branch - e.g., main)
=======
(Their changes on the incoming branch)
>>>>>>> feature-branch-name
```

## 3. How to Resolve a Conflict
Fixing a conflict does not require complex Git commands. It is a standard text-editing process:

1. **Edit:** Open the file in your code editor.
2. **Clean:** Delete the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
3. **Decide:** Edit the code so it looks *exactly* how the final version should look (you can keep yours, keep theirs, or combine them).
4. **Save:** Save the file.
5. **Stage:** Tell Git you resolved it by moving the file to the Staging Area: 
   `git add <file_name>`
6. **Commit:** Finalize the merge and seal it in the Vault: 
   `git commit -m "Resolved merge conflict"`
