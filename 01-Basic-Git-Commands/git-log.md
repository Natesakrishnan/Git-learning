# git log

## 1. Command Name
`git log` and `git log --oneline`

## 2. Purpose
`git log` displays the **commit history** of your repository — a list of every snapshot ever committed, newest first. It shows who made each commit, when, and what message was attached. `git log --oneline` shows the same history in a shorter, easier-to-scan format with one commit per line.

## 3. Syntax

```text
git log
git log --oneline
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Runs a Git command. |
| `log` | The sub-command that lists commit history. |
| `--oneline` | A flag that compresses each commit down to a short hash and the commit message, on a single line. |

By default, `git log` shows, for every commit: a long **commit hash** (a unique ID), the author's name and email, the date and time, and the full commit message.

## 5. Example

```text
git log
git log --oneline
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into a repository that already has at least one commit:
   ```text
   cd K:\GitPractice
   ```
2. View the full history:
   ```text
   git log
   ```
3. Press the `Space` bar to scroll down if there are many commits, or `q` to quit the view and return to the prompt.
4. View the same history in compact form:
   ```text
   git log --oneline
   ```

## 7. Expected Output

Full `git log`:

```text
commit a1b2c3d4e5f6071829304150617283940516273 (HEAD -> master)
Author: Natesa Krishnan V <you@example.com>
Date:   Mon Nov 24 09:00:00 2026 +0530

    Add draft readme file
```

Compact `git log --oneline`:

```text
a1b2c3d (HEAD -> master) Add draft readme file
```

## 8. Real-Time Use Case

Developers use `git log` to:
- Review what has changed in a project over time, especially when joining an existing project.
- Find the exact commit hash needed for other commands, such as checking out an old version or reverting a change.
- Use `git log --oneline` for a quick, readable summary during code reviews or standup discussions, instead of scrolling through full commit details.

## 9. Important Notes

- `git log` opens in a **pager** (usually `less`) on some systems; on Windows Command Prompt it may simply print to the screen. If it ever appears "stuck", try pressing `q`.
- The commit hash at the top of each entry is unique and can be used elsewhere (for example, with `git show <hash>`).
- `git log` only shows commits that exist **locally** unless you have pulled the latest history from GitHub first.
- `(HEAD -> master)` next to the top commit tells you that is the current commit your `master` branch is pointing to.

## 10. Related Commands

- [`git show`](git-show.md) – see full details of one specific commit.
- [`git commit -m "message"`](git-commit.md) – create the commits that appear in the log.
- [`git status`](git-status.md) – check current state alongside history.
