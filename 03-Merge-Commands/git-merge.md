# git merge

## 1. Command Name
`git merge branch_name` and `git merge --abort`

## 2. Purpose
`git merge` combines the history of another branch **into** your current branch. For example, if you finished a feature on `feature-login` and want to bring it into `master`, you switch to `master` and merge `feature-login` into it. `git merge --abort` is a safety command used to cancel a merge that has run into problems (a conflict) and return to the state before the merge started.

## 3. Syntax

```text
git merge branch_name
git merge --abort
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git merge` | The sub-command that combines branch histories. |
| `branch_name` | The branch whose changes you want to bring **into** your current branch. |
| `--abort` | Cancels an in-progress merge that has conflicts, restoring your branch to how it was before you ran `git merge`. |

A merge can finish in one of two ways:
- **Fast-forward merge** – if your current branch has no new commits since the other branch was created, Git simply moves your branch pointer forward. No special merge commit is created.
- **Merge commit** – if both branches have diverging changes, Git creates a new commit that joins both histories together. If the **same lines** of the **same file** were changed differently on both branches, Git reports a **merge conflict** and asks you to resolve it manually before completing the merge.

## 5. Example

```text
git switch master
git merge feature-login
```

If a conflict happens and you want to cancel:
```text
git merge --abort
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Move into your repository and make sure your feature branch has commits:
   ```text
   cd K:\GitPractice
   git switch feature-login
   echo Login page content > login.txt
   git add login.txt
   git commit -m "Add login page"
   ```
2. Switch to the branch you want to merge **into** (usually `master`):
   ```text
   git switch master
   ```
3. Merge the feature branch into `master`:
   ```text
   git merge feature-login
   ```
4. If Git reports a conflict, open the listed file(s), look for conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`), manually edit the file to keep the correct content, then:
   ```text
   git add <the-conflicted-file>
   git commit
   ```
5. If you decide you are not ready to resolve the conflict, cancel it instead:
   ```text
   git merge --abort
   ```

## 7. Expected Output

A clean fast-forward merge:
```text
K:\GitPractice> git merge feature-login
Updating a1b2c3d..9f8e7d6
Fast-forward
 login.txt | 1 +
 1 file changed, 1 insertion(+)
```

A merge with a conflict:
```text
Auto-merging login.txt
CONFLICT (content): Merge conflict in login.txt
Automatic merge failed; fix conflicts and then commit the result.
```

## 8. Real-Time Use Case

Developers use `git merge` to:
- Bring a completed, tested feature branch back into `master` so it becomes part of the main project.
- Combine a teammate's branch with their own after reviewing the changes.
- Use `git merge --abort` when a conflict looks complicated and they want to pause, re-examine both branches, and try again later rather than resolving it under pressure.

## 9. Important Notes

- **Always commit or stash your current work before merging** — merging with uncommitted changes can be blocked or, in rare cases, cause confusing results.
- A merge **conflict** is not an error you did something wrong — it simply means Git needs your help deciding between two different versions of the same lines. Take your time resolving it.
- `git merge --abort` only works while a conflict is still unresolved and uncommitted. Once you commit the merge, you cannot "abort" it — you would need a different, more advanced command to undo it.
- Read the branch names carefully: `git merge feature-login` while standing on `master` merges `feature-login`'s changes **into** `master`, not the other way around.

## 10. Related Commands

- [`git switch branch_name`](../02-Branch-Commands/git-switch.md) – move to the branch you want to merge into.
- [`git branch -d branch_name`](../02-Branch-Commands/git-branch-delete.md) – delete a feature branch after it has been merged.
- [`git status`](../01-Basic-Git-Commands/git-status.md) – check for conflict markers and merge state.
- [`branch-collaboration.md`](../06-GitHub-Workflow/branch-collaboration.md) – see merging in the context of a full team workflow.
