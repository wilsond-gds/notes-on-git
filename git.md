# Learning Git 

## Definitions

Git is a distributed system so everyone using the git repo has the ability to check in where they are and everyone else knows what’s been happening in the repo. You can also download the entire repository to work on it individually.

We are aiming for ‘atomic commits’ with meaningful commit messages.

The **working directory** is in sync with your local file system and it knows when you’ve made any changes. Your **staging index** is like a point on the end of your git commit history. Your **commit history** is the list of commits you’ve made.

* `repository` your project folder
* `commit` save a snapshot
* `hash` a computer generated ID
* `checkout` time travel to a specific commit
* `branches` separate versions of your code, or a moveable label that points to a commit
* `merge` the combination of two or more branches
* `remote` a computer with a repo on it
* `clone` get the repo from the remote for the first time
* `push` get new commits to the repo from the remote
* `pull` send your new commits to the remote

These terms are defined in [**git for humans** (video)](https://www.youtube.com/watch?v=eWxxfttcMts&t=1s). See also [**getting more from git** (video)](https://www.youtube.com/watch?v=FQ4IdcrOUz0).

Writing good commit message is hard but useful, as it requires you to really understand the code base, what you’ve changed, and why it’s a good change. It also helps other people answer the same questions.

## Start with these commands

* Create a git managed folder `git init`
* Pull from a remote repository `git pull https://github.com/wilsond-gds/vsc-learn.git`
* Check status `git status`
* Which branch am I on? `git rev-parse --abbrev-ref HEAD`

## Create a branch

* Create a branch and switch to it `git checkout -b branch-name`
* Or longer form, `git branch branch-name`, `git checkout branch-name`

## Staging commits

Stage commits (get them ready to become part of the official repo) by doing `git add`. `git add --patch` will ask you which bits of a file you want to add. These bits are called `hunks`.

## Finished with branch, won't merge

* `git stash` puts files away
* `git stash list` tells you what you've put away
* `git checkout master` to return to master

## Playing around with the code and just want to go back to a clean state

* `git reset --hard`
* `git pull [https path to repo] main`

## See changes to a file

* `git diff path/to/file`

## copy a file from one branch to another

* `git fetch`
* `git checkout -m master [path to file]`
* `git add [path to file]`
* `git commit`


## Create pull request

**Remember** when creating multiple pull requests, always `git checkout` back to the main branch before creating another branch for the next pull request.

## Rebase and merge

Reset the git history to a particular point in your work history
* `[branch][folder]$ git reset --hard origin/[folder]`  
* `HEAD is now at [hash] [commit message]`

Rebase to remove commits that aren't required - change `pick` to `drop`
* `$ git rebase -i HEAD~2`

Force push to override the tracking in github
* `$ git push --force`

Forgotten to sign the commit? 
* First, amend the commit to sign it
* `$ git commit --amend --no-edit -S`
* Then force push again to override the tracking in github
* `$ git push --force`

## Amending small changes in your history

```
git add --patch
git commit --amend
git reset [sha]
```

[View the video section](https://youtu.be/FQ4IdcrOUz0?t=1463) explaining these commands. 

* See above for `git add --patch`. 
* `git commit --amend` lets you amend your last commit. 
* `git reset` is almost the opposite of `git add` and `git commit` but it’s not exactly the same. Find the `SHA` of the commit and then do `git reset sha` to go back to the state of the repo at that commit. `git reset sha --hard` will go back and forget everything before that point.

## Making big changes in your git history

* `git rebase` [video section](https://youtu.be/FQ4IdcrOUz0?t=1866) allows you to access more tools that can change your git history. **Only use rebasing on local unpublished branches**.
* `git rebase --abort` reduces surprises in the process of rebasing.
* `git rebase --interactive` gives you an interactive list of changes to your repo. 
* `git show -b` will show the difference between two commits.

## commands to attempt to understand fully

* `git checkout` and related flows
* `git rebase` and related flows
* `git stash pop` and `git stash apply`
* `git log --show-signature`
* `git push +[branch-name]` to override local changes

## Vim commands related to working with git

* `:cq` clears and quits
* `:q` runs commands
* `:wq` writes and runs commands
