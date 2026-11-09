## scenarios: 
* fastforward merge
* rebase    
* cherry-pick


*  fastforward merge :
    ```
    git merge --no-ff <branchname>
    ```
* rebase:

    ```
    git rebase <branchname>
    ```
* cherry-pick:
    ```
    git cherry-pick <commit_hash>
    ```

## Branching startegy :
* It depends on the team and project requirements. Some common branching strategies include:
    * Git Flow: A branching model that defines a strict branching structure with specific branches for features, releases, and hotfixes. It provides a clear workflow for managing development and release cycles.

* Sprint :  
    * sprint is the time for the feature development and testing. It is a time-boxed period during which a specific set of work is completed and made ready for review. Sprints are commonly used in agile software development methodologies, such as Scrum, to organize and manage the development process.
    * Weekly / Bi-weekly / Monthly sprints are common, depending on the team's workflow and project requirements. The duration of a sprint is typically determined by the team and can vary based on factors such as project complexity, team size, and development goals.

## tagging in git :
* Tagging is a way to mark specific points in a Git repository's history. It is used for creating release versions, marking important milestones, or identifying specific commits. Tags are often used to indicate stable versions of the codebase that can be referenced later.

* git tag <tagname> : This command creates a new tag with the specified name. By default, it creates a lightweight tag that points to the current commit.


### Task :
* In your own organization , try to protect the master branch.
* list down all rules that you feel are important to protect the master branch.
* Simulate the direct push rejection to the master branch.