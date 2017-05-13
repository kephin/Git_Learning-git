# Rebasing

### :wrench: Rebase other bransh

:speech_balloon: Scenario: we are currently on the feature / bug branch, if we want to incorporate any changes that have happened on master, we will need to rebase the master

```bash
# on the branch that we want to rebase into, say featureBranch
# the source branch we want to rebate is the master branch
$ git rebase master

# after rebase, we then switch to master and merge the featureBranch
$ git checkout master
$ git merge newFeature
$ git branch -d newFeature
```

If we encounter a conflict, we can abort the process, and then deal with it manually

```bash
$ git rebase --abort
```

Or we can use the merge tool to handle

```bash
$ git mergetool

# after dealing with the conflict we can continue on the rebase
$ git rebase --continue
```

### :nut_and_bolt: Pull with rebase from GitHub

:speech_balloon: Scenario: if we want to rebase the changes on remote

Before the operation, it's always recommended to synchronize the reference on GitHub, and then see the logs first

```bash
# fetch is a non-destructive command that simply updates the reference between remote and local
$ git fetch origin master

# see the logs
$ git log --all --oneline --graph --decorate
```

To keep the local commits ahead of the commits on GitHub, in order that we can benefit from the changes on GitHub

```bash
$ git pull --rebase origin master

# on the other hand, we can merge it by git pull
$ git pull origin master

# which is equal to
$ git fetch origin mater
$ git merge origin/master
```
