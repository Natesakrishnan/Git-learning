# git pull

## 1. Command Name
`git pull`

## 2. Purpose
`git pull` downloads the latest commits from a remote repository (GitHub) **and immediately merges them** into your current local branch, in one combined step. It is how you keep your local copy of a project up to date with changes made by others, or changes you made from a different computer.

## 3. Syntax

```text
git pull
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Runs a Git command. |
| `pull` | The sub-command that downloads and merges remote changes. |

Behind the scenes, `git pull` is really two steps combined:
1. `git fetch` – download the latest commits from the remote (without touching your working files).
2. `git merge` – merge those freshly downloaded commits into your current branch.

Because a merge is involved, `git pull` can occasionally produce a **merge conflict** if you and the remote changed the same lines of the same file — exactly as described in the [`git merge`](../03-Merge-Commands/git-merge.md) documentation.

## 5. Example

```text
git pull
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Make sure your own work is committed or safely saved first:
   ```text
   git status
   ```
3. Download and merge the latest changes from GitHub:
   ```text
   git pull
   ```
4. If a conflict appears, resolve it the same way described in the [`git merge`](../03-Merge-Commands/git-merge.md) documentation, then commit the result.

## 7. Expected Output

When there are new changes to merge:

```text
K:\GitPractice> git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
Unpacking objects: 100% (3/3), 320 bytes | 10.00 KiB/s, done.
From https://github.com/Natesakrishnan/Git-learning
   a1b2c3d..9f8e7d6  master     -> origin/master
Updating a1b2c3d..9f8e7d6
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)
```

When you are already up to date:

```text
K:\GitPractice> git pull
Already up to date.
```

## 8. Real-Time Use Case

Developers run `git pull` to:
- Start each work session by syncing with the latest changes teammates have pushed to GitHub.
- Update their local `master` branch before creating a new feature branch, so the new branch starts from the latest code.
- Refresh their copy of a project after someone else merges a pull request.

## 9. Important Notes

- Always try to `git pull` **before** you start making changes and before you `git push`, to reduce the chance of conflicts.
- If you have uncommitted changes that would be overwritten, Git will stop and ask you to commit or stash them first — this is a safety feature, not an error to be afraid of.
- Since `git pull` automatically merges, it can create a merge conflict exactly like `git merge` can. Read the file(s) Git mentions, fix the conflict markers, then `git add` and `git commit`.
- `git pull` only pulls into your **current** branch from its matching remote branch — make sure you are on the correct branch first with `git branch`.

## 10. Related Commands

- [`git fetch`](git-fetch.md) – download changes without merging, the safer "look before you leap" alternative.
- [`git merge branch_name`](../03-Merge-Commands/git-merge.md) – understand the merge step that `git pull` performs automatically.
- [`git push origin master`](git-push.md) – upload your own changes after pulling and resolving any conflicts.
- [`branch-collaboration.md`](../06-GitHub-Workflow/branch-collaboration.md) – see pulling in the context of team collaboration.
