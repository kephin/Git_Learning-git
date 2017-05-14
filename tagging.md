# Tagging

:mag: Tags are nothing more than labels that we can apply at any commits in the history. They are often used to denote major milestones or version numbers in source code.

### Lightweight tags

```bash
# create a tag on the particular commit
$ git tag myTag

# list all tags
$ git tag --list

# we can use the name of the tags in other Git commands as the reference
$ git show myTag

# delete the tag
$ git tag -d myTag
```

### Annotated tags
:mag: Similar to lightweight tag, except with extra information

```bash
$ git tag -a v-1.0 # will prompt the editor for leaving messages

# you can also
$ git tag -a v-1.2 -m 'Release 1.2'
# or you can omit -a
$ git tag v-1.2 -m 'Release 1.2'

# now if we git show on the annotated tag, it will show the tag information
# lightweight tags will just show commit information
$ git show v-1.0
```

### Comparing tags

```bash
# compare difference between commits referenced by tags
$ git diff v-1.0 v-1.2
# or
$ git difftool v-1.0 v-1.2
```

### Tagging a specific commit

```bash
# create a tag onto commit 94ef32i
$ git tag -a v-0.9-beta 94ef32i
```

### Updating a existing tag

```bash
# if tag: v-0.8-alpha is existed, we want to move it to the commit bd2847d
$ git tag -a v-0.8-alpha -f bd2847d
```

### Using tag with GitHub

```bash
# push certain tag to the remote
$ git push origin v-0.9-beta

# push all local tags to the remote
$ git push origin master --tags

# delete certain tag to the remote
$ git push origin :v-0.8-alpha
```
