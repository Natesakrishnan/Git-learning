# git restore

## 1. Command Name
`git restore filename`, `git restore .`, and `git restore --staged filename`

## 2. Purpose
`git restore` is used to **undo changes**. It has two different jobs depending on how you use it:
- `git restore filename` / `git restore .` — discards changes in your **working folder**, putting a file (or all files) back to how they looked in the last commit.
- `git restore --staged filename` — removes a file from the **staging area** (undoes a `git add`), **without** touching the actual content of the file.

## 3. Syntax

```text
git restore filename
git restore .
git restore --staged filename
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git restore` | The sub-command for restoring/undoing changes. |
| `filename` | Restores only that specific file. |
| `.` | Restores **all** changed files in and below the current folder. |
| `--staged` | Instead of touching file content, this unstages a file — moving it from "staged" back to "modified but not staged", exactly undoing a `git add`. |

## 5. Example

Discard changes to one file (revert it to the last commit):
```text
git restore notes.txt
```

Discard changes to everything in the folder:
```text
git restore .
```

Unstage a file you accidentally staged (keeps your edits, just unstages them):
```text
git restore --staged notes.txt
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

**Discarding a working-folder change:**
1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Edit a file that is already committed, for example by adding text to `notes.txt`.
3. Check the change is visible:
   ```text
   git status
   ```
4. Discard the change, restoring the last committed version:
   ```text
   git restore notes.txt
   ```
5. Confirm the file is back to its committed state:
   ```text
   git status
   ```

**Unstaging a file:**
1. Stage a file:
   ```text
   git add notes.txt
   ```
2. Realize you are not ready to commit it yet, and unstage it:
   ```text
   git restore --staged notes.txt
   ```
3. Confirm with `git status` that `notes.txt` is back to "not staged" — but your edits are still there.

## 7. Expected Output

```text
K:\GitPractice> git restore notes.txt
K:\GitPractice> git status
On branch master
nothing to commit, working tree clean
```

```text
K:\GitPractice> git restore --staged notes.txt
K:\GitPractice> git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   notes.txt
```

## 8. Real-Time Use Case

Developers use `git restore` to:
- Throw away experimental edits that didn't work out, quickly returning a file to its last good, committed state.
- Fix a mistake where they staged the wrong file with `git add`, using `--staged` to undo just the staging without losing their actual edits.
- Clean up a messy working folder before starting a fresh piece of work, using `git restore .` to reset everything back to the last commit.

## 9. Important Notes — ⚠️ Destructive Command Warning

- **`git restore filename` and `git restore .` are destructive and permanently discard uncommitted changes in your working folder.** Once you restore a file this way, any edits since the last commit are **gone** and cannot be recovered through normal means. Always double-check with `git status` or `git diff` before restoring, if you are unsure.
- `git restore --staged filename` is **safe** — it only affects the staging area and never deletes or changes the actual content of your file.
- `git restore` **only affects files that Git is already tracking** (files that have been committed at least once, or staged). It does not delete brand-new, untracked files — for that, a different, more advanced command (`git clean`) is used, which is intentionally not covered here for beginners.
- When in doubt about whether a change can be recovered, it is safer to **commit first**, even with a simple message like `"WIP"` (work in progress), rather than risk losing work with `git restore`.

## 10. Related Commands

- [`git add filename` / `git add .`](../01-Basic-Git-Commands/git-add.md) – the command whose effect `git restore --staged` undoes.
- [`git status`](../01-Basic-Git-Commands/git-status.md) – always check before and after restoring.
- [`git commit -m "message"`](../01-Basic-Git-Commands/git-commit.md) – save your work permanently so it is never at risk of being discarded.
