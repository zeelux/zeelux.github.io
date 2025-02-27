# Git Quick Reference
I'm just getting started using git and so far I've used mostly 
GitHub Desktop and WebStorm's built-in git support. I'm adding some 
common commands here as a quick reference for myself when I need/want
to use terminal instead.

* Remove a file from version control (untrack)
```shell
 git rm --cached --force [path/to/file]
```
* Add a single file
```shell
git add [path/to/file]
```
* Add all files (excluding those in .gitignore)
```shell
git add .
```
* Switch branch
```shell
git checkout <<branch name>>
```
* Commit pending changes
```shell
git commit -m "<<Commit Message>>"
```
* Get latest from remote
```shell
git pull
```
* Create and switch to new branch, leaving unstaged pending changes in workspace. Then stage changes.
```shell
git checkout -b <<branch name>>
git add *
```
* Push changes to remote where the branch doesn't exist yet
```shell
git push --set-upstream origin <<branch-name>>
```
* Undo local changes to a tracked file
```shell
git checkout -- <<File Name1>> <<File Name2>>
```
* List remote branches that are not tracked locally
```shell
git fetch
git branch -r
```
OR
```shell
git remote show <remote-name>
```
* After fetching remote branches, check one of them out locally
```shell
git checkout -b <branch-name> <name-of-remote>/<branch-name>
```

## Moving committed changes to a new branch
I sometimes accidentally commit changes on the master branch locally. If that is a protected branch on the remote server that you cannot commit directly to, you need to move these changes to another branch and rollback master. 

### Note: Any changes not committed will be lost.
```shell
git branch newbranch      # Create a new branch, saving the desired commits
git reset --hard HEAD~3   # Move master back by 3 commits (GONE from master)
git checkout newbranch    # Go to the new branch that still has the desired commits
```
But do make sure how many commits to go back. Alternatively, you can instead of HEAD~3, simply provide the hash of the commit (or the reference like origin/master) you want to "revert back to" on the master (/current) branch, e.g:
```shell
git reset --hard a1b2c3d4
```
Similar approach with slightly different commands
```shell
git checkout -b newbranch # Create a new branch that includes the desired commits (current state of master)
git checkout master       # Switch back to master
git reset --hard HEAD~1   # Move master back by 1 commit (GONE from master)
git checkout newbranch    # Go to the new branch that still has the desired commits
```

## Ignoring changes for a tracked file

To prevent local changes for a specific file from being added to a Git commit, one can use the git update-index command with the --skip-worktree flag. 
This tells Git to ignore changes to the specified file in the working directory. Mark the file to be ignored.

```shell
 it update-index --skip-worktree <file_path>
```

Replace <file_path> with the actual path to the file. Verify the file is marked.

```shell
git ls-files -v
```
Files with the S flag in the output are marked with --skip-worktree. To revert and track changes again.

```shell
git update-index --no-skip-worktree <file_path>
```

This will remove the skip-worktree flag and changes will be tracked again.
