# Basic Commands

Git basics 

## Initial changes

### git status

Displays repository status

### git add

Adds files to the staging area

### git commit -m "First file in demo repo"

Commit changes with -m message

### git commit -am "First file in demo repo"

Adds all modified files to the staging area and  Commits changes with -m message 

similar to git add . + git commit -m


### rm -rf .git

Removes git files 

### git init
 
Initializes git  on existing project folder

### git log 

Logs all commits that are part of a Repository

### git show

Display the commit changes along with the diffs

### git ls-files

List all files tracked by the repository so far

## Backing Out changes

### git reset HEAD

Backs out commited changes to the staging area but keep the modifications on the working directory

### git checkout

Discard canges entirely and restore to the last status as the repository

```
git checkout --README.md
```


## Git Alias

### git config

Creates alias for specified git commands && parameters

```
git config --global alias.hist "log --oneline --graph --decorate --all"
```

Hint: list all configs created:

```
git config --global --list
```
 
## Removing and renaming files


### git mv 

Renames (moves*) files

```
git mv example.txt demo.txt 

git commit -m "renaming file"
```

The file name would be changed even though it was renamed after the  git add command

### git rm

Removes the staged file and tracks the change


Ps: if files were modified outside git (without git mv or git rm ) then git will miss that real change, ex:

mv example.txt newname.txt 

git status > git would consider example as deleted and newname as a new file 

to fix:

git add -A 

## git diff 

Shows diference between two commits or branches 

```
git diff 

or

git diff d444e90 HEAD

or 

git diff updates master
```

ps: HEAD -> last commit at current branch

## git branch

### git branch

List current branch

### create new branch with checkou command

Creates a new branch called updates based on master 

```
git checkout -b updates
```


### git checkout

Switches the current branch 

```
git checkout master
```


### git fetch

The git fetch command downloads commits, files, and refs from a remote repository into your local repo.

```
git fetch
```

ps:  it doesn’t force you to actually merge the changes into your repository. 


look at the remote repository for dead branches and removes reference if any, very useful after 

git branch -d 

```
git fetch -P  

```

### git merge

Merge branches to the master when master has no change pending compared to child branches

### remove branch

git branch -d name_of_branch

## GIT TAGGING

### git tag tagname

### git tag -d tagname

### git tag -a v1.0 -m "Release 1.0"

Adds optional comment and version, useful to create a baseline 


## SAVING WORK IN PROGRESS WITH STASH

### git stash 

useful when you need to modidy something with urgency that might be fixed or added prior
to the work that have been in progress, this way you can save the progresse and upload 
new changes and after that continue your work

### git stash list

### git stash pop 

get the work progress back and  removes it's entry from the stash list

## Time trave with reset and reflog

### git reset c22s2si2 (commit id) --soft

change the HEAD's position but keep all the changes made after the commit id choosed

Preserves: staging area and workspace

### git reset c22s2si2 (commit id) --mixed (*default option)

change the HEAD's position including the stages made after the commit id but all modifications go 
to workspace

Preserves workspace but reset stages made after the commit id

### git reflog 

shows all commit ids along with actions made 

useful to list all actions done so far and choose the commit id to travel with git reset


## SSH authentication

### generate key

```
gbarska@br:~/.ssh$ ssh-keygen -t rsa -C "email@domain.com"
```

### test ssh access

```
ssh -T git@github.com
```
### cloning repo

<!-- go to github repository, click on copy URL button  change authentication method to ssh -->

git clone git@github.com:gbarska/repository_name


## Updating references (after renaming repositories)

### git remote 

List references:

```
git remote -v 
```

Set url:

```
git remote set-url origin git@github.com:gbarska/nome_do_repo

```

Show detailed info for the reference:

git remote show origin

