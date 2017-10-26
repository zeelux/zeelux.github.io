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
* Push chagnes to remote where the branch doesn't exist yet
```git
git push --set-upstream origin <<branch-name>>
```

* Moving to a new branch

Unless there are other circumstances involved, this can be easily done by branching and rolling back.

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
