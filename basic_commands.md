# Git settings and basic commands

### Default config

Config settings

```bash
# list all configs:
$ git config --global -l
# or git config --global --list
$ git config --local -l

# put user info. globally:
$ git config --global user.name 'kephin'
$ git config --global user.email 'wunshon76325@gmail.com'

# set sublime the default editor
# Lunix
$ git config --global core.editor 'subl -n -w'
# Windows
$ git config --global core.editor '"E:/Sublime Text 3/sublime_text.exe" -n -w'

# to check or edit
$ git config --global -e
# or
$ subl ~/.gitconfig

# remove config:
$ git config --global --unset user.name
```

Add alias
  
```bash
# add alias
$ git config --global alias.hist 'log --all --graph --decorate --oneline'
# now we can use `git hist` to review history logs

# edit alias
$ subl ~/.gitconfig

# remove alias
$ git config --global --unset alias.hist
```

### .gitignore

  ```bash
  # ignored by folder
  node_modules/

  # ignored by patterns matching: to ignore all txt files
  *.txt

  # except for note.txt
  !note.txt
  ```

### Manage commits

Modify commit，use **--amend**

```bash
$ git commit --amend -m 'new commitments'
```

Recovery from `git add`

  ```bash
  # if the file did not commit before
  $ git rm --cached YOUR_FILE_NAME
  # if the file has committed before
  $ git reset HEAD YOUR_FILE_NAME
  ```

View commit nodes
  1. Show commits history

  ```bash
  $ git gitk
  $ git log --graph --oneline --decorate --since='3 days ago'

  # for specific file
  $ git log -- index.js

  # for specific file that has renamed
  $ git log --follow -- index.js
  ```
  2. Show information about specific commit

  ```bash
  # show the newest commit
  $ git show HEAD

  # show the first parent commit in master
  $ git show HEAD~1
  # or
  $ git show HEAD^1

  # show the first parent in branch
  $ git show HEAD^2

  # use @ to replace HEAD
  $ git show @
  ```

If you want to view the difference for a certain file between commits

  ```bash
  $ git show YOUR_FILE_NAME
  $ git show @~1:YOUR_FILE_NAME
  ```

### Compare files and check out

1. Compare

  ```bash

  ```
2. Check out files from local repo

  ```bash
  # take out certain files for certain version
  $ git checkout @ YOUR_FILE_NAME_1 YOUR_FILE_NAME_2 ..
  # take out all files from the latest repo
  $ git checkout .
  ```
3. Find strings in files with certain version of local repo

  ```bash
  $ git grep 'strings' @

  # add a number of how many lines are with 'strings'
  $ git grep -c 'strings' @
  # ignore capital or lower case
  $ git grep -i 'strings' @
  # only thow files
  $ git grep -l 'strings' @
  ```
4. Find who edit the repo in

  ```bash
  $ git blame YOUR_FILE_NAME

  # start with line 3 to the end
  $ git blame -L 3, YOUR_FILE_NAME
  # from beginning to line 2
  $ git blame -L ,2 YOUR_FILE_NAME
  # from line 2 to line 3
  $ git blame -L 2,3 YOUR_FILE_NAME
  ```
5. Change file name or folder name

  ```bash
  $ git mv OLD_FILE_NAME NEW_FILE_NAME

  ```
6. 暫存
7. Clear repo

  ```bash
  $ git gc
  ```


### Git completed

1. Always `git push origin master` before `git push origin master`. `git pull` will update our repository with any changes that may have happened on the remote repository down to our local repository. Just to make sure we're up-to-date before we do any push back up to out remote repository.

2. Show all the tracked files

  ```bash
  $ git ls-files
  ```
3. reset / checkout

  ```bash
  $ git checkout index     # checkout the branch
  $ git checkout -- index  # checkout the file
  ```
4. Always rename your file before you make some changes

```bash
# git will stage the changes
$ git mv content.js newContent.js
```
5. Staging your files

  ||new files|modified files|deleted files||
  |---|---|---|---|---|
  |git add --all|v|v|v|stage all|
  |git add .|v|v|v|stage all|
  |git add --ignore-removal .|v|v|x|stage new and modified files only|
  |git add -u|x|v|v|stage modified and deleted files only|

6. Deleting files

  ```bash
  $ git rm oldFile.js
  ```

7. help

```bash
$ git help stash
```

8. reflog

```bash
$ git reflog
```

9. branch in remote?

### Regret from commit/push

1. Be careful. **git reset** will delete all your working changes!

  ```bash
  $ git reset --hard HEAD~1
  ```
2. If you already pushed it, you will need to force push to get rid of it.

  ```bash
  $ git push origin HEAD --force
  ```

  **However**, if others may have pulled it, then you would be better off starting a new branch. Because when they pull, it will just merge it into their work, and you will get it pushed back up again.

  If you already pushed, it may be better to use git revert, to create a "mirror image" commit that will undo the changes. However, both commits will be in the log.
