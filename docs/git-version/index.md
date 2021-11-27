# Git versionament system

1. [Official documentation](https://git-scm.com/doc)

## Basic workflow

To clone a repo:
```shell
git clone https://github.com/GiliardGodoi/quickrefs.git
```

To get updates from remote repository:
```shell
git pull
```

To add a specific file to stage area:
```shell
git add path_to_or_filename.txt
```

To add all files to stage area:
```shell
git add .
```

To commit files with a short message:
```
git commit -m "commit message"
```

To push commits to the remote repo:
```shell
git push
```

## Branches

To see all local branches
```shell
git branch
```

To create a new local branch
```shell
git branch pretty-name
```

Change to another branch
```shell
git checkout pretty-name
```

Instead, you can create and change to another branch in a single line:
```shell
git checkout -b pretty-name
```

Push changes from a local branch to remote repo (and creating a remote branch):
```shell
git push --set-upstream origin pretty-name
```

Download a remote branch:
```shell
git checkout -b pretty-name origin/pretty-name
```