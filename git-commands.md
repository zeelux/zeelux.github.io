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
