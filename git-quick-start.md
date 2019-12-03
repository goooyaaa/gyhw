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


