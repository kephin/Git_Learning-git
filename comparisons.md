# Comparisons

### :computer: Install and config merge / diff Tool

:arrow_down: Installation

```bash
# installation
$ sudo apt-get update
$ sudo apt-get install meld

# open meld
$ meld

# find meld path
$ which meld  # will returns /usr/bin/meld
```

Config: set up diff / merge tool to git

```bash
# difftool
$ git config --global diff.tool meld
$ git config --global difftool.meld.path /usr/bin/meld
$ git config --global difftool.prompt false

# mergetool
$ git config --global merge.tool meld
$ git config --global mergetool.meld.path /usr/bin/meld
$ git config --global mergetool.prompt false
```

Or you can open .gitconfig file through editor

```bash
$ git config --global -e
```

### :rocket: Operation

```bash
# view the difference in the terminal
$ git diff

# open difftool, ie. meld
$ git difftool
```

### :book: Comparisons

:fire: Compare working directory and the staging area

```bash
$ git diff -- app.js
$ git difftool -- app.js
```

Compare working directory and Git repository(last commit)

```bash
$ git diff HEAD -- app.js
$ git difftool HEAD -- app.js
```

Compare between staging area and the Git repository(last commit)

```bash
$ git diff --staged HEAD -- app.js
$ git difftool --staged HEAD -- app.js
```

Compare between commits, the order should be the prior one and the latter one

```bash
# compare the last commit and the one just prior to the last commit
$ git diff @^ @
# difftool will compare one file at a time, and cycle through
$ git difftool @^ @
```

Compare between local and remote master branches

```bash
$ git difftool master origin/master
```
