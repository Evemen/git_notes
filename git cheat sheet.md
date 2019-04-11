# [Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)

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
git diff # By default git diff will show you any uncommitted changes since the last commit.
git add [file]
git diff --staged
git reset [file]
git commit -m "[descriptive message]"
```

The 3 main types of git diff commands:

```sh
git diff: Show differences between your working directory and the index.
git diff –cached: Show differences between the index and the most recent commit.
git diff HEAD: Show the differences between your working directory and the most recent commit.
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
git rm [filename] # removes the file from the repo but also deletes it from the local file system.
git rm --cached [filename] # To remove the file from the repo and not delete it from the local file system use:
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

## Save Fragments

Shelve and restore incomplete changes

```sh
git stash
git stash list
git stash pop
git stash drop
```

## Review History

Browse and inspect the evolution of project files

```sh
git log
git log --follow [file]
git diff [first-branch] [second-branch]
git show [commit]
```

## Redo Commits

Erase mistakes and craft replacement history

```sh
git reset [commit]
git reset --hard [commit]
```

还有git revert更推荐使用（在使用remote repo和collaboration时）

参考[如何在 Git 中重置、恢复，返回到以前的状态](https://zhuanlan.zhihu.com/p/42081574)

## Synchronize Changes

Register a repository bookmark and exchange version history

```sh
git fetch [bookmark]
git merge [bookmark]/[branch]
git push [alias] [branch]
git pull
```

## 一些实用的命令

```sh
# 便捷的查看commit history
git log --oneline
git log --oneline master
git log --oneline branch_1
```

```sh
# 修改写错的commit
git commit --amend
# 场景：我刚刚的commit忘了add 改动文件了怎么办，不用新建commit，可以直接修改
git add .
git commit --amend
```

```sh
git reflog
# 在你眼前的是你用 git 命令的所有历史
# 每一条历史都有一个序号index，表示为 HEAD@{index}
# 找到你刚刚闯祸的那条命令 index
git reset HEAD@{index}
# 恢复，神奇时光机
```

```sh
# 连接远程仓库
git remote add origin git@github.com:jia-zhuang/test.git
# 将本地仓库同步到远程仓库
git push origin master
```

```sh
git config --list
```

# 参考

https://zhuanlan.zhihu.com/p/42427823

https://zhuanlan.zhihu.com/p/36749397

https://zhuanlan.zhihu.com/p/40461007

https://www.atlassian.com/git/tutorials/saving-changes/git-diff

http://gitguys.com/topics/git-diff/
