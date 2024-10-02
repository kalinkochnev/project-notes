# Remotes
## Adding remote repository
`git remote add origin https://github.com/VijayNew/NewExample.git`

## Set upstream branch
`git branch --set-upstream-to <remote-branch>`

Shorthand to use -u while pushing
`git push -u origin local-branch`

# Branches
## Delete branch
```
git branch -d  local_branch_name
```
## Create branch from another branch
https://stackoverflow.com/a/4470822
```
git checkout -b myFeature dev
```

## Compare file across two branches
https://stackoverflow.com/a/4099805

File path is relative.
```
git diff mybranch master -- myfile.cs
```

## Create branch from old commit
`git checkout -b NEW_BRANCH_NAME COMMIT_ID


# Submodules
## Rebuild the git submodule/Restore to last commit
`git submodule update`

## Remove a git submodule
1. Run `git rm <path to submodule>`
2. Cd to the directory /.git/modules/
3. Remove the submodule folder
# Commits
## Revert commit and put back to stage
 [How to revert a commit and put changes back to stage](https://stackoverflow.com/questions/59010582/how-to-revert-a-commit-and-put-changes-back-to-stage)

```
git reset HEAD^
```
HEAD^ means the previous commit.

## Amend commit
If a fix isn't changing code behavior, but perhaps just renaming the commit message do ... to fix the last commit.
```
git commit --amend
```

## List commits
`git log`
## Remove folder from all commits
https://stackoverflow.com/a/61544937
```bash
git-filter-repo --path dir --invert-paths
```



## Create empty commit
`git commit --allow-empty -am 'empty commit'`

## Squashing
You can combine all of your commits on one branch by squashing. And then you can merge that one branch as a single commit.

```
git checkout master
git merge --squash bugfix
git commit // omitting -m allows you to manually resolve conflicts and then set a message
```




# Rebase
https://git-scm.com/book/en/v2/Git-Branching-Rebasing

Git rebase is used to create a linear history instead of multiple "timelines". 

![[rebase diagram.svg]]

`git rebase` takes all the changes committed on one branch and replays them onto a different branch. 

1) Checkout the feature branch
2) Rebase (aka replay) it onto the master branch
3) You are still on the feature branch, so you need to go back to the master branch and merge your rebase

## Use cases
- You have a `client` and a `server` branch. And the `client` depends on some of the work on `server`
![[rebase 1.png]]
You can "replay" the changes of `client` onto master without relying on `server`.

```
git rebase --onto master server client
```

*“Take the `client` branch, figure out the patches since it diverged from the `server` branch, and replay these patches in the `client` branch as if it was based directly off the `master` branch instead.”*
![[rebase 2.png]]
## Important!
**DO NOT rebase commits outside your local repository and people may have worked on.**

# Best Practices
https://gist.github.com/luismts/495d982e8c5b1a0ced4a57cf3d93cf60
