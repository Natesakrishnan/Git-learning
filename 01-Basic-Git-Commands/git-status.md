# git status

## 1. Command Name
`git status`

## 2. Purpose
`git status` shows the **current state** of your working folder and staging area. It tells you which files have been changed, which files are staged and ready to be committed, and which files Git does not know about yet (untracked files). It is the command you will run most often while learning Git, because it tells you exactly what to do next.

## 3. Syntax

```text
git status
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Runs a Git command. |
| `status` | Asks Git to compare three things: your last commit, your staging area, and your working folder — and report the differences. |

`git status` never changes anything — it is completely safe to run as often as you like.

## 5. Example

```text
K:\GitPractice> git status
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Open Command Prompt and move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Create a new file to see status in action:
   ```text
   echo Hello Git > notes.txt
   ```
3. Run:
   ```text
   git status
   ```
4. Observe that `notes.txt` is listed under **Untracked files**.
5. Stage the file with `git add notes.txt` and run `git status` again to see it move to **Changes to be committed**.

## 7. Expected Output

Before staging anything:

```text
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        notes.txt

nothing added to commit but untracked files present (use "git add" to track)
```

After running `git add notes.txt`:

```text
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   notes.txt
```

## 8. Real-Time Use Case

Developers run `git status` constantly during everyday work to:
- Check what has changed before deciding whether to `git add` or `git commit`.
- Make sure they are not about to commit the wrong files.
- Double-check that a merge or pull completed cleanly with no leftover conflicts.
- Confirm which branch they are currently on (the first line always shows `On branch <name>`).

## 9. Important Notes

- `git status` is a **read-only** command — it never modifies your files or history, so there is no risk in running it.
- If `git status` shows files you never intended to track (like build output or temporary files), you may need a `.gitignore` file to exclude them — a slightly more advanced topic to explore after mastering the basics.
- The messages shown by `git status` (like `use "git add <file>..." to include`) are hints — Git is literally telling you the next command to run.

## 10. Related Commands

- [`git add filename`](git-add.md) – stage a specific file.
- [`git add .`](git-add.md) – stage all changed files.
- [`git commit -m "message"`](git-commit.md) – save staged changes into history.
- [`git log`](git-log.md) – view the commit history once changes are committed.
