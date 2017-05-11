# Branching and Merging

### :seedling: Branching

Branching basics

```bash
# list all the local branches
$ git branch

# -a will list both local and the remote branches
$ git branch -a

# create a new branch
$ git branch myNewBranch

# switch to another branch
$ git checkout myNewBranch

# create and switch to the new branch at the same time
$ git checkout -b newFeature

# rename the branch
$ git branch -m myNewBranch newBranch

# delete the branch (we can't delete the branch we're currently on)
$ git branch -d newBranch
```

### :twisted_rightwards_arrows: Merging

:mag: **Fast forward merges**: will place all the commits on the master branch as we never branched away. Fast forward merge is only possible when there are no changes being made on the target branch

```bash
# switch to the master first
$ git checkout master

# before any merge, we should know what the differences are
$ git difftool master newFeature

# will merge the name of the source branch into my current branch
$ git merge newFeature
```

After the merge, the newFeature branch is no longer needed, so we can delete it by

```bash
$ git branch -d newFeature
```

:mag: **Disable fast forward merges**: will preserve the fact that we've branched off, we need to give it the commit message because it will create a new commit

```bash
# will auto-merge and prompt default editor for commit message
$ git merge newFeature --no-ff

# or you could use -m
$ git merge newFeature --no-ff -m "merge branch 'newFeature'"
$ git branch -d newFeature # don't forget to remove the branch
```

:mag: **Automatic merge**: if there are commits in both master and other new branches, and there is no conflict

```bash
# will auto-merge and prompt default editor for commit message
$ git merge newFeature

# or you could use -m
$ git merge newFeature -m "merge branch 'newFeature'"
$ git branch -d newFeature # don't forget to remove the branch
```

:collision: **Conflict merge**: if we did changes in the same file and the same area, it will result a conflict

```bash
# review the difference before merging
$ git difftool master newFearure

# will cause the conflict and lead you to the merging state
$ git merge newFearure

# open merge tool to deal with the conflict
$ git mergetool

# commit the merge
$ git commit -am "merge branch 'newFeature'"
```
