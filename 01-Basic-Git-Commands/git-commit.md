# git commit

## 1. Command Name
`git commit -m "message"`

## 2. Purpose
`git commit` takes everything currently in the staging area and permanently saves it as a new **snapshot** in your project's history. Each commit is like a save point you can always return to. The `-m` flag lets you attach a short, descriptive message explaining what the commit changes, right from the command line.

## 3. Syntax

```text
git commit -m "message"
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Runs a Git command. |
| `commit` | The sub-command that creates a new snapshot from staged changes. |
| `-m` | Flag meaning "message follows". Without it, Git would open a text editor and ask you to type a message there instead. |
| `"message"` | A short description of what this commit does, written in quotes, e.g. `"Add login page"`. |

A commit records: a snapshot of all staged files, the author's name/email, a timestamp, the commit message, and a link to the previous commit (so Git can build a full history chain).

## 5. Example

```text
git commit -m "Add initial project files"
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository:
   ```text
   cd K:\GitPractice
   ```
2. Make a change and stage it:
   ```text
   echo Hello > readme-draft.txt
   git add readme-draft.txt
   ```
3. Commit the staged change with a clear message:
   ```text
   git commit -m "Add draft readme file"
   ```
4. Confirm it worked:
   ```text
   git log --oneline
   ```

## 7. Expected Output

```text
K:\GitPractice> git commit -m "Add draft readme file"
[master (root-commit) a1b2c3d] Add draft readme file
 1 file changed, 1 insertion(+)
 create mode 100644 readme-draft.txt
```

## 8. Real-Time Use Case

Developers commit:
- After completing a small, logical unit of work (for example, "fix login bug" or "add navbar styling").
- Before switching branches or trying something risky, so there is always a safe point to come back to.
- Regularly throughout the day, rather than saving up a huge pile of unrelated changes into one giant commit.

## 9. Important Notes

- You cannot commit anything that has not been staged first with `git add`. If `git status` shows unstaged or untracked changes, those will **not** be included in the commit.
- Write clear, specific commit messages. `"fixed stuff"` is a common beginner mistake — prefer something like `"Fix typo in header navigation"`.
- If you forget `-m`, Git opens a text editor (often Vim) for the message, which can be confusing for beginners. Always include `-m "..."` until you are comfortable with editors.
- The very first commit in a repository is sometimes called the **root commit**, as shown in the sample output above.

## 10. Related Commands

- [`git add filename` / `git add .`](git-add.md) – stage changes before committing.
- [`git status`](git-status.md) – verify what will be included before committing.
- [`git log`](git-log.md) – view the commit after creating it.
- [`git push`](../04-GitHub-Remote-Commands/git-push.md) – upload commits to GitHub.
