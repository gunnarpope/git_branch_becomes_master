
# git_branch_becomes_master
This repo is to test making the current branch the new master and pushing it to the remote

by: Gunnar Pope 

# steps
* first, make a copy of the repo directory on your hard drive
* Try this to set the current branch as the master

```
 git branch test_branch # create a branch off from master
 vim hello_world.txt    # add a file to the master branch
 git add -A
 git commit -m "adding hello world file" #commit the file in the master branch
 git checkout test_branch		 # switch to the new branch
 vim hello_world_newbranch.txt		 # add a file to the new branch
 git checkout master			 # switch to the master branch
 git reset --hard test_branch		 # set the branch as the head of master
 git status				 # sanity check - still need to add the recent changes
 git add -A
 git commit -m "commiting all changes that existed in new branch named 'test_branch"
 git push				 # push all the changes to the remote

```

## Reconsile 'Detached HEAD' git error.
9/6/18

I created this error by doing a `git checkout <previous commit>` and then made some changed to the files. Essentially, I started editing the code to an unnamed branch. What you need to do is create a branch, check it out, then point the master branch to it using `git branch -f master temp`. See [How can I reconcile detached HEAD with master/origin?](https://stackoverflow.com/questions/5772192/how-can-i-reconcile-detached-head-with-master-origin) for a great explanation.


```
git branch temp
git branch
git checkout temp 
git diff master temp
git branch -f master temp
git checkout master
git status
git push

```

