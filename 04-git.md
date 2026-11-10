### Master branch protection:
* Go to repo >> Settings >> Rulesets >> Rulesets >>  New branch Ruleset 
    * Provide rulesetname  
    * Bypass list : Add your required bypassers 
    * Target Branches : master/main
    * Branch rules :   
        * Restrict deletions
        * Block force pushes
        * Require pull request reviews before merging
            * Add minimum number of approvals - 1/2

* Branch protection can be done at two levels :
    * Repository level 
    * Organization level


* Force push command :

```
git push origin <branch_name> --force
git push origin <branch_name> -f
```

### Squashing:
* If you want to combine multiple commits into one commit, you can use the squash option while merging a pull request. This helps in keeping the commit history clean and concise.

* Commands to ssquash in local :

    ```
    git rebase -i HEAD~3
    ```

* The above command will open a file like below. It will show only two commits , beacause we are squsing the second and third commit into the first commit:

    ```
    pick def5678 Second commit message
    pick ghi9012 Third commit message

    ```

    * remove pick and add squash 

    ```
    squash def5678 Second commit message
    squash ghi9012 Third commit message
    ```

* Do git log , you will see only one commit with the message of the first commit.



## Default reviewers for a PR : 


