# Git

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

### Stage files
```
git add README.md
git add -A
```
### Unstage files. HEAD refers to last commit on the current branch/timeline you are currently on.
`git reset HEAD <file>`

### Reset changes
`git checkout README.md`

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

### View current remotes
`git remote-v`

### Push to Github. **origin** is remote name, **master** is the current branch you are trying to push
`git push -u origin master`
