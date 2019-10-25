# Git 常用命令

> demo-branch: 演示分支


#### 分支相关

```bash
# 切换分支
git checkout demo-branch

# 创建新分支并切换到该分支
git checkout -b demo-branch

# 删除本地分支
git branch -D demo-branch 

# 删除远程分支
1、git push origin -d demo-branch
2、git push origin :demo-branch

# 显示本地分支
git branch

# 显示远程分支
git branch -r

# 显示本地和远程分支
git branch -a

# 显示本地分支关联远程仓库情况
git branch -vv

# 重命名本地分支
git branch -m new-branch


```
#### 拉取远程仓库代码到本地

```bash
# 拉取远程仓库代码到本地当前分支(本地分支已与远程分支关联)
git pull

# 拉取远程仓库代码到本地其它分支
git pull origin <remote-branch>:<local-branch>

# 拉取远程分支代码到本地当前分支
git pull origin <remote-branch>
```

#### 提交相关

```bash
# 添加变更代码到暂存区(文件已被追踪)
git add -u

# 添加所有变更到暂存区
git add .

# 提交代码到本地仓库
git commit -m 'xxxx'
```

#### 撤回相关

```bash
# 放弃本地的一些变更
git checkout <file-name>

# 放弃本地所有变更
git checkout .

# 如果已经commit了且代码还在本地仓库，想撤回commit提交，且代码还想保留
git reset

# 代码回退到某一版本且这个版本之前的代码还想保留
git reset <commit-hash>

# 代码回退到某一版本且以前的代码都不要了
git reset --hard <commit-hash>
```
