# Git Setup & Config

Initiate a git repository into existing directory

```sh
git init
```

Clone an existing repository into a specified directory

```sh
git clone [repo-url]
```

Set user information for your commits 

```sh
git config --global user.name "[name]"

git config --global user.email "[email]"
```
> Tag `--global` is used for configuring user information for all local repositories

# Git Daily Work

Stage changes for the next commit 

```sh
git add 
```

> After `git add` you can add ``directory-name`` or `files-name` \
> You `.` to stage all changes in current directory

Commit staged files and specify a commit message

```sh
git commit -m "message" 
```

Show list of all changes <staged, unstaged and tracked>

```sh
git status 
```

Display the commit history

```sh
git log 
```

Show unstaged changes

```sh
git diff 
```

Push your commits into a specified branch

```sh
git push [remote] [branch] 
```

# Git Branches

Creates a new branch

```sh
git branch [branch-name]
```

Delete branch

```sh
git branch -d [branch-name]
```

Switch to specified branch

```sh
git checkout [branch-name]
```

> Add `-b` tag after `checkout` to create and switch to branch, if not already exist

Combine a specified branch files with the current branch

```sh
git merge [branch-name]
```

> ***Exp.*** If you're working on branch `dev` and now you want to merge that into branch `main`, \
> You need to get into branch `main` and run this command `git merge dev`

# Git Remote Repo

Connect to a remote repo

```sh
git remote add [name] [url]
```

> We mostly use the term `origin` for the tag `name`, which is the name for the `remote`

Update the connected remote repo

```sh
git remote set-url [name] [url]
```

Fetch changes from the remote

```sh
git fetch [remote]
```