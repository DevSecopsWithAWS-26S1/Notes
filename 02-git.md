## Task 
* Create a PR from dev to master in the Notes repository.
* Create your own organization and repo inside it and give me the user access to it. Repo should be private repo.


* blame:
    * git blame is used to show the last modification of each line in a file, along with the author and commit information. It helps to identify who made changes to specific lines of code and when those changes were made. This can be useful for tracking down bugs, understanding the history of a file, and collaborating with other developers.

```
git blame <filename>
```

* fastforward merge
    * A fast-forward merge is a type of merge that occurs when the branch being merged has not diverged from the branch it is being merged into. In other words, the branch being merged is a direct descendant of the branch it is being merged into. In this case, Git can simply move the pointer of the target branch forward to the latest commit of the source branch, without creating a new merge commit.

* rebase
    * A rebase is a Git command that allows you to move or combine a sequence of commits to a new base commit. It is often used to maintain a clean and linear commit history by integrating changes from one branch onto another. When you rebase, Git takes the commits from the source branch and applies them on top of the target branch, effectively rewriting the commit history.

* cherry-pick
    * Cherry-pick is a Git command that allows you to apply a specific commit from one branch onto another branch. It is useful when you want to selectively incorporate changes from one branch into another without merging the entire branch. When you cherry-pick a commit, Git creates a new commit on the target branch with the same changes as the original commit. 

