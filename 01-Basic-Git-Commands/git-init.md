# git init

## 1. Command Name
`git init`

## 2. Purpose
`git init` is used to create a brand-new, empty Git repository inside a folder. It turns a normal folder into a folder that Git can track, by creating a hidden `.git` subfolder that stores all the version history, configuration, and metadata for the project. You only need to run this command **once per project** — right at the start.

## 3. Syntax

```text
git init
```

or, to create a new folder and initialize it at the same time:

```text
git init <folder-name>
```

## 4. Explanation

| Part | Meaning |
|---|---|
| `git` | Tells Windows Command Prompt you want to run a Git command. |
| `init` | Short for "initialize". This is the sub-command that creates the hidden `.git` folder. |
| `<folder-name>` | (Optional) The name of a new folder to create and initialize in one step. If you leave this out, Git initializes the **current** folder. |

After running `git init`, Git creates a `.git` folder containing things like:
- `HEAD` – a pointer to your current branch.
- `config` – repository-specific settings.
- `objects/` – where Git will eventually store your commits.
- `refs/` – where branch and tag pointers live.

You should never manually edit or delete files inside `.git` unless you really know what you are doing.

## 5. Example

```text
K:\GitPractice> git init
```

## 6. Step-by-Step Procedure (Windows Command Prompt)

1. Open **Command Prompt** (search for `cmd` in the Start menu).
2. Navigate to the folder where you want to create your project, for example:
   ```text
   cd K:\GitPractice
   ```
3. If the folder does not exist yet, create it first:
   ```text
   mkdir K:\GitPractice
   cd K:\GitPractice
   ```
4. Run:
   ```text
   git init
   ```
5. Confirm the `.git` folder was created:
   ```text
   dir /a
   ```
   You should see a `.git` entry in the listing (the `/a` flag shows hidden files).

## 7. Expected Output

```text
K:\GitPractice> git init
Initialized empty Git repository in K:/GitPractice/.git/
```

## 8. Real-Time Use Case

Developers run `git init` when:
- Starting a brand-new personal or team project from scratch.
- Converting an existing folder of code (that has never used Git) into a Git-tracked project, so they can start recording history before making further changes.
- Creating a local practice repository to learn Git commands safely, like the `K:\GitPractice` folder used throughout this documentation.

## 9. Important Notes

- **Do not run `git init` inside a folder that is already a Git repository** (or inside a subfolder of one) unless you specifically intend to create a *nested* repository — this can cause confusing behavior.
- Running `git init` again in the same folder is safe; it will **not** delete your existing history. Git will simply say it reinitialized the existing repository.
- `git init` only creates the repository — it does **not** connect you to GitHub. That requires `git remote add origin <URL>` (covered in the GitHub Remote Commands section).
- Always double check your current folder with `cd` before running `git init`, so you don't accidentally initialize the wrong directory (like your whole `C:\` drive).

## 10. Related Commands

- [`git status`](git-status.md) – check the state of your repository after initializing it.
- [`git remote`](../04-GitHub-Remote-Commands/git-remote.md) – connect your local repository to a GitHub repository.
- [`git add`](git-add.md) – start tracking files after initializing.
