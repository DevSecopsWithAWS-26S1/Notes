# Git essentials

## Common commands

```sh
git init .

git add .
git add <filename>
git add -A

git commit -m "<commit message>"

git reset <filename>
git checkout filename
git reset --hard

git revert <commitid>

git log
git log --oneline

git branch
git branch -r
git branch -a
git branch <branchname>

git checkout <branchname>
git checkout -b <branchname>

git config --global user.name "<username>"
git config --global user.email "<Useremail>"

git remote -v
git config --list

git remote add origin <repourl>
git remote set-url origin <repourl>

git push origin <branchname>

git branch -d <branchname>
git branch --delete <branchname>
git push origin --delete <branchname>
```

## Clone the repository

When joining a project, copy its remote repository to your machine with `git clone`:

```sh
git clone <repository_url>
```

For example, clone the Notes repository over HTTPS:

```sh
git clone https://github.com/DevSecopsWithAWS-26S1/Notes.git
```

## Pull remote changes

`git pull` downloads updates from the remote and integrates them into the current local branch:

```sh
git pull origin <branchname>
```

## Merge branches

Use `git merge` to bring the changes from another branch into the branch you currently have checked out:

```sh
git merge <branchname>
```

## Merge conflicts

A conflict can occur when branches change the same part of a file and Git cannot combine the edits automatically. Resolve the affected lines, then commit the result.

## Pull requests

A pull request proposes a set of changes for review before they are merged into a shared branch. Teammates can inspect the changes, discuss them, and approve or request updates. GitHub, GitLab, and Bitbucket all support pull requests or equivalent review workflows.
