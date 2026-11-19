# Branch protection

Configure protection for `master` or `main` from **Repository/Organization Settings > Rules > Rulesets**:

- Set a ruleset name.
- Select the bypass users or teams that are allowed to override rules.
- Target the `master` and/or `main` branch.
- Restrict branch deletion.
- Block force pushes.
- Require pull request reviews before merging.
- Set a minimum number of approvals.

Branch protection can be configured at repository or organization level.

## Force push

A force push replaces remote history and should be used only with caution:

```sh
git push origin <branch_name> --force
git push origin <branch_name> -f
```

## Squash commits

Squashing combines multiple commits into one, keeping the merge history concise.

To squash the latest three commits interactively:

```sh
git rebase -i HEAD~3
```

The editor may show the following commits:

```text
pick def5678 Second commit
pick ghi9012 Third commit
```

Keep the first commit as `pick` and mark later commits as `squash`:

```text
pick def5678 Second commit
squash ghi9012 Third commit
```

Save and close the editor. Git will prompt for the final commit message.


