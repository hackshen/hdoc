# Git 常用命令

> demo-branch: 演示分支 ([在线练习Git](https://learngitbranching.js.org/))

> git访问慢可以在host里面添加: `140.82.112.6 www.github.com  api.github.com` 也可通过[Ip Address](https://www.ipaddress.com/)查询github的真实地址


#### 初始化
```bash
# 生成公钥
ssh-keygen -t rsa -C "你的邮箱地址"
# 查看你的公钥
cat ~/.ssh/id_rsa.pub

# 全局配置提交信息
git config --global user.name "提交者的名字"
git config --global user.email "你的邮箱地址"

# 测试是否配置成功
ssh -T git@github.com
```

#### 进阶
```bash
# 配置多个公钥(~/.ssh 下新建config文件填入以下内容)

#Github
Host github
HostName github.com
User hackshen.com@gmail.com
IdentityFile ~/.ssh/id_rsa_github  #你github对应的公钥路径

#Gitlab
Host gitlab
HostName gitlab.xxxxx.com
User hackshen.com@gmail.com
IdentityFile ~/.ssh/id_rsa #你gitlab对应的公钥路径

Tips: 如果你电脑重启了这时候你会发现你github的公钥失效了，因为缓存丢失了执行以下命令即可
ssh-add ~/.ssh/id_rsa_github
```
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

#### 其它

```bash
# 合并某次commint
git cherry_pick <commit-hash>
```
