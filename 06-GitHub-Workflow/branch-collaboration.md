# Branch Collaboration Workflow (Working Safely with Branches and GitHub)

## 1. Workflow Name
Full branch collaboration cycle: creating branches, pushing, pulling, merging, resolving conflicts, and cleaning up branches (local and remote).

## 2. Purpose
This document ties together everything learned so far into the **complete, repeatable cycle** a developer follows when collaborating with others (or even just with themselves across different sessions) using Git and GitHub. It shows how all the individual commands fit together in the order they are normally used.

## 3. Syntax (Full Cycle)

```text
git switch master
git pull
git switch -c feature-name
git add .
git commit -m "message"
git push -u origin feature-name
(open Pull Request, review, merge on GitHub)
git switch master
git pull
git branch -d feature-name
git push origin --delete feature-name
```

## 4. Explanation

| Stage | Command(s) | Purpose |
|---|---|---|
| 1. Sync first | `git switch master` → `git pull` | Start from the latest version of the shared code. |
| 2. Branch off | `git switch -c feature-name` | Create an isolated space for your change. |
| 3. Work | `git add .` → `git commit -m "message"` | Save your progress in small, clear commits. |
| 4. Share | `git push -u origin feature-name` | Upload your branch so others (or GitHub) can see it. |
| 5. Review | Pull Request on GitHub | Get feedback before the change becomes permanent. |
| 6. Integrate | Merge the Pull Request on GitHub | Combine the reviewed change into `master`. |
| 7. Re-sync | `git switch master` → `git pull` | Bring the newly merged change back to your computer. |
| 8. Clean up | `git branch -d feature-name` → `git push origin --delete feature-name` | Remove the finished branch locally and remotely. |

## 5. Example

A developer fixing a navbar bug might run:

```text
git switch master
git pull
git switch -c bugfix-navbar
echo Fix navbar alignment > navbar.txt
git add navbar.txt
git commit -m "Fix navbar alignment bug"
git push -u origin bugfix-navbar
```
...then open and merge a Pull Request on GitHub, and finally:
```text
git switch master
git pull
git branch -d bugfix-navbar
git push origin --delete bugfix-navbar
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Always start a new piece of work from an up-to-date `master`:
   ```text
   cd K:\GitPractice
   git switch master
   git pull
   ```
2. Create a new branch named clearly after the work you are doing:
   ```text
   git switch -c bugfix-navbar
   ```
3. Make your changes, checking progress along the way:
   ```text
   git status
   ```
4. Stage and commit your work, ideally in small, focused commits:
   ```text
   git add .
   git commit -m "Fix navbar alignment bug"
   ```
5. Push your branch to GitHub:
   ```text
   git push -u origin bugfix-navbar
   ```
6. Open a Pull Request on GitHub (see [`github-pull-request.md`](github-pull-request.md)), get it reviewed, and merge it.
7. Return to `master` and pull down the merged result:
   ```text
   git switch master
   git pull
   ```
8. Delete the now-finished branch, both locally and on GitHub:
   ```text
   git branch -d bugfix-navbar
   git push origin --delete bugfix-navbar
   ```

## 7. Expected Output

```text
K:\GitPractice> git branch -d bugfix-navbar
Deleted branch bugfix-navbar (was 9f8e7d6).

K:\GitPractice> git push origin --delete bugfix-navbar
To https://github.com/Natesakrishnan/Git-learning.git
 - [deleted]         bugfix-navbar
```

## 8. Real-Time Use Case

This is the everyday rhythm of working on a real software team:
- Every bug fix or feature follows the same pattern: sync → branch → work → push → review → merge → clean up.
- Keeping `master` always deployable and stable, because new work only ever enters it through a reviewed Pull Request.
- Avoiding the confusion of multiple people editing `master` directly at the same time, which is a common source of conflicts and mistakes for beginners.

## 9. Important Notes

- **Local branches vs. remote-tracking branches:** your local `feature-name` branch and GitHub's `origin/feature-name` are related but separate — pushing, pulling, and fetching are what keep them in sync. Deleting one does not automatically delete the other (see [`git branch -d`](../02-Branch-Commands/git-branch-delete.md) and [`git push origin --delete`](../04-GitHub-Remote-Commands/git-push.md)).
- Always pull the latest `master` **before** branching, to reduce the chance of conflicts later.
- If a conflict does appear during a merge or pull, resolve it calmly using the steps in [`git merge`](../03-Merge-Commands/git-merge.md) — conflicts are a normal, expected part of collaboration, not a sign of failure.
- Clean up finished branches regularly (`git branch -d` and `git push origin --delete`) to keep both your local and remote repositories easy to navigate.

## 10. Related Commands

- [`git switch branch_name` / `git switch -c branch_name`](../02-Branch-Commands/git-switch.md)
- [`git pull`](../04-GitHub-Remote-Commands/git-pull.md) / [`git fetch`](../04-GitHub-Remote-Commands/git-fetch.md) / [`git push`](../04-GitHub-Remote-Commands/git-push.md)
- [`git merge branch_name`](../03-Merge-Commands/git-merge.md)
- [`git branch -d branch_name`](../02-Branch-Commands/git-branch-delete.md)
- [`github-pull-request.md`](github-pull-request.md) – detailed Pull Request steps referenced in stage 5–6 above.
