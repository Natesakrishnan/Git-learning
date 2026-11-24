# git push

## 1. Command Name
`git push origin master`, `git push -u origin branch_name`, and `git push origin --delete branch_name`

## 2. Purpose
`git push` uploads your local commits to a remote repository (GitHub), making them available to others and backing them up online. The `-u` flag additionally remembers the pairing between your local branch and the remote branch, so future pushes from that branch can be done with just `git push`. `git push origin --delete branch_name` removes a branch from the **remote** repository (GitHub), separate from deleting it locally.

## 3. Syntax

```text
git push origin master
git push -u origin branch_name
git push origin --delete branch_name
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git push` | The sub-command that uploads commits to a remote. |
| `origin` | The name of the remote you are pushing to (set up with `git remote add origin URL`). |
| `master` / `branch_name` | The name of the local branch whose commits you want to upload. |
| `-u` | Short for `--set-upstream`. Links your local branch to the matching remote branch so that later you can simply type `git push` with no extra arguments. |
| `--delete branch_name` | Tells Git to delete `branch_name` **on the remote** (GitHub), not on your own computer. |

## 5. Example

Push your main branch for the first time:
```text
git push -u origin master
```

Push again later (once the upstream link exists):
```text
git push
```

Delete a branch from GitHub:
```text
git push origin --delete feature-signup
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Make sure you have committed your work and connected a remote (see [`git remote`](git-remote.md)):
   ```text
   cd K:\GitPractice
   git remote -v
   ```
2. Push your `master` branch to GitHub for the first time, setting the upstream link:
   ```text
   git push -u origin master
   ```
3. Enter your GitHub credentials if prompted (Command Prompt may open a browser sign-in window, or ask for a username and a personal access token).
4. For future pushes from `master`, you only need:
   ```text
   git push
   ```
5. To remove a branch from GitHub once it is no longer needed there:
   ```text
   git push origin --delete feature-signup
   ```

## 7. Expected Output

```text
K:\GitPractice> git push -u origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Writing objects: 100% (4/4), 310 bytes | 310.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Natesakrishnan/Git-learning.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

## 8. Real-Time Use Case

Developers push to:
- Share their local commits with teammates by uploading them to the shared GitHub repository.
- Back up their work online, so it is safe even if their own computer has a problem.
- Trigger automated processes many teams set up on GitHub, such as tests or deployments that run whenever new commits are pushed.
- Delete old, already-merged feature branches from GitHub to keep the remote repository tidy.

## 9. Important Notes

- **`git push` can fail** if the remote has commits you do not yet have locally (for example, a teammate pushed first). In that case, Git will ask you to `git pull` first before pushing again — never force-push over others' work unless you fully understand the consequences.
- The `-u` flag only needs to be used **once** per branch; after that, plain `git push` remembers where to send commits.
- Deleting a branch with `--delete` only affects GitHub — your local branch (if it still exists) is untouched. Use `git branch -d branch_name` separately to remove it locally too.
- Always double-check which branch you are pushing, especially in a shared project, to avoid accidentally pushing unfinished or experimental work to `master`.

## 10. Related Commands

- [`git remote -v` / `git remote add origin URL`](git-remote.md) – connect to GitHub before pushing.
- [`git pull`](git-pull.md) – download others' changes, often needed before a push succeeds.
- [`git branch -d branch_name`](../02-Branch-Commands/git-branch-delete.md) – delete the matching local branch.
- [`push-project-to-github.md`](../06-GitHub-Workflow/push-project-to-github.md) – complete first-time push walkthrough.
