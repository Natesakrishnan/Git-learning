# git switch

## 1. Command Name
`git switch branch_name` and `git switch -c branch_name`

## 2. Purpose
`git switch` moves you from one branch to another, updating the files in your working folder to match that branch. The `-c` flag (short for "create") lets you **create a brand-new branch and move onto it** in a single command, instead of using `git branch` and `git switch` separately.

## 3. Syntax

```text
git switch branch_name
git switch -c branch_name
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git switch` | The sub-command for changing your current branch. |
| `branch_name` | The name of an **existing** branch to move onto. |
| `-c` | Flag meaning "create". Combined with a name, it creates the branch first, then switches to it immediately. |

When you switch branches, Git updates your working folder's files to match the last commit on that branch. This is why it is important to commit or stash your current changes first — switching branches with unsaved changes that conflict can be blocked by Git for your own safety.

## 5. Example

Switch to an existing branch:
```text
git switch feature-login
```

Create a new branch and switch to it immediately:
```text
git switch -c feature-signup
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Confirm your current branch:
   ```text
   git branch
   ```
3. Create and switch to a new branch in one step:
   ```text
   git switch -c feature-signup
   ```
4. Confirm you have moved:
   ```text
   git branch
   ```
5. Switch back to `master`:
   ```text
   git switch master
   ```

## 7. Expected Output

```text
K:\GitPractice> git switch -c feature-signup
Switched to a new branch 'feature-signup'

K:\GitPractice> git branch
  master
* feature-signup

K:\GitPractice> git switch master
Switched to branch 'master'
```

## 8. Real-Time Use Case

Developers use `git switch` to:
- Jump between an in-progress feature branch and `master` to fix an urgent bug, then return to their feature work.
- Start new work immediately with `git switch -c`, which is faster than running `git branch` and then switching separately.
- Review a teammate's branch locally after fetching it, by switching onto it to inspect the code.

## 9. Important Notes

- If you have uncommitted changes that would be overwritten by switching, Git will refuse and show an error — commit, stash, or discard those changes first.
- `git switch branch_name` only works if `branch_name` **already exists**. To create a new one at the same time, you must use `-c`.
- `git switch` is the modern, beginner-friendly replacement for the older `git checkout branch_name` command, and is recommended because it is more focused and less confusing.
- Always run `git status` after switching to confirm you are in a clean state before continuing work.

## 10. Related Commands

- [`git branch branch_name`](git-branch.md) – create a branch without switching to it.
- [`git branch -d branch_name`](git-branch-delete.md) – delete a branch once you are done with it.
- [`git merge branch_name`](../03-Merge-Commands/git-merge.md) – merge the branch you switched away from back into another branch.
