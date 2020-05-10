# Mac Env Config

### [Homebrew](https://brew.sh/)

> Homebrew是一款Mac OS平台下的软件包管理工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。简单的一条指令，就可以实现包管理，而不用你关心各种依赖和文件路径的情况，十分方便快捷。

> 如果你zsh或者nvm连接超时，在 /etc/hosts 文件里面添加 `199.232.68.133 raw.githubusercontent.com`


###### 安装 Homebrew

```bash
#在终端输入如下命令
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

###### 常用命令
```bash
brew install git #安装软件
brew search git  #搜索软件
brew remove git  #卸载软件
brew list        #显示已安装的软件
brew update      #更新所有软件
```

### [iTerm2](https://www.iterm2.com/) +  Zsh + [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh)

>`iTerm2`: 是Mac下终端的替代品，比自带的终端强N倍
>`Zsh`: Linux 的一种 shell 外壳
>`Oh My Zsh`: 是用来管理 zsh 的配置，具有有丰富的插件，让你爱不释手

###### 安装 iTerm2
```bash
# 官网下载地址，下载的是压缩文件，解压后是执行程序文件，直接将它拖到 Applications 目录下
https://www.iterm2.com/

# 通过homebrew安装
brew cask install iterm2
```
###### 安装 Oh My Zsh

```bash
#在终端输入如下命令
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

#安装好之后 把 Zsh 设置为当前用户的默认 Shell
chsh -s /bin/zsh
```



### [Git](https://git-scm.com/)

###### 安装 Git
```bash
#通过homebrw安装
brew install git

#通过官网下载安装
https://git-scm.com/downloads
```
###### 创建 ssh key
```bash
ssh-keygen -t rsa -C "你的Email"
```
###### 验证有效性
```bash
ssh -T git@github.com
```

### [Nvm](https://github.com/creationix/nvm)
> nvm是Mac下的`node`版本管理工具，可以任意的切换node版本，为什么选择安装`NVM`而不是`N`呢？因为nvm安装的node版本是隔离开的，每个node版本都有一个独立的文件夹
> [Nvm仓库地址](https://github.com/creationix/nvm)

###### 安装 Nvm

```bash
#在终端输入如下命令
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```
###### 配置环境变量
```bash
#编辑用户根目录下的~/.bash_profile文件添加以下环境变量;如果你用的zsh那么编辑~/.zshrc
#打开新的窗口环境变量生效，或者执行 source ~/.bash_profile 或 source ~/.zshrc 及时生效
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```
###### nvm 常用命令
```bash
nvm install   #安装指定版本
nvm uninstall #卸载已安装的node版本
nvm use       #切换已安装的node版本
nvm ls        #列出本机已安装的node版本
nvm ls-remote #列出所有远程服务器可安装的node版本
nvm current   #显示当前正在用的node版本
nvm alias default v8.9.0 #默认node版本
nvm alias     #给不用的node版本添加别名
nvm unalias   # 删除已定义的别名
```

### [mycli](https://github.com/dbcli/mycli)
> A Terminal Client for MySQL with AutoCompletion and Syntax Highlighting.

###### install
```bash
brew update && brew install mycli
```

###### use
```bash
mycli -u [name] -p [password]
```





