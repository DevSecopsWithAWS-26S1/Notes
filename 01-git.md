## Git 

```


* git init . 

* git add .
* git add <filename>
* git add  -A 

* git commit -m "<commit message>"

* git reset <filename>
* git checkout filename
* git reset --hard 

* git revert <commitid>

* git log 

* git log --oneline 

* git branch 

* git branch -r 

* git branch -a 

* git branch <branchname>

* git checkout <branchname>

* git checkout -b <branchname>

* git config --global user.name "<username>"

* git config --global user.email "<Useremail>"

* git remote -v 

* git config --list 

* git remote add origin <repourl>

* git remote set-url origin <repourl>

* git push origin <branchname>


* git branch -d <branchname>
* git branch --delete <branchname>

* git push origin --delete <branchname>

```

##  A new developer joined the team and wants to contribute to the project. They need to clone the repository to their local machine. What command should they use?

* git clone <repository_url>

* https - 
    ```
    git clone https://github.com/DevSecopsWithAWS-26S1/Notes.git

    ```

##  Pull
* pull is used to fetch and download content from a remote repository and immediately update the local repository to match that content.

```
git pull origin <branchname> 
```

## Merge 
 * Merge is used to combine the changes from one branch into another branch. It takes the contents of a source branch and integrates it with the target branch.

```
git merge <branchname>
```

## Merge Conflicts :    
* When two files on the branches are having changes on the same line, then git will not be able to merge the branches automatically. This is called a merge conflict.


## Pull Request :
* A pull request is a way to submit contributions to a project. It is often used in collaborative development environments, such as GitHub, GitLab, and Bitbucket. When a developer wants to contribute changes to a project, they can create a pull request to propose their changes to the project's maintainers. The maintainers can then review the changes, discuss them, and decide whether to merge them into the main codebase.

