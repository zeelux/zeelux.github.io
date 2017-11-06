# Git Quick Reference
I'm just getting started using git and so far I've used mostly 
GitHub Desktop and WebStorm's built-in git support. I'm adding some 
common commands here as a quick reference for myself when I need/want
to use terminal instead.

* Remove a file from version control (untrack)
```git
 git rm --cached --force [path/to/file]
```
* Add a single file
```git
git add [path/to/file]
```
* Add all files (excluding those in .gitignore)
```git
git add .
```
* Switch branch
```git
git checkout <<branch name>>
```
* Commit pending changes
```git
git commit -m "<<Commit Message>>"
```
* Get latest from remote
```git
git pull
```
* Create and switch to new branch, leaving unstaged pending changes in workspace. Then stage changes.
```git
git checkout -b <<branch name>>
git add *
```
* Push changes to remote where the branch doesn't exist yet
```git
git push --set-upstream origin <<branch-name>>
```

* Moving committed changes to a new branch

I've frequently accidentally commited changes on the master branch locally. Since that is a protected branch in my case I need to move these changes to another branch and rollback master. 

# Note: Any changes not committed will be lost.
```git
git branch newbranch      # Create a new branch, saving the desired commits
git reset --hard HEAD~3   # Move master back by 3 commits (GONE from master)
git checkout newbranch    # Go to the new branch that still has the desired commits
```
But do make sure how many commits to go back. Alternatively, you can instead of HEAD~3, simply provide the hash of the commit (or the reference like origin/master) you want to "revert back to" on the master (/current) branch, e.g:
```git
git reset --hard a1b2c3d4
```
Similar approach with slightly different commands
```git
git checkout -b newbranch # Create a new branch that includes the desired commits (current state of master)
git checkout master       # Switch back to master
git reset --hard HEAD~1   # Move master back by 1 commit (GONE from master)
git checkout newbranch    # Go to the new branch that still has the desired commits
```
