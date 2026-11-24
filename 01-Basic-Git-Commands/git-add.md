# git add

## 1. Command Name
`git add filename` and `git add .`

## 2. Purpose
`git add` moves changes from your working folder into the **staging area** (also called the "index"). Staging is like putting items into a box before you seal and ship it — it lets you choose exactly which changes will go into your next commit. Nothing is permanently saved to history until you also run `git commit`.

## 3. Syntax

```text
git add filename
git add .
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Runs a Git command. |
| `add` | The sub-command that stages changes. |
| `filename` | Stages only that **one specific file** (e.g. `git add index.html`). |
| `.` | A shortcut meaning "the current folder and everything inside it". Stages **all** new and modified files in and below the current directory. |

Staging does not change your files on disk — it only tells Git "include this version of this file in the next commit."

## 5. Example

Stage a single file:
```text
git add notes.txt
```

Stage everything that has changed:
```text
git add .
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Create or edit a couple of files:
   ```text
   echo File One > one.txt
   echo File Two > two.txt
   ```
3. Check what Git sees:
   ```text
   git status
   ```
4. Stage only `one.txt`:
   ```text
   git add one.txt
   ```
5. Run `git status` again — notice `one.txt` is staged, but `two.txt` is still untracked.
6. Stage everything that remains:
   ```text
   git add .
   ```
7. Run `git status` one more time to confirm both files are now staged.

## 7. Expected Output

`git add` itself prints nothing when it succeeds — that is normal. You confirm the result using `git status`:

```text
K:\GitPractice> git add one.txt
K:\GitPractice> git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   one.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        two.txt
```

## 8. Real-Time Use Case

- `git add filename` is used when a developer wants to commit **only one specific change** and leave other in-progress work out of the commit (keeping commits focused and clean).
- `git add .` is used when a developer has finished a chunk of work and all the changed files in the folder belong together in a single, logical commit.

## 9. Important Notes

- `git add .` stages **everything** under the current folder, including files you may not have meant to include — always run `git status` first to review what will be staged.
- Staging is not permanent — if you make a mistake, you can unstage a file with `git restore --staged filename` (see the Restore Commands section) before committing.
- Staging a file does **not** save it to history. You must still run `git commit` afterward.
- Be careful running `git add .` from the wrong folder — it stages everything below your current location, which could be more than you expect in a large project.

## 10. Related Commands

- [`git status`](git-status.md) – see what is staged vs. unstaged.
- [`git commit -m "message"`](git-commit.md) – save staged changes permanently into history.
- [`git restore --staged filename`](../05-Restore-Commands/git-restore.md) – undo staging a file.
