---
description: Workflow to delete existing git history and force push the current state as a new initial commit.
---

This workflow will reset your git history, making your current local state the "first" commit on your GitHub repository.

> [!WARNING]
> This will permanently delete the history of all previous commits. This action is destructive and cannot be easily undone.

1.  **Remove existing git history**:
    Delete the hidden `.git` folder to remove all version control history.
    ```powershell
    Remove-Item -Path .git -Recurse -Force
    ```

2.  **Initialize new repository**:
    Start a fresh git repository.
    ```powershell
    git init
    ```

3.  **Add all files**:
    Stage all your current files for the new initial commit.
    ```powershell
    git add .
    ```

4.  **Create initial commit**:
    Commit the files.
    ```powershell
    git commit -m "Initial commit"
    ```

5.  **Set the remote origin**:
    Re-link your local repo to your GitHub repository.
    ```powershell
    git remote add origin https://github.com/joselops/joselops.github.io.git
    ```

6.  **Force push to GitHub**:
    Overwrite the history on GitHub with your new initial commit.
    ```powershell
    git push -u --force origin master
    ```
    *(Note: If your main branch is named `main` instead of `master`, use `main` in the command above.)*
