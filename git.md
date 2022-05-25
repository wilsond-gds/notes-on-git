# Learning Git 

## Definitions

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

These terms are defined in [**git for humans** (video)](https://www.youtube.com/watch?v=eWxxfttcMts&t=1s)


## Start with these commands

* Create a git managed folder `git init`
* Pull from a remote repository `git pull https://github.com/wilsond-gds/vsc-learn.git`
* Check status `git status`

## Create a branch

* Create a branch and switch to it `git checkout -b branch-name`
* Or longer form, `git branch branch-name`, `git checkout branch-name`

## Finished with branch, won't merge

* `git stash` puts files away
* `git stash list` tells you what you've put away
* `git checkout master` to return to master

## Playing around with the code and just want to go back to a clean state

* `git reset --hard`
* `git pull https://github.com/alphagov/di-ipv-core-front.git main`

## See changes to a file

* `git diff path/to/file`

## copy a file from one branch to another

* `git fetch`
* `git checkout -m master ~/core-front/src/app/oauth2/middleware.test.js`
* `git add ~/core-front/src/app/oauth2/middleware.test.js`
* `git commit`


## Create pull request

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