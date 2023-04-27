---
title: Git Commands
pubDate: 2023-04-27
description: ''
---

## 初始化

1. 直接关联远程仓库
    - git clone: 将远程仓库拉取到本地
1. 先创建本地仓库，再关联远程仓库
    - git init: 本地目录使用 Git 做版本管理
    - git remote add: 将本地的 Git 仓库与远程仓库关联 `git remote add origin https://github.com/someone/someproject.git`，origin 为远程服务器名

## 提交

- git add: 将变动的文件加入 Git 索引，如 `git add app/model/user.rb`
- `git commit -m "commit detail"`
- `git push origin`: 将本地的代码更新到名为 orgin 的远程版本库

## 分支管理

### git branch

命令参数：

- `-d`, `--delete`: 删除分支
- `-m`, `--move`: 移动或重命名分支

参数若是大写，等同于多了 `--force`，强制执行。

```bash
# 列出本地所有分支
git branch

# 从当前的工作版本创建 newbranch 分支
git branch newbranch

# 强制删除 newbranch 分支
git branch -D newbranch

# 重命名分支
git branch -M oldBranch newBranch
```

### git checkout

- `git checkout newbranch`: 切换到 newbranch 分支
- `git checkout app/model/user.rb`: 将 user.rb 文件从上一个已提交的版本中更新回来，未提交的内容全部会回滚

### git rebase

用下面两幅图解释会比较清楚一些，rebase 命令执行后，实际上是将分支点从 C 移到了 G，这样分支也就具有了从 C 到 G 的功能

![[git-rebase.png]]

### git reset

将当前的工作目录完全回滚到指定的版本号，假设如下图，我们有 A-G 五次提交的版本，其中 C 的版本号是 bbaf6fb5060b4875b18ff9ff637ce118256d6f20，我们执行了 `git reset bbaf6fb5060b4875b18ff9ff637ce118256d6f20` 那么结果就只剩下了 A-C 三个提交的版本

![[git-reset.png]]

### git tag

将某个具体的版本打上标签，就不需要记忆复杂的版本号哈希值了

## git log

查看历史提交记录

```bash
# 查看简洁版本
git log --oneline

# 指定最近几个提交
git log --oneline -5

# 按日期筛选
git log --after="2019-3-2" --before="2019-3-19"

# 以类似 GUI 工具的形式展示日志
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

## git revert

revert 可以平稳的回滚代码，并且保留提交记录。

```bash
# 回滚到某个 commit
git revert commit-sha1
```

## git mv

如果直接修改文件（夹）名，git 会判定为删除该文件（夹），再添加 untracked 的文件（夹），导致文件（夹）的修改历史丢失。可以使用 `git mv` 移动或重命名文件，同时保留修改历史。

```bash
git mv [-v] [-f] [-n] [-k] <source> <destination>
git mv [-v] [-f] [-n] [-k] <source> ... <destination directory>
```

在第一种形式中，它将 `<source>` 重命名为 `<destination>` ，它必须存在，并且可以是文件，符号链接或目录。  
在第二种形式中，最后一个参数必须是现有目录，给定的源都将被移动到目标目录中。

- `-f` , `--force`: 即使目标存在，也要强制重命名或移动文件
- `-k`: 跳过移动或重命名会导致错误情况的操作。当源既不存在也不受 Git 控制时，或者除非-f给出，否则会覆盖现有文件时发生错误。
- `-n`, `--dry-run`: 没做什么，只显示会发生什么
- `-v`, `--verbose`: 报告移动文件的名称

Sometimes, carrying out a case-sensitive rename may require to take two steps:

```bash
git mv casesensitive tmp
git mv tmp CaseSensitive
```

## git pull

获取最新代码

```bash
# 将 origin 这个版本库的代码更新到本地的 main 分支
git pull origin main
```

## git rm

从本地和远程仓库删除文件

```bash
git rm <file>
git rm -r <folder>
git commit -m 'delete something'
git push origin main
```

只删除远程仓库中的文件

```bash
git rm --cached <file>
git rm -r --cached <folder>
git commit -m 'delete something'
git push origin main
```

## git stash

会把所有未提交的修改（包括暂存的和非暂存的）都保存起来，当前工作目录就干净了。

```bash
# 创建 stash
git stash
# 创建 stash 并备注
git stash save "test stash message"
# 查看现有 stash
git stash list
# 恢复到工作目录，删除 stash
git stash pop
# 恢复到工作目录，但不删除 stash
git stash apply
```

stash 还有一些[高级用法](https://www.cnblogs.com/tocy/p/git-stash-reference.html)，这里不列举。

## git status

查看当前目录的状态

```bash
# 查看状态 git status --long
git status

# 概要信息 git status --short
git status -s
```
