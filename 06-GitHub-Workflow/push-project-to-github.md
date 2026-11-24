# Pushing a Project to GitHub (Creating a Repository, Connecting, and Pushing)

## 1. Workflow Name
Creating a GitHub repository → Connecting a local repository to GitHub → Pushing project files to GitHub

## 2. Purpose
This workflow covers the **complete first-time journey** of taking a project that exists only on your own computer (in `K:\GitPractice`) and publishing it on GitHub, so it is backed up online and shareable with others. It ties together `git init`, `git add`, `git commit`, `git remote add origin`, and `git push` into one end-to-end process.

## 3. Syntax (Commands Used)

```text
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/Natesakrishnan/Git-learning.git
git push -u origin master
```

## 4. Explanation

| Step | Command | What it does |
|---|---|---|
| 1 | Create a repository on GitHub.com | Makes an empty, online "home" for your project. |
| 2 | `git init` | Turns your local folder into a Git repository. |
| 3 | `git add .` | Stages all your project files. |
| 4 | `git commit -m "Initial commit"` | Saves the first snapshot of your project locally. |
| 5 | `git remote add origin <URL>` | Connects your local repository to the GitHub repository. |
| 6 | `git push -u origin master` | Uploads your commit(s) to GitHub and links `master` to `origin/master` for future pushes. |

## 5. Example

```text
cd K:\GitPractice
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/Natesakrishnan/Git-learning.git
git push -u origin master
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. **Create the GitHub repository first**, in your web browser:
   - Sign in at `github.com`.
   - Click **New repository**.
   - Name it `Git-learning` (matching the example URL used throughout this documentation).
   - Leave it **empty** — do **not** check "Add a README", so there is no conflicting history.
   - Click **Create repository**.
2. Open Command Prompt and move into your local project folder:
   ```text
   cd K:\GitPractice
   ```
3. Initialize Git (skip if already done):
   ```text
   git init
   ```
4. Stage all your project files:
   ```text
   git add .
   ```
5. Create your first commit:
   ```text
   git commit -m "Initial commit"
   ```
6. Connect your local repository to the GitHub repository you created:
   ```text
   git remote add origin https://github.com/Natesakrishnan/Git-learning.git
   ```
7. Push your project to GitHub for the first time:
   ```text
   git push -u origin master
   ```
8. Refresh the GitHub page in your browser — your files should now appear there.

## 7. Expected Output

```text
K:\GitPractice> git push -u origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Writing objects: 100% (4/4), 310 bytes | 310.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Natesakrishnan/Git-learning.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

## 8. Real-Time Use Case

This exact workflow is used by developers every time they:
- Start a brand-new personal or learning project and want it backed up and visible on GitHub.
- Turn a folder of code written locally (perhaps during a course or tutorial) into a shareable, portfolio-ready GitHub repository.
- Begin a new project at a job or in a team, before anyone else has contributed to it.

## 9. Important Notes

- Create the GitHub repository **empty** (no README/license/`.gitignore`) the first time, so pushing does not run into conflicting, unrelated histories.
- If Command Prompt asks for authentication, you may need a GitHub username and a **Personal Access Token** (used in place of a password) — this is a one-time setup step covered in GitHub's own account settings.
- Double-check the remote URL for typos before pushing; an incorrect URL causes a "repository not found" error.
- After this first push, you only need `git add`, `git commit`, and plain `git push` for future changes — the remote connection and upstream link are already set up.

## 10. Related Commands

- [`git init`](../01-Basic-Git-Commands/git-init.md)
- [`git add .`](../01-Basic-Git-Commands/git-add.md)
- [`git commit -m "message"`](../01-Basic-Git-Commands/git-commit.md)
- [`git remote add origin URL`](../04-GitHub-Remote-Commands/git-remote.md)
- [`git push -u origin branch_name`](../04-GitHub-Remote-Commands/git-push.md)
