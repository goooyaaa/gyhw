fix bug by tag

[toc]

## 思路
1. 主分支回退到打标签的那次提交
2. 拉取分支bugfix
3. 主分支立即回到最新状态
4. 切换到bugfix分支，修改bug，发版本，打新标签
5. 合并bugfix分支到主干上
6. 手动推送标签到远程

## 思路2
利用tag功能切换并修改某个历史版本
`git checkout -b [branchName] [tagName]`省去123步骤，我x，这次是正确的

## 相关命令


## 查到之前发布的版本tag id 
```
git tag 
git show v1.x.x
git reset --hard tag_id
```
## 新建bugxxfix分支
```
git checkout -b bugxxfix
# 切换到 master 分支
git checkout master
# 查看最新版本对应的 Commit ID
git reflog
# 前进到最新版本
git reset --hard 1523898
git checkout bugfix
```
## 修改bug
正常 git add & git commit 即可，并将 bugfix 分支推送到远程 GitHub
```
git add <file>
git commit -m "Fix bugs"
git push origin bugxxfix
```
## 重打tag
```
git tag v0.0.x
```
将改好 Bug 的代码重新打上 v0.1.1 的 tag。这里需要注意的是，默认情况下 git 会给 v0.1.1 附上一个当前的时间戳，从而会出现 v0.1.1 的发布时间比 v0.4.2 晚的情况，GitHub 的 Release 页面则会认为 v0.1.1 是最新的版本。因此我们需要自行“伪造”一个提交日期，即为原先 v0.1.1 的提交日期即可：
```
GIT_COMMITTER_DATE="2017-10-14 23:27" git tag -f v0.1.1 -m "The V0.1.1 Release"
```
将修改后的 tag 推送到远程 GitHub（强制更新）：
```
git push -f origin --tags
```
## Merge
最后需要将 bugfix 分支归并到 master 分支：
```
git checkout master
git merge bugfix --allow-unrelated-histories
```
## 清理
后续的一些清理工作即删除临时的 bugfix 分支：
```
# 删除本地 bugfix 分支
git branch -d bugfix
# 删除远程 bugfix 分支
git push --delete origin bugfix
```
end