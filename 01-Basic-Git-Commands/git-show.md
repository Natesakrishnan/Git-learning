# git show

## 1. Command Name
`git show`

## 2. Purpose
`git show` displays detailed information about a **single commit** — including who made it, when, the commit message, and the exact line-by-line changes (the "diff") introduced by that commit. It is useful when `git log` tells you a commit exists, and you want to see exactly what changed inside it.

## 3. Syntax

```text
git show
git show <commit-hash>
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Runs a Git command. |
| `show` | The sub-command that displays one commit's full details. |
| `<commit-hash>` | (Optional) The ID of the commit you want to inspect, copied from `git log`. If left out, `git show` displays the **most recent** commit (`HEAD`). |

## 5. Example

```text
git show
git show a1b2c3d
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Find a commit hash with:
   ```text
   git log --oneline
   ```
3. Copy a short hash from the output, e.g. `a1b2c3d`.
4. View that commit's details:
   ```text
   git show a1b2c3d
   ```
5. Or simply view the latest commit without typing a hash:
   ```text
   git show
   ```
6. Press `q` to exit if the output opens in a pager.

## 7. Expected Output

```text
commit a1b2c3d4e5f6071829304150617283940516273 (HEAD -> master)
Author: Natesa Krishnan V <you@example.com>
Date:   Mon Nov 24 09:00:00 2026 +0530

    Add draft readme file

diff --git a/readme-draft.txt b/readme-draft.txt
new file mode 100644
index 0000000..3b18e51
--- /dev/null
+++ b/readme-draft.txt
@@ -0,0 +1 @@
+Hello
```

## 8. Real-Time Use Case

Developers use `git show` to:
- Double-check exactly what a specific commit changed before deciding whether to build on it, revert it, or discuss it in a code review.
- Investigate a bug by viewing the commit that introduced a particular line of code.
- Quickly inspect the most recent commit right after making it, as a sanity check.

## 9. Important Notes

- You only need the first 7 characters of a commit hash (sometimes fewer) — Git will match it as long as it is unique enough.
- `git show` can also be used on branches and tags, not just raw commit hashes (a more advanced use you will encounter later).
- If a commit changed many files, the diff output can be long — use `q` to exit the pager at any time.
- `git show` does not change anything; it is a safe, read-only command.

## 10. Related Commands

- [`git log` / `git log --oneline`](git-log.md) – find the commit hash to inspect.
- [`git commit -m "message"`](git-commit.md) – create the commits you can later inspect.
- [`git restore filename`](../05-Restore-Commands/git-restore.md) – discard changes if you decide you don't want them.
