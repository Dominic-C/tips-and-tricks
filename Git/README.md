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

# Committing

## Amending commits

### Amending commit names
Lets say you have a latest commit with a BAD COMMIT NAME, and we want to change it

we can run:
```
$ git commit --amend -m "Amended commit message"
```

Note: commit hash changes with this command, because commit hashes takes into account commit names.

### Amending commit contents
with the --amend option in git commit, we can also add files to our last commit

For instance, if we wanted to add `BomoSort.py` into our last commit but forgot to, we can do the following
```
$ git add Bomosort.py
$ git commit --amend
```

# Pull
-- insert standard code for pull --

An alternative to git pull which many git aficianados use is a git fetch followed by a merge. This is effectively the same thing as a pull.

# Push

# Cherry pick

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
$ git cherry-pick 1bghe2632
```


# Resources
* [Intro to git core concepts](https://www.youtube.com/watch?v=uR6G2v_WsRA)
* [Branching and Merging](https://www.youtube.com/watch?v=FyAAIHHClqI)
