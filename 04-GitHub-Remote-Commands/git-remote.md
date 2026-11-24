# git remote

## 1. Command Name
`git remote -v` and `git remote add origin URL`

## 2. Purpose
A **remote** is a saved connection between your local repository and a repository hosted somewhere else — most commonly on GitHub. `git remote add origin URL` creates that connection and names it `origin` (the standard, conventional name for your main remote). `git remote -v` ("verbose") lists all remotes currently connected to your repository and their URLs.

## 3. Syntax

```text
git remote -v
git remote add origin URL
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git remote` | The sub-command for managing remote connections. |
| `-v` | Flag meaning "verbose" — shows the full URL for each remote instead of just its name. |
| `add` | Adds a new remote connection. |
| `origin` | The conventional name given to your primary remote. You could technically name it anything, but almost every project uses `origin`. |
| `URL` | The web address of the remote repository, e.g. `https://github.com/Natesakrishnan/Git-learning.git`. |

## 5. Example

```text
git remote add origin https://github.com/Natesakrishnan/Git-learning.git
git remote -v
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Create a new, empty repository on GitHub first (in your browser), **without** a README, so it stays empty and ready to receive your local project.
2. Copy the repository's HTTPS URL, e.g. `https://github.com/Natesakrishnan/Git-learning.git`.
3. In Command Prompt, move into your local repository:
   ```text
   cd K:\GitPractice
   ```
4. Connect it to GitHub:
   ```text
   git remote add origin https://github.com/Natesakrishnan/Git-learning.git
   ```
5. Confirm the connection:
   ```text
   git remote -v
   ```

## 7. Expected Output

```text
K:\GitPractice> git remote add origin https://github.com/Natesakrishnan/Git-learning.git
K:\GitPractice> git remote -v
origin  https://github.com/Natesakrishnan/Git-learning.git (fetch)
origin  https://github.com/Natesakrishnan/Git-learning.git (push)
```

Notice two lines appear — one for `fetch` (downloading) and one for `push` (uploading) — because the same URL is used for both directions by default.

## 8. Real-Time Use Case

Developers use `git remote` to:
- Connect a brand-new local project to a brand-new, empty GitHub repository for the very first time.
- Check which GitHub (or other hosting) repository their local folder is currently linked to, especially when working across multiple projects.
- Set up multiple remotes in more advanced workflows (for example, one for a personal fork and one for the original/upstream project) — a topic to explore after mastering the basics.

## 9. Important Notes

- You can only `add` a remote named `origin` **once**. If it already exists and you need to change the URL, you would use `git remote set-url origin <new-URL>` instead of `add` (a slightly more advanced variant).
- Double-check the URL for typos — an incorrect URL will cause `git push` and `git pull` to fail with a "repository not found" style error.
- `git remote add` does **not** upload anything by itself — it only creates the connection. You still need `git push` to actually send your commits to GitHub.
- Make sure the GitHub repository is **empty** (no README, license, or `.gitignore` created automatically) the first time you connect a local project, to avoid conflicting histories.

## 10. Related Commands

- [`git push origin master`](git-push.md) – upload your local commits to the connected remote.
- [`git pull`](git-pull.md) – download and merge changes from the remote.
- [`git fetch`](git-fetch.md) – download changes from the remote without merging them yet.
- [`push-project-to-github.md`](../06-GitHub-Workflow/push-project-to-github.md) – full walkthrough of connecting and pushing a new project.
