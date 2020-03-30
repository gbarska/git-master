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

## git init .
 
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

### git checkout

Discard canges entirely and restore to the last status as the repository

```
git checkout --README.md
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

### git diff 

Shows diference between two commits 

```
git diff 

or

git diff d444e90 HEAD
```

ps: HEAD -> last commit at current branch

