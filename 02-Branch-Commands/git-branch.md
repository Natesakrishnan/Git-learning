# git branch

## 1. Command Name
`git branch`, `git branch -a`, `git branch -r`, and `git branch branch_name`

## 2. Purpose
`git branch` is used to **list, create, or inspect branches**. A branch is an independent line of development — it lets you work on new features or fixes without touching the stable code on your main branch (`master`). This command has several variations for listing local branches, remote branches, or all branches, and for creating a new branch.

## 3. Syntax

```text
git branch
git branch -a
git branch -r
git branch branch_name
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git branch` | Lists all **local** branches in your repository. The branch you are currently on is marked with a `*`. |
| `git branch -a` | Lists **all** branches — both local branches and remote-tracking branches (e.g. `remotes/origin/master`). |
| `git branch -r` | Lists only **remote-tracking** branches (branches that exist on GitHub, as far as your local copy knows). |
| `git branch branch_name` | **Creates** a new local branch called `branch_name`, copied from your current branch — but does **not** switch to it. |

## 5. Example

```text
git branch
git branch -a
git branch -r
git branch feature-login
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. List your current local branches:
   ```text
   git branch
   ```
3. Create a new branch for a feature:
   ```text
   git branch feature-login
   ```
4. Confirm it was created (note: you are still on your original branch):
   ```text
   git branch
   ```
5. If you have a GitHub remote connected, view remote-tracking branches:
   ```text
   git branch -r
   ```
6. View everything together:
   ```text
   git branch -a
   ```

## 7. Expected Output

```text
K:\GitPractice> git branch
* master

K:\GitPractice> git branch feature-login
K:\GitPractice> git branch
* master
  feature-login

K:\GitPractice> git branch -a
* master
  feature-login
  remotes/origin/master
```

## 8. Real-Time Use Case

Developers use `git branch` to:
- Create a dedicated branch for every new feature or bug fix (e.g. `feature-login`, `bugfix-navbar`), keeping `master` always stable.
- Check which branch they are currently on before making changes (the `*` marker).
- See what branches exist on the remote GitHub repository with `-r` or `-a`, especially when collaborating with a team.

## 9. Important Notes

- `git branch branch_name` only **creates** the branch — it does not move you onto it. To create and switch in one step, use `git switch -c branch_name` instead.
- Remote-tracking branches shown with `-r` are read-only local bookmarks of what exists on GitHub — they update only when you `git fetch` or `git pull`.
- Branch names should avoid spaces and special characters; use hyphens instead, e.g. `feature-login` rather than `feature login`.
- This repository documentation uses `master` as the main branch name, matching the examples in this project (some newer repositories use `main` instead).

## 10. Related Commands

- [`git switch branch_name` / `git switch -c branch_name`](git-switch.md) – move to an existing or new branch.
- [`git branch -d branch_name`](git-branch-delete.md) – delete a branch you no longer need.
- [`git merge branch_name`](../03-Merge-Commands/git-merge.md) – combine a branch's changes into your current branch.
