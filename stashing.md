# Stashing

:speech_balloon: Scenario: when we've made some changes and are not ready to commit the changes; However, we are informed to change the gears to make some hot fixes for urgent reason. In order to save the changes that are currently in progress

```bash
# stash current works
$ git stash

# load the latest stash
$ git stash apply

# list all the stash
$ git stash list

# drop the latest stash
$ git stash drop
```

Since `git stash` only stashes tracked files by default, we can add `-u` parameter to stash untracked files, too

```bash
# also stash untracked files
$ git stash -u
```

Execute `$ git stash apply` and `$ git stash drop` at the same time

```bash
$ git stash pop
```

### Manage multiple stashes

:mag: Be careful that the stashes are stored in reverse order

```bash
# stash with messages
$ git stash save 'simple changes'

# show the diff
$ git stash show stash@{1}

# apply the specific stash and drop
$ git stash apply stash@{1}
$ git stash drop stash@{1}

# empty all the stashes
$ git stash clear
```

### Stash into a branch

```bash
# create newBranch branch and switch to it, and then pop the latest stash
$ git stash branch newBranch
```
