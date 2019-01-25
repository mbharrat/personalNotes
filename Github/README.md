# Github Cheatsheet

---
## Git Configuration
To set your username

```sh
$git config --global user.name <Your Name>
```

To set your email
```sh
$git config --global user.email <email>
```

Check the configurations

```sh
$git config <option>
```
options could be user.name, or user.email

## Basic Git Commands

Create a new repo
```sh
$git init
```

Check the status of git files (basically see which files are staged)
```sh
$git status
```

Adds specific files to staging

```sh
$git add <name of file>
```

To add them all

```sh
$git add .
```
Pull from remote branch and overwrite local changes

```sh
$git fetch --all
$git reset --hard origin/<name of branch>
```

Remove file from staging
```sh
$git rm --cached <fileName>
```

Commit file with message
```sh
$git commit -m "My message"
```
Doing just git commit wil open up vim for longer messages

Shows commit log
```sh
$git log
```

Shows just subject of git commits
```sh
$git log --oneline
```
Show difference between master and remote branch
```sh
git diff <masterbranch_path> <remote_path>
```
Remove last commit
```sh
$git reset HEAD^
```
Remove git tracking from project
```sh
$rm -rf .git
```

## Remote Repo Commands

Clone repo into current directory
```sh
$git clone
```

Connect local repo to remote
```sh
$git remote add <name of file>
```
Get files from remote repo
```sh
$git pull
```
Upload and update changes to remote repo (must set upstream origin...if not set github will tell you how)
```sh
$git push -u origin
```
Go back on a commit
```sh
$git reset HEAD~
```

## Git Branching
### What is a git branch?
*An independant line of development*

List all the branches in a repo
```sh
$git branch
```

Create a new branch
```sh
$git branch <nameOfBranch>
```

Safely delete a local branch
```sh
$git branch -d <nameOfBranch>
```

Force delete a branch

```sh
$git branch -D <nameOfBranch>
```

Rename current branch
```sh
$git branch -m <newName>
```

## Git Checkout
### What is it?
*Navigate between branches*

Switches over to branch
```sh
$git checkout <existingBranch>
```

Create a new branch and checkout
```sh
$git checkout -b <newBranch>
```
Overwrite changes and checkout current branch!!! (USEFUL)
```sh
$git checkout .
```
Reverts most recent commit
```sh
$git revert HEAD
```

## Git Merge

Merge master/dev in local branch
```sh
$git checkout dev-A
$git merge dev-B
```

## Steps for editing on new branch
1. Make Branch
2. Checkout Branch
3. Do work in that branch
4. ```$git add .```
5. commit changes
6. Switch to master
7. Merge, ```git merge <branch>```
8. Push to master
9. Delete branch

## Steps for initializing exisiting repo
1. ```git init```
2. ```git add .```
3. ```git commit -m "First Commit"```
4. ```git remote add origin <githubURL>```
5. ```git push -u origin master```





