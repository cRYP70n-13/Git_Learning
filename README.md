# Creating Snapshots

## Viewing the staged/unstaged changes

* `git diff` # Shows unstaged changes
* `git diff --staged` # Shows staged changes
* `git diff --cached` # Same as the above

## Viewing the history

* `git log` # View the full history
* `git log --oneline` # Summary of the history
* `git log --reverse` # List the commits from the oldest to the newest

## Viewing a commit

* `git show <commit-hash>` # Shows the given commit
* `git show HEAD` # Shows the last commit
* `git show HEAD~2` # shows two steps before the last commit
* `git show HEAD:file.ext` # Shows the version of file.txt stored in the last commit

## Unstaging files (Undoing git add)

* `git restore --staged file.ext` # Copies the last version of files.js from repo to index

## Discarding local changes

* `git restore file.ext` # Copies the file.ext from index to working directory
* `git restore file1.ext file2.ext` # Restores multiple files in working directory
* `git restore .` # Discards all local changes (Except untracked files)
* `git clean -fd` # Removes all the untracked files

## Restoring an earlier version of a file

* `git restore --source=HEAD~2 file.ext`

# Browsing History

## Viewing the history

* `git log --stat` # Shows the list of modified files
* `git log --patch` # Shows the actual changes (patches)

## Filtering the history

* `git log -3` # Shows the last 3 entries
* `git log --author="cRYP70n"`
* `git log --before="2021-01-04"`
* `git log --grep="GoLang"` # Commits with "GoLang" in their messages
* `git log -S"GoLang"` # Commits with "GoLang" in their patches
* `git log hash1..hash2` # Range of commits
* `git log file.txt` # commits that touched file.txt

## Formatting the log output

* `git log --pretty=format:"%an commited %H"`

## Creating an alias

* `git config --global alias.lg "log --oneline"`

## Viewing a commit

* `git show HEAD~2`
* `git show HEAD~2 HEAD file.ext` # Shows the version of file stored in this commit

## Compairing commits

* `git diff HEAD~2 HEAD` # Shows the changes between two commits
* `git diff HEAD~2 HEAD file.ext` # changes to file.ext only

## Checking out a commit

* `git checkout <commit hash>` # Checks out the given commit
* `git checkout master` # Checks out the master branch

## Finding a bad commit

* `git bisect start`
* `git bisect bad` # Marks the current commit as a bad commit
* `git bisect good <commit hash>` # Marks the given commit as a good commit
* `git bisect reset` # Terminates the bisect session

# Rewriting History

## Undoing commits

* `git reset --soft HEAD^` # Removes the last commit, keeps changed staged
* `git reset --mixed HEAD^` # Unstages the changes as well
* `git reset --hard HEAD^` # Discards the local changes

## Reverting commits

* `git revert <commit-hash>` # reverts the given commit
* `git revert HEAD~3` # Reverts the last three commits
* `git revert --no-commit HEAD~4`

## Recovering lost commits

* `git reflog` # Shows the history of HEAD
* `git reflog show bugfix` # Shows the history of bugfix pointer

## Amending the last commits

* `git commit --amend` # which changes the commit message

## Interactive rebasing

* `git rebase -i HEAD~5`
