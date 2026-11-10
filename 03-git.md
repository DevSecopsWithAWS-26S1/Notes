# Branching scenarios

Use these commands to try a merge, a rebase, and a cherry-pick:

## Fast-forward merge

A regular merge can fast-forward when the target branch has not advanced independently:

```sh
git merge <branchname>
```

Use `--no-ff` only when you want a merge commit even though a fast-forward is available:

```sh
git merge --no-ff <branchname>
```

## Rebase

Move the current branch's commits onto the selected branch:

```sh
git rebase <branchname>
```

## Cherry-pick

Apply one commit to the current branch:

```sh
git cherry-pick <commit_hash>
```

## Branching strategy

The right strategy depends on the team and the project. Git Flow is a structured option, with distinct branches for features, releases, and urgent fixes.

### Sprints

A sprint is a time-boxed development and testing period with a defined set of work. Teams often plan weekly, bi-weekly, or monthly sprints based on the scope and their working cadence.

## Tags

Tags label particular points in repository history, such as a release or milestone. Create a lightweight tag at the current commit with:

```sh
git tag <tagname>
```

## Task

In your organization, turn on branch protection for `master`, decide which rules are appropriate, and verify that a direct push is rejected.
