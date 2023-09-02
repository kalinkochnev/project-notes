
## Revert commit and put back to stage
 [How to revert a commit and put changes back to stage](https://stackoverflow.com/questions/59010582/how-to-revert-a-commit-and-put-changes-back-to-stage)

```
git reset HEAD^
```
HEAD^ means the previous commit.

## Remove a git submodule
1. Run `git rm <path to submodule>`
2. Cd to the directory /.git/modules/
3. Remove the submodule folder

## Rebuild the git submodule/Restore to last commit
`git submodule update`

## List commits
`git log`

## Adding remote repository
`git remote add origin https://github.com/VijayNew/NewExample.git`
`
## Set upstream branch
`git branch --set-upstream-to <remote-branch>`

Shorthand to use -u while pushing
`git push -u origin local-branch`

# Remove folder from all commits
https://stackoverflow.com/a/61544937
```bash
git-filter-repo --path dir --invert-paths
```

# Delete branch
```
git branch -d  local_branch_name
```

# Create branch from another branch
https://stackoverflow.com/a/4470822
```
git checkout -b myFeature dev
```

# Create empty commit
`git commit --allow-empty -am 'empty commit'`

# Create branch from old commit
`git checkout -b NEW_BRANCH_NAME COMMIT_ID

# Create new repository from commit of other repository

# Add remote repository
```
git remote add origin git@github.com:kalinkochnev/project-notes.git

git push -u -f origin main
```
`-u/--set-upstream` sets push/pull for future actions
`-f` overwrites everything in remote