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

## Stage
### Stage files
```
git add README.md
git add -A
```
### Unstage files. HEAD refers to last commit on the current branch/timeline you are currently on.
`git reset HEAD <file>`

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
