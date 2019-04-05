# Git Cheat Sheet

## Configure Tooling

Configure user information for all **local** repositories

```sh
cat ~/.gitconfig
git config --global user.name "[name]"
git config --global user.email "[email address]"
git config --global color.ui auto
```

## Create Repositories

Start a new repository or obtain one from an existing URL

```sh
git init [project-name]
git clone [url]
```

## Make Changes

Review edits and craft a commit transaction

```sh
git status
git diff
git add [file]
git diff --staged
git reset [file]
git commit -m "[descriptive message]"
```

## Group Changes

Name a series of commits and combine completed efforts

```sh
git branch
git branch [branch-name]
git checkout [branch-name]
git merge [branch]
git branch -d [branch-name]
```

## Refactor Filenames

Relocate and remove versioned files

```sh
git rm [filename]
git rm --cached [filename]
git mv [file-original] [file-renamed]
```

## Suppress Tracking

Exclude temporary files and paths

A text file named .gitignore suppresses accidental versioning of files and paths matching the specified patterns

```sh
git ls-files --other --ignored --exclude-standard
```

Git sees every file in your working copy as one of three things:

- tracked - a file which has been previously staged or committed;
- untracked - a file which has not been staged or committed; or
- ignored - a file which Git has been explicitly told to ignore.

Ignored files are usually build artifacts and machine generated files that can be derived from your repository source or should otherwise not be committed. 

