# Git

## General
### Initialize Repository
`git init`

### Get Help
```
git --help
git config --help
```

### List configurations
`git config --global -l`

### Set configuration
`git config user.name laiboonh`

### Set editor. This editor is for OSX only
`git config --global merge.tool opendiff`

### See history. Refer below for more advance commands
`git log`


## Stage
### Stage files
```
git add README.md
git add -A
```
### Unstage files. HEAD refers to last commit on the current branch/timeline you are currently on.
`git reset HEAD <file>`

### To completely stop tracking and remove file from repo (and filesystem)
```
git rm -f test.log
git commit -m "removed test.log"
```
### To completely stop tracking the file only (file remains in filesystem)
```
git rm --cached test.log
git commit -m "removed test.log"
```

### Reset changes
`git checkout -- README.md`


## Commit
### Commit files
`git commit -m "commit message"`

### Undo last commit. Reset into staging. ^ does not work in DOS, use ~ instead.
```
git reset --soft HEAD^
git reset --soft HEAD~
```

### Undo last 2 commits.
`git reset --soft HEAD~~`

### Undo last commit and remove all changes
`git reset --hard HEAD~`

### Add file to last commit and amend last commit message
```
git add git.ignore
git commit --amend -m "new message"
```

### Show unstaged difference since last commit
`git diff`

### Show staged difference since last commit
`git diff --staged`


## Remote
### View current remotes
`git remote-v`

### Add remote
`git remote add <name> <address>`

### Remove remote
`git remote rm <name>`

### Push to Github. -u is used so that you can do git push subsequently without arguments.
`git push -u <name> <branch>`

### Pull down changes from Github
`git pull`


## Branching.

### To see all remote branches
`git branch -r`

### To see more details about remote branches
`git remote show origin`

### Delete remote branch
`git push origin :shopping_cart`

### Delete local branch
`git branch -d shopping_cart`

### Cleanup stale branches
`git remote prune origin`

### Link up to remote branch of your choice
### This would push local staging to heroku-staging remote staging branch
`git push heroku-staging staging`
### This would push local staging to heroku-staging remote master branch
`git push heroku-staging staging:master`

### After branching HEAD is still at the master timeline. Switch to cat timeline.
```
git branch cat
git checkout cat
```
### shortcut
`git checkout -b cat`

### Merge branch into master. If nothing has happened in the master branch since. Git will "fast-forward" the HEAD pointer.
```
git checkout master
git merge cat
```

### If there **were** changes that happened in master since. Git will do a recursive merge and create a log message that branch have been merged in.

### We can choose to do a rebase instead. Refer to rebase section below first.
### This will allow cat branch to have all the commit in master since, and then have our commit in the cat branch.
### When we merge in master branch, it will be a smooth fast forward instead of a merge commit
`
git checkout cat
git rebase master
git checkout master
git merge cat
`

## Scenarios

### Colleague committed first, no conflicts.
### git pull does a `git fetch` which creates an origin/master branch and then a `git merge origin/master`
```
git pull
git push
```
### Colleague committed first and touched the same file
### git pull will fail to merge. we edit the affected file and then `git commit -a`
```
git pull
```
### Collaborating on a remote branch. If work is going to last several days you will want to push it to Github and start tracking it.
```
git checkout -b shopping_cart
git push origin shopping_cart
```

## Tag
### List all
`git tag`

### Checkout a tag
`git checkout v0.0.1`

### Add a tag
`git tag -a v0.0.3 -m "version 0.0.3"`

### Push to remote
`git push --tags`


## Rebase
### Fetch all latest change from remote into local branch origin/master
`git fetch`
### `git rebase` will
1. Move all changes which are in master but not in origin/master to a temporary area
2. Run all origin/master commits one at a time
3. Run all commits in the temporary area one at a time
`git rebase`
### If there were conflicts resolve the conflicts by editing the affected files
```
git add index.html
git rebase --continue
```

## Viewing logs
### `git config --global color.ui true` will emphasize the SHA hash
### `git log --pretty=oneline` for one liner easy viewing
### `git log --oneline -p` for more details on each commit
### `git log --oneline --graph` for visuals on when merge happened
### `git diff HEAD~5` for difference between current state and 5 commits ago
### `git diff master cat` for difference between branches
### `git blame index.html --date short`
### use aliases for all these tricky commands
`git config --global alias.mylog "log --pretty=format:'%h %s [%an]' --graph"`
