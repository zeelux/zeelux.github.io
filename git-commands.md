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
* Commit pending changes
* Get latest from remote
