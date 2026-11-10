# Working with Git history and teams

## Tasks

- Open a pull request from `dev` to `master` in the Notes repository.
- Create an organization and a private repository, then grant the requested user access.

## Blame

`git blame` shows the most recent commit and author associated with each line of a file. It can help trace when a line changed and provide context when investigating a bug:

```sh
git blame <filename>
```

## Fast-forward merges

A fast-forward merge is possible when the target branch has no new commits of its own since the feature branch was created. Git can advance the target branch pointer without creating a merge commit.

## Rebase

`git rebase` replays a branch's commits on top of a new base commit. This can produce a linear history, but it rewrites commit IDs, so coordinate before rebasing commits that others already use.

## Cherry-pick

`git cherry-pick` applies one selected commit to the current branch without merging all the other changes from its source branch:

```sh
git cherry-pick <commit_hash>
```

## Branching strategies

Choose a branching model that fits the team and its release process. Git Flow is one option; it separates feature work, releases, and urgent fixes into defined branch types.

## Sprints

A sprint is a fixed period for completing and reviewing a planned set of work. Teams commonly use weekly, two-week, or monthly sprints, depending on their goals and workflow.

## Git tags

Tags mark specific commits, often to identify releases or milestones. A lightweight tag points directly to the current commit:

```sh
git tag <tagname>
```

## Task

- Protect the `master` branch in your organization.
- List the rules you consider useful for protecting it.
- Try a direct push to `master` and observe the rejection.
