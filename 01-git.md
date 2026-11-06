## Git 

```


To initialize a new git repository in the current directory
-----------------------------------------------------------
* git init . 

To move all new and modified files from working tree to staging area
--------------------------------------------------------------------
* git add .

To add particular file to staging area
---------------------------------------
* git add <filename>


To add all changes to staging area
----------------------------------
* git add  -A 


To save staged changes in local repo
------------------------------------
* git commit -m "<commit message>"


To remove specified file from staging area
--------------------------------------------
* git reset <filename>

To remove changes on working tree after we do reset
---------------------------------------------------
* git checkout filename

To remove changes from staging area and working tree 
-----------------------------------------------------
* git reset --hard 


To create a new commit that reverses the changes introduced by earlier commit
-----------------------------------------------------------------------------
* git revert <commitid>

To display complete commit history
---------------------------------
* git log 

To display commit history in a short, single line format
---------------------------------------------------------

* git log --oneline

To list all local branches
--------------------------

* git branch

To list all remote branches
---------------------------
* git branch -r 

To list all local and remote branches
-------------------------------------
* git branch -a 

To create new branch
---------------------
* git branch <branchname>


To switch from current branch to other existing branch
------------------------------------------------------
* git checkout <branchname>


To create new branch and immediately switches to it
----------------------------------------------------
* git checkout -b <branchname>

To config git username globally
-------------------------------
* git config --global user.name "<username>"

To config git email globally
----------------------------
* git config --global user.email "<Useremail>"

To show which remote repo connected to local repo
-------------------------------------------------
* git remote -v 

To show remote config in local repo
------------------------------------
* git config --list 

To connect local repo to remote repo
------------------------------------
* git remote add origin <repourl>

To connect to already existed configured remote repo
----------------------------------------------------
* git remote set-url origin <repourl>

To push local commits to remote repo
------------------------------------
* git push origin <branchname>


To delete local branch 
-----------------------
* git branch -d <branchname>
* git branch --delete <branchname>

To delete remote branch
------------------------
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

