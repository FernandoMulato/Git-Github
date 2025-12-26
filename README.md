# Git–GitHub  
Fundamentals of Git & GitHub

## Git
### Check the Git version and get help

- `git -v`
- `git --version`
- `git -h`
- `git --help`

### Basic Terminal Commands

- `ls`: lists all directories in the current workspace.
- `cd`: moves to the desired directory (using tab completion or typing the name directly).
- `cd ..`: go back one level.
- arrow keys: navigate through previously used commands.
- `pwd`: shows the current path.
- `mkdir "folder_name"`: creates a folder.
- `code .`: opens the folder in Visual Studio Code if installed.

### Git Configuration

- `git config --global user.name "userName"`
- `git config --global user.email "email@example.com"`

### Git init

- `New-Item -Path "hello_git.py" -ItemType File`: creates a file of any type (.py, .java, etc.).
- `git init`: indicates that we want to work with Git.

### Branches in Git

- `git branch -m main`: renames the branch from master to main.
- `git config --global init.defaultBranch "branch_name"`: configuration to change the default name of the main branch.

### Git add and commit

- `git add file_name.example`: adds a specific file.
- `git add .`: adds all files.
- `git commit -m "comment"`: saves the changes to the Git repository.

### Git log and status

- `git status`: shows the status of files.
- `git log`: shows commit information.
- `git log --graph`: more visual representation.
- `git log --graph --pretty=oneline`: shows only commit messages.
- `git log --graph --decorate --all --oneline`: shortens the commit ID.

### Git checkout and reset

- `git checkout file_name.example`: moves to a specific point in the changes (moves HEAD). Similar to a rollback without saving.
- `git checkout .`: applies to all files.
- `git reset`: resets the file regardless of what was done afterward.

### Git alias

- `git config --global alias.tree "log --graph --decorate --all --oneline"`: creates an alias for a command to make it faster (tree is the alias).
- `git tree`: runs the alias.

### Gitignore

- `New-Item -Path ".gitignore" -ItemType File`: creates the file needed to ignore files.

### Git diff

- `git diff`: shows what has been modified without saving.

### Navigation

- `git checkout commit_id`: moves through the project changes.

### Git reset hard and reflog

- `git reset --hard commit_id`: moves to a specific point in the timeline, backward or forward.
- `git reflog`: shows the complete history.

### Git tag

- `git tag tag_name`: marks important points such as app versions. You can move to it using checkout (`git checkout main` to return).
- `git revert`: deletes a commit (dangerous).

### Git branch and switch

- `git branch branch_name`: creates a new branch.
- `git switch branch_name`: switches to another branch.

### Git merge

- `git merge main`: merges changes from another branch into the current one (in this case, the main branch).

### Git conflicts

- Remove unnecessary code in the editor, then add and commit the changes.

### Git stash

- Used when you must urgently switch branches and have code with errors.
- `git stash`: temporary commit that does not affect the tree.
- `git stash list`: shows pending stashes.
- `git stash pop`: restores the previous work.
- `git stash drop`: deletes the stash.

### Reintegration in Git

- Reintegrate into main by switching:
- `git diff login`: verify changes.
- `git merge login`: merge the login branch into main.

### Branch deletion

- `git branch -d branch_name`: deletes the branch but keeps it in memory.

## GitHub
### Introduction to GitHub

Git works locally, while GitHub works remotely.

### SSH Authentication

Check the documentation, as this may change.

In Git Bash:
- `ls -al ~/.ssh`: lists SSH keys. If it does not exist, the `.ssh` folder is created.
- `ssh-keygen -t ed25519 -C "your_email@example.com"`: creates a public and private key.

Add the key to the agent in PowerShell (administrator):
- `Get-Service -Name ssh-agent | Set-Service -StartupType Manual`
- `Start-Service ssh-agent`

PowerShell without elevated permissions:
- `ssh-add c:/Users/YOU/.ssh/id_ed25519`

Add the public key to GitHub in settings.
- `ssh -T git@github.com`: verify in Git Bash, type yes, and run again.

### Git remote

- `git remote add origin repository_url.git`: adds the remote repository.
- `git push -u origin branch_name`: syncs and uploads local files to GitHub.

### Project upload

- `git push origin branch_name`: uploads files to the repository if synchronized.

### Git fetch and pull

- `git fetch`: downloads the change history without applying changes.
- `git pull origin branch_name`: downloads history and changes.
- `git config pull.rebase false`: configures pull to use merge.

### Git clone

- `git clone ssh_project_url`: copies the repository using HTTPS, SSH, or GitHub CLI.

### Git push

- `git push --set-upstream origin main`: configures or syncs main to use git push and pull.

### GitHub fork

Used to clone a repository that is not yours.

# Collaborative workflow

## 🟢 MODEL 1 – Collaborators + Pull Requests (RECOMMENDED ⭐)

👉 This is the professional standard.

### 🔹 How it works

- You create the repository.
- You add team members as **Collaborators**.
- Each member:
  - Clones the repository.
  - Creates their own `feature/*` branch.
  - Pushes their feature branch.
  - Opens a **Pull Request** to `develop`.
- Another team member reviews and approves the PR.
- The changes are merged.
- The feature branch is deleted.

### 🔹 Typical Permissions

In GitHub:

- **Write** → can create branches and Pull Requests.
- **Maintain / Admin** → manage rules and repository settings.

👀 **Important:**

Even if they are collaborators, they **should NOT push directly** to `main` or `develop`.

This is enforced using **branch protection rules** 👇

## 🔐 Branch Protection (KEY)

In **Settings → Branches**:

For `main` and `develop`:

- ✅ Require Pull Request before merging
- ✅ Require at least one review
- ✅ Block direct pushes
- ❌ Do not allow force pushes

👉 **Result:**

- No one can break production.
- All changes go through code review.

---

## 🟡 MODEL 2 – Fork + Pull Request

👉 Commonly used in **open source projects**.

### 🔹 How it works

- You do NOT add members as collaborators.
- Each contributor:
  - Creates a **fork** of the repository.
  - Works on their own fork.
  - Opens a Pull Request to your repository.

### ❌ Disadvantages for closed teams

- Slower workflow.
- More friction.
- Not necessary if you trust your team.

## 🧩 So… How should features be handled in a team?

### Ideal workflow using Git Flow + GitHub

- `main` → production
- `develop` → integration
- `feature/*` → individual work

### Each team member:

```bash
git checkout develop
git pull
git checkout -b feature/login
```

**Then:**

```bash
    git push -u origin feature/login
```

**After that:**

- Pull Request: feature/login → develop

- Code review

- Merge

- Delete branch

### 🧠 Direct answer to the question

Should I add them as collaborators, or should they clone the repo and make PRs?

✅ Yes, add them as collaborators
✅ Yes, they should clone the repository
✅ Yes, they should work using feature branches
✅ Yes, they should create Pull Requests

👉 All of this together — it is not mutually exclusive.

### 🏆 Final recommendation (for your project)

Given that:

- You are learning Git Flow

- It is a team project

- It is probably a university or semi-professional project

👉 Use:

- Collaborators

- Mandatory Pull Requests

- Branch protection on main and develop

This is exactly how teams work in real companies 💼

# Next

### Pull request

When the repository is forked into your GitHub account, make changes and push them. Then go to GitHub, click collaborate, and create a PR.

If the PR arrives in your repository, review it under Pull Requests, leave comments, approve it, or request changes. To apply it, click **Merge pull request**.

### PR conflicts

Click resolve conflicts in the PR, fix the issues, mark as resolved, and commit the merge.

### Fork synchronization

Sync from the cloned repository.

### GitHub Markdown

Documentation is important; GitHub provides Markdown documentation.

### Graphical tools

Graphical tools include:

- GitHub Desktop
- GitKraken (recommended)
- Sourcetree
- Fork

### Git & GitHub Flow

- The **Main** branch (Production) versions releases such as v0.1, v0.2, etc.
- The **Develop** branch (QA) receives work from other teams.
- **Feature** branches are where teams work (login branch, payment branch, etc.).
- The **Release** branch verifies Develop and merges into Main, then closes Develop.
- The **Bugfix** branch fixes issues found in Release.
- The **Hotfix** branch fixes production issues and merges into Main and Develop.
- Check documentation to stay updated.

### Gitflow example

- `git flow version`: checks if git-flow is installed.
- `git flow init`: starts working with Git Flow.
- Configure settings or leave defaults.
- `git flow feature start feature_branch_name`: creates a new feature.
- `git flow feature finish feature_branch_name`: finishes the feature.
- `git flow release start release_name`: creates a release.
- `git flow release finish release_name`: finishes the release.
- In multi-person teams, all changes must go through a PR. The feature team submits a PR to the Develop branch team.
- To add branches created by Git Flow to GitHub, use:
    - `git push origin develop` (or `branch_name`)
    - `git push origin feature/login`
    - Important: 
        - `git push -u origin feature/feature_name`: To be able to do a git push to the respective branch.
        - `git push origin --delete feature/feature_name`: To remove the remote branch.
        - `git branch -r`: To view remote branches.
        - `git fetch --prune`: To clean local references of already deleted branches.



### Git cherry-pick and rebase (delicate)

- `git cherry-pick commit_id`, `git cherry-pick --continue`, `git cherry-pick --abort`: brings a commit into main.
- `git rebase branch_name`, `git rebase --continue`, `git rebase --abort`: rebases a branch and rewrites history.

### GitHub Pages and Actions

- **GitHub Pages**: create static websites.
- **Actions**: API for automation.

## Useful Links

- [Official Git Website](https://git-scm.com)
- [Git Book](https://git-scm.com/book/en/v2)
- Tools: [iTerm](https://iterm2.com/) + [Oh My Zsh](https://ohmyz.sh/), [VS Code](https://code.visualstudio.com/), [Miro](https://miro.com/)
- [Git Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet/)
- [GitHub](https://github.com)
- [GitHub Docs](https://docs.github.com/en)
- [SSH for GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh)
- [GitHub Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
- [GitHub Pages](https://pages.github.com/)
- [GitHub Actions](https://github.com/features/actions)