Github.com
----------
`ssh -T git@github.com` <!-- authenticate with http://github.com -->  

# set remote url so we can use ssh keys
`git remote set-url origin git@github.com:$USER/$REPO`  

# add an upstream if the repo is a fork
`git remote add upstream git://github.com/$FORK/$REPO`  

# sync fork with upstream
`git pu`

# delete branch
`git branch -d branch_name` # -D for --force
`git push origin --delete branch_name`

Github: work flow for forked projects
------------------------------------
1. `git checkout master`
2. `git pu`
3. `git checkout <branchname>`
 ... hack...  
4. `git add --patch`
5. `git commit`
...  
6. `git log --patch`
7. `git rebase -i upstream` <!-- squash commits into one nice commit -->
8. `git log --patch`
9. `git push origin <branch_name>`
10. Create pull request.

Porcelain Commands
------------------
`git checkout -b <new_branch>` <!-- create and checkout branch -->
`git branch -d <branch>`	   <!-- delete branch -->
`git push origin --delete <branch_name>` <!-- delete remote branch -->
`git pu`								<!-- sync with upstream -->
`git rm $(git ls-files --deleted)`		<!-- remove all deleted -->
`git reset --hard 0d1d7fc32`

`git log`
`git show 66f962a` <!-- detailed view -->
`git show-branch --more=10`

`git diff 0d1d7fc32 87bf784`

`git rm` <!-- followed by commit -->
`git mv` <!-- and commit -->

`git config -l`


Plumbing Commands 
-----------------

