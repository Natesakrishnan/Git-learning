# git fetch

## 1. Command Name
`git fetch`

## 2. Purpose
`git fetch` downloads the latest commits, branches, and history from a remote repository (GitHub) — but, unlike `git pull`, it does **not** merge anything into your current branch or touch your working files. It simply updates your local "remote-tracking branches" (like `origin/master`) so you can look at what changed before deciding what to do next.

## 3. Syntax

```text
git fetch
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Runs a Git command. |
| `fetch` | The sub-command that downloads new data from the remote without merging it. |

After running `git fetch`, your own branch (e.g. `master`) stays exactly as it was. Only the remote-tracking branch (e.g. `origin/master`) is updated to reflect what is currently on GitHub. You can then inspect the new commits (for example with `git log origin/master`) before deciding to merge them in.

## 5. Example

```text
git fetch
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Download the latest information from GitHub without changing your files:
   ```text
   git fetch
   ```
3. See what changed on the remote compared to your local branch:
   ```text
   git log master..origin/master --oneline
   ```
4. If you are happy with what you see, bring it into your branch:
   ```text
   git merge origin/master
   ```

## 7. Expected Output

```text
K:\GitPractice> git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
Unpacking objects: 100% (3/3), 320 bytes | 10.00 KiB/s, done.
From https://github.com/Natesakrishnan/Git-learning
   a1b2c3d..9f8e7d6  master     -> origin/master
```

Notice that, unlike `git pull`, there is no "Fast-forward" or "Updating" message — your own `master` branch has not moved yet.

## 8. Real-Time Use Case

Developers use `git fetch` to:
- Safely check what teammates have pushed to GitHub **before** merging it into their own work, especially on sensitive or shared branches.
- Review incoming changes with `git log` or `git diff` first, rather than merging blindly.
- Keep remote-tracking information up to date for tools and IDEs that show how far ahead/behind a branch is, without changing any files.

## 9. Important Notes

### Difference between `git fetch`, `git pull`, and `git push`

| Command | Direction | What it does |
|---|---|---|
| `git fetch` | **Download only** | Downloads new commits from the remote but does **not** merge them into your branch. Safe to run at any time. |
| `git pull` | **Download + merge** | Downloads new commits **and** immediately merges them into your current branch (`fetch` + `merge` combined). Can create a conflict. |
| `git push` | **Upload** | Sends your own local commits **up to** the remote repository, making them available to others. |

A simple way to remember it: `fetch` **looks**, `pull` **looks and merges**, `push` **sends**.

- `git fetch` never changes your working files, so it is always safe to run, even if you have uncommitted changes.
- Running `git fetch` regularly (without merging) is a good habit for staying aware of remote activity before you are ready to integrate it.

## 10. Related Commands

- [`git pull`](git-pull.md) – the combined fetch-and-merge command.
- [`git push origin master`](git-push.md) – the opposite direction: uploading your commits.
- [`git merge branch_name`](../03-Merge-Commands/git-merge.md) – manually merge fetched changes when you are ready.
- [`git log` / `git log --oneline`](../01-Basic-Git-Commands/git-log.md) – inspect fetched commits before merging.
