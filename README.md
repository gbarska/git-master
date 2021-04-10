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

### Mapping existing folder to remote

$ git remote add origin remote repository URL
# Sets the new remote

$ git remote -v
# Verifies the new remote URL


### rm -rf .git

Removes git files 

### git init
 
Initializes git  on existing project folder

### git log 

Logs all commits that are part of a Repository

https://devhints.io/git-log

### git show

Display the commit changes along with the diffs

### git ls-files

List all files tracked by the repository so far

## Backing Out changes

### git reset HEAD
Discard canges entirely and restore to the last status as the repository

```
git reset HEAD~1
```

Backs out commited changes to the staging area but keep the modifications on the working directory

### git checkout

```
git checkout --README.md
```

## Git ignore

### .gitgnore

In order to ignore unwanted files we should create a file called .gitignore with predefined files and folders that 
should be ignored.


PS: !IMPORTANT

To remove files or folders that have already been tracked and/or pushed :


git rm --cached nameoffolder
git rm --cached nameoffile


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

## git Branches

### git branch

List current branch

### create new branch with checkou command

Creates a new branch called updates based on master 

```
git checkout -b updates
```

### git pull

Synchronize local workspace with remote, only consider current branch

```
git pull
```

In order to consider all branches, at the remote should add --all
Ex: if we need to synchronize our local workspace that is pointin to master
with the development branch

```
git pull --all
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

### remove branch locally

git branch -d name_of_branch


### remove branch remote

git push origin :nome_branch


## GIT TAGGING

### git tag tagname

### git tag -d tagname

### git tag -a v1.0 -m "Release 1.0" commit_id

Adds optional comment and version, useful to create a baseline 


### git push --force origin tag_name

Forces git remote repository to update the tag with the changes made locally


### git tag update commit id 

updates the commit associated with the tag to other commit:
git tag -f name_of_tag other_commit_id 


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

### Rebase

When remote repository contains changes ahead of your local repository and you want your "version"
of code to be AHEAD of any other changes without having to MERGE, we can use the rebase option


git commit -am "updating local changes to be ahead of remote"

git fetch 

git pull --rebase

git push


## GIT FORK & SOCIAL

While working with social repositories or Fork content, sometimes we need to update our copy of 
the repository, ( the remote repo that was forked from the original repo) in this case:

Show all remote urls :

```
git remote -v 
```

When we clone our forked repo our local repository will be pointing to our remote copy of the code
to point to the original repository we must add the original repo's url as a source:

```
git remote add nome_do_repo_alternativo url_repo_alternativo

ex:
git remote add upstream git@github.com/opensourcedev/opensource-proj.git
```

Now we can update our local repo:

```
git pull upstream master
```

and push the code to our remote repository's copy:

```
git push origin master
```

##
Git setup ssh 
https://dev.to/bdbch/setting-up-ssh-and-git-on-windows-10-2khk

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

then open git-bash -> cd userfolder/.ssh/
type: cat id_rsa.pub

copy output and paste in Github


## GITHUB SUBMODULES - PAGES

[GitHub Pages](https://pages.github.com/) is great for building a personal or project website. It'll default to _http://username.github.io_, or you can even [use your own custom domain name](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/) from services like [Namecheap](https://www.namecheap.com/), which I will write about in another post soon.

So you set up your GitHub Page for yourself or project, but what if you want to show off some of your other projects you are working on. You can go the poor man's route, and simply just copy everything from another repository into a folder in your _username.github.io_ repository, commit and push the changes to GitHub, and you'll be able to navigate to _http://username.github.io/project_.

But this comes with some seriously inconvienent and non-conventional drawbacks, such as duplication of code across repositories and manually copy/paste-ing everytime changes are made to update your hosted codebase. Good luck maintaining that.

The other, more elegant solution is to use [Git Submodules](http://www.git-scm.com/book/en/v2/Git-Tools-Submodules). These will allow us to pull in other repositories and have them sit as a "repository within a repository" [cue _Inception_ sound effect](http://inception.davepedu.com/noflash.php).

The process is as follows:

1. Via the command line, navigate to your repository
  
  `cd path/to/your/repository.github.io`

2. Add a submodule
  
  `git submodule add https://github.com/username/otherrepository`
    
    note: It must be the `https://` address

3. Add/commit your new files
  
  `git add .gitmodules`
  
  `git add otherrepository/`
  
  `git commit -m "Added otherrepository submodule"`

4. Push your changes
  
  `git push origin master`

5. navigate to _http://username.github.io/otherrepository_

Now if you start making changes to your other repository, you'll need to update your GitHub Pages repository to reflect those changes:

1. Via the command line, navigate to your GitHub Pages repository
  
  `cd path/to/your/repository.github.io`

2. Navigate into your submodule
  
  `cd otherrepository/`

3. Pull from you master

  `git pull origin master`
  
4. Navigate back up to your GitHub Pages repository

  `cd ..`

5. Add/commit your updated files
  
  `git add .gitmodules`
  
  `git add otherrepository/`
  
  `git commit -m "Updated otherrepository submodule"`

6. Push your changes
  
  `git push origin master`

And now your changes should be reflected online.



## UPDATING GIT SUBMODULES

`git submodule foreach git pull origin`
