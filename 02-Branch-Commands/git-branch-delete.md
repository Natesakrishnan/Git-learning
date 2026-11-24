# git branch -d (Delete a Branch)

## 1. Command Name
`git branch -d branch_name`

## 2. Purpose
`git branch -d` deletes a **local** branch you no longer need — typically after its work has already been merged into another branch (like `master`). This keeps your list of branches clean and avoids clutter from old, finished feature branches.

## 3. Syntax

```text
git branch -d branch_name
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git branch` | The branch-management sub-command. |
| `-d` | Flag meaning "delete" (a **safe** delete). |
| `branch_name` | The name of the local branch you want to remove. |

The `-d` flag performs a **safe delete**: Git will refuse to delete the branch if it contains commits that have not been merged anywhere else, to protect you from losing work. (A force-delete using `-D` exists for advanced cases, but is not covered here since it is considered an advanced/destructive topic.)

## 5. Example

```text
git branch -d feature-signup
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Make sure you are **not** currently on the branch you want to delete — switch to `master` first:
   ```text
   git switch master
   ```
3. Confirm the feature branch has already been merged into `master` (see [`git merge`](../03-Merge-Commands/git-merge.md)).
4. Delete the branch:
   ```text
   git branch -d feature-signup
   ```
5. Confirm it is gone:
   ```text
   git branch
   ```

## 7. Expected Output

```text
K:\GitPractice> git branch -d feature-signup
Deleted branch feature-signup (was 9f8e7d6).
```

If the branch has **not** been merged yet, Git protects you with a warning instead:

```text
error: The branch 'feature-signup' is not fully merged.
If you are sure you want to delete it, run 'git branch -D feature-signup'.
```

## 8. Real-Time Use Case

Developers delete branches to:
- Clean up after a feature branch has been successfully merged into `master` and is no longer needed.
- Keep `git branch` output short and easy to read on projects with many contributors creating many short-lived branches.
- Avoid confusion about which branches still represent active, unfinished work.

## 9. Important Notes

- **You cannot delete the branch you are currently on.** Switch to a different branch first (commonly `master`).
- `-d` (lowercase) is the **safe** option — it refuses to delete a branch with unmerged work. Treat any warning from Git as a signal to double-check before considering a force delete.
- Deleting a local branch with `-d` does **not** delete the matching branch on GitHub — that requires `git push origin --delete branch_name` (covered in the GitHub Remote Commands section).
- Think of branch deletion as similar to deleting a file: once truly removed (and not referenced anywhere), old commits on it can become very hard to recover — always confirm the work is merged first.

## 10. Related Commands

- [`git branch branch_name`](git-branch.md) – create branches.
- [`git switch branch_name`](git-switch.md) – move off a branch before deleting it.
- [`git merge branch_name`](../03-Merge-Commands/git-merge.md) – merge a branch's work before deleting it.
- [`git push origin --delete branch_name`](../04-GitHub-Remote-Commands/git-push.md) – delete the matching remote branch on GitHub.
