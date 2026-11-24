# Creating and Merging a Pull Request on GitHub

## 1. Workflow Name
Creating and pushing a new branch → Creating a Pull Request → Merging a Pull Request

## 2. Purpose
A **Pull Request** (PR) is GitHub's way of proposing that changes from one branch be reviewed and then merged into another branch (usually `master`). Instead of merging locally with `git merge`, a Pull Request lets you (or teammates) **review the changes on GitHub's website first**, leave comments, and then merge with a click once everyone is happy. This workflow walks through the full cycle, from creating a branch to merging its Pull Request.

## 3. Syntax (Commands Used)

```text
git switch -c feature-login
git add .
git commit -m "Add login page"
git push -u origin feature-login
```
Then the Pull Request itself is created and merged through the GitHub website, not the command line.

## 4. Explanation

| Step | Where it happens | What happens |
|---|---|---|
| Create a branch | Command Prompt | `git switch -c feature-login` creates and moves to a new branch. |
| Make changes & commit | Command Prompt | Normal `git add` + `git commit` workflow on the new branch. |
| Push the branch | Command Prompt | `git push -u origin feature-login` uploads the new branch to GitHub. |
| Open a Pull Request | GitHub website | GitHub detects the new branch and offers a **"Compare & pull request"** button. |
| Review | GitHub website | You (or teammates) read the diff, leave comments, and request changes if needed. |
| Merge | GitHub website | Clicking **"Merge pull request"** combines the branch into `master` on GitHub. |
| Update locally | Command Prompt | `git switch master` then `git pull` brings the merged changes back to your computer. |

## 5. Example

```text
git switch -c feature-login
echo Login page content > login.txt
git add login.txt
git commit -m "Add login page"
git push -u origin feature-login
```

## 6. Step-by-Step Procedure (Windows Command Prompt + GitHub Website)

1. Move into your repository and create a new branch for your change:
   ```text
   cd K:\GitPractice
   git switch -c feature-login
   ```
2. Make your changes, then stage and commit them:
   ```text
   git add .
   git commit -m "Add login page"
   ```
3. Push the new branch to GitHub:
   ```text
   git push -u origin feature-login
   ```
4. Open `https://github.com/Natesakrishnan/Git-learning` in your browser. GitHub will usually show a yellow banner with a **"Compare & pull request"** button for your newly pushed branch — click it.
5. Add a clear title and description explaining what the branch changes, then click **"Create pull request"**.
6. Review the diff shown on the Pull Request page (or have a teammate review it and leave comments).
7. Once satisfied, click **"Merge pull request"**, then **"Confirm merge"**.
8. Back in Command Prompt, update your local `master` branch with the newly merged change:
   ```text
   git switch master
   git pull
   ```

## 7. Expected Output

Pushing the branch:
```text
K:\GitPractice> git push -u origin feature-login
...
remote: Create a pull request for 'feature-login' on GitHub by visiting:
remote:      https://github.com/Natesakrishnan/Git-learning/pull/new/feature-login
To https://github.com/Natesakrishnan/Git-learning.git
 * [new branch]      feature-login -> feature-login
Branch 'feature-login' set up to track remote branch 'feature-login' from 'origin'.
```

After merging on GitHub and pulling locally:
```text
K:\GitPractice> git pull
Updating a1b2c3d..9f8e7d6
Fast-forward
 login.txt | 1 +
 1 file changed, 1 insertion(+)
```

## 8. Real-Time Use Case

Pull Requests are the standard way professional teams:
- Review each other's code before it becomes part of the main project, catching bugs and style issues early.
- Discuss proposed changes directly on GitHub, with comments attached to specific lines of code.
- Keep a clear, searchable history of **why** a change was made, since the Pull Request description and discussion stay attached to the merge forever.
- Run automated checks (tests, linters) on a Pull Request before allowing it to be merged.

## 9. Important Notes

- You do not need to be part of a team to practice Pull Requests — you can open one against your own repository, review it yourself, and merge it, which is a great way to learn the workflow.
- Always push your branch (`git push -u origin branch_name`) **before** you can open a Pull Request for it — GitHub needs the branch to exist remotely first.
- After merging a Pull Request on GitHub, remember to `git pull` locally afterward, and consider deleting the now-merged branch both on GitHub (GitHub often offers a "Delete branch" button) and locally with `git branch -d`.
- Keep Pull Requests focused on one feature or fix at a time — this makes them much easier to review.

## 10. Related Commands

- [`git switch -c branch_name`](../02-Branch-Commands/git-switch.md)
- [`git push -u origin branch_name`](../04-GitHub-Remote-Commands/git-push.md)
- [`git pull`](../04-GitHub-Remote-Commands/git-pull.md)
- [`git merge branch_name`](../03-Merge-Commands/git-merge.md) – the local equivalent of what GitHub does when you click "Merge".
- [`branch-collaboration.md`](branch-collaboration.md) – the full team workflow this fits into.
