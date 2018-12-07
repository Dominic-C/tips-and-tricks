# Initializing a git repository
Creating a github repository with an existing project folder.

```
$ git init
$ git add .
$ git commit -m "Initial commit"
$ git remote add origin <remote repository URL> # note, if you have errors with the ssh url, make sure you generate an SSH key for your device
$ git remote -v # verifies the remote (have not tried this before)
$ git push origin master
```
# Individual file management
This portion is about individiual file management in the git management system

## Undoing changes before a commit
Let's say i have a file called `file1.py`, I have made some changes to it but it doesnt work. So i want to reset to the previous commit. I can simply run:
```
$ git checkout file1.py
```

note: to check the differences between two files, i can run `git diff`


# Branching
Creating a branch from an existing branch. First you have to switch to the branch you wish to branch from. Then make a branch from there.

For instance, say i have a branch `testing`, and i want to create a branch `testing_2`. We can do the following
```
$ git checkout testing
$ git checkout -b testing_2 testing
```

# Git Commit
my usual workflow is to do a `git commit -m "<Commit description>"` when i have single line commit headings or a `git commit` when I have a couple of lines i wish to write in the commit

Some people do a `git commit -am "<commit description>"` which stages all changed files and commits them in a single line, but has less fine control on the staging area.

**flags**
-m: Message
-a: all. This tells git to automatically stage all files that have been modified and deleted, but new files are not affected (git does'nt know unless you tell it)

## Amending commits

### Amending commit names
Lets say you have a latest commit with a BAD COMMIT NAME, and we want to change it

we can run:
```
$ git commit --amend -m "Amended commit message"
```

**Note:** commit hash changes with this command, because commit hashes takes into account commit names.
Chaning the commit hash results in changing its git history. We should only do this when the commits are local and are not pushed to any shared repository.

### Amending commit contents
with the --amend option in git commit, we can also add files to our last commit

For instance, if we wanted to add `BomoSort.py` into our last commit but forgot to, we can do the following
```
$ git add Bomosort.py
$ git commit --amend
```
**Note:** commit hash changes with this command, because commit hashes takes into account commit names.
Chaning the commit hash results in changing its git history. We should only do this when the commits are local and are not pushed to any shared repository.

# Git Pull
the general format for git pull is `$ git pull <options> <repository>`, if nothing is specified, it fetches and updates all branches existing in the remote repository.

An alternative to git pull which many git aficianados use is a `git fetch` followed by a `git merge`. This is effectively the same thing as a `git pull`, but better practice.

`git fetch` fetches the latest versions of files pushed to the repository but doesnt merge them to your local sandbox. This means you can view the checkout what your colleagues have pushed without merging their files into your local sandbox.

# Git Push

# Cherry Pick


# Git Stash
What git stash does is put all your unstaged and uncommitted changes into deltas (differences between two files) and store them into a stash. Then it removes those differences from your working copy and reverts it back to the last committed version.

To do a git stash, we can simply run
```
$ git stash
OR
$ git stash save "message that describes the stash"
```
To view the stash, we can run
```
$ git stash list
```

To reapply the stash, we can run
```
$ git stash apply <stash name, typically "stash@{0}"> # note, this applies only single stashes and does not remove them from the stash list
OR
$ git stash pop # applies stash and removes it from stash list
```

If you need to clear the stash, you can run
```
$ git stash clear
```

# Fixing Huge Messes

## You have been committing to the wrong branch
For instance, let's say you have been committing to `master` branch by accident for one commit.

What we are are going to do is switch to the intended branch(lets say `prototypeBr`), grab those commits, switch back to the master branch and remove those commits.

1. Copy the first 6-7 digits in the commit hash
```
$ git log
# then copy the first few characters of the commit hash
```
2. Switch to branch `prototypeBr` and do a cherry pick
```
$ git checkout prototypeBr
$ git cherry-pick 1bghe2632 # where 1bghe2632 was the commit hash
```
3. Now that we have the commits in our new branch, we can remove the commits from the master branch. We do this by making a reset on the master branch. 

There are 3 types of resets we should know about, use any one of these depending on the situation.
* Soft reset:`git reset --soft <hash of commit to roll back to>`. This rolls back the commit specified, but keeps changes in staging area (no loss of work)
* Mixed reset, which is the default: `git reset <hash to roll back to>`. This rolls back the commits, but changes are kept in the working directory.
* Hard reset: `git reset --hard <hash to roll back to>`. Rolls back to the commit, deletes all changes to **tracked files** after this hash in your working directory. Leaves any untracked files alone. i.e. does not touch files that were not introduced to git by git add and git commit.

If you really wanted to get a clean workspace and remove all untracked files, you can do a `git clean -df`. `-d` get rids of any untracked directories while `-f` gets rid of any untracked files. (this will be good if you accidentally unzipped a file and added it to the staging area)

# Adding files to .gitignore after they have been in your repo for several commits
Updating your .gitignore is only useful if you have new files you want to ignore and have not committed yet. To ignore already committed files, we can do the following:

```
$ git rm -r --cached .
$ git add .
$ git commit -m "Clean up ignored files"
```

# Reverting merge
```
$ git revert -m 1 dd8d6f587fa24327d5f5afd6fa8c3e604189c8d4>
```

# Resolving a merge conflict by keeping incoming changes instead of your own
```
$ git checkout --theirs <file name>
# followed by
$ git add <filename>
```

# Merging one branch into another
1. checkout the branch you wanna merge into
2. `git merge branchname`

# Creating another branch from a commit
if you checkout a commit, you will be known to be in a state known as the Detached HEAD. To make a new branch from the detached HEAD state, you can do the following.

1. `git checkout <SHA>`
2. `git branch new-branch`
3. `git checkout new-branch`

# Resources
* [Intro to git core concepts](https://www.youtube.com/watch?v=uR6G2v_WsRA)
* [Branching and Merging](https://www.youtube.com/watch?v=FyAAIHHClqI)
* [Fixing common mistakes and undoing bad commits](https://www.youtube.com/watch?v=FdZecVxzJbk&t=596s)