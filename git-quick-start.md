## install & config 
git config --global user.name "goooyaaa"
git config --global user.email "goooyaaa@163.com"

## 常用命令
git status
git log 

## 版本回退
Git中HEAD表示当前版本，也就是最新提交的版本。上一个版本就是HEAD^，上上一个版本就是HEAD^^，往上100个版本写成HEAD~100。

```git
git reset --hard HEAD^
git reset --hard commitId
git reflog #查看命令历史
```

## 版本库

- 工作区
- 暂存区
- 本地仓库
- 远程仓库

工作区>>>>暂存区>>>>仓库
git add把文件从工作区>>>>暂存区，git commit把文件从暂存区>>>>仓库
git diff查看工作区和暂存区差异
git diff --cached查看暂存区和仓库（上次git commit 后的内容）差异
git diff HEAD 查看工作区和仓库的差异

## 撤销修改
1. 放弃工作区的修改时，用命令git checkout -- file
2. 修改了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
3. 已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

## 删除文件
先手动删除文件，然后使用git rm <file>和git add<file>效果是一样的。
另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：
git checkout -- test.txt
git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”

<<<<<<< HEAD
## branch branch branch branch branch
git branch -b dev
查看分支：git branch
创建分支：git branch <name>
切换分支：git checkout <name>或者git switch <name>
创建+切换分支：git checkout -b <name>或者git switch -c <name>
合并某分支到当前分支：git merge <name>
删除分支：git branch -d <name>

