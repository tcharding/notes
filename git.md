github.com
----------
* ssh -T git@github.com  # authenticate
* git remote set-url origin git@github.com:user/repo-name
* git remote add upstream git://github.com/FORK/foo

general usage
-------------
* git checkout -b <new_branch>	# create and checkout branch
* git branch -d <branch>		 # delete branch
* git push origin --delete <branch_name> # delete remote branch
* git pu # sync with upstream

work flow
---------
* git checkout master 
* git pu
* git checkout <branchname>
 ... hack...
* git add --patch
* git commit
...
* git log --patch
* git rebase -i upstream 	# squash commits into one nice commit
* git log --patch
* git push origin <branch_name>

