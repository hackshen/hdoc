# Cenetos manual

> 刚安装/购买centos主机后一些环境配置、常用命令、使用手册.

## 环境初始化

#### Install git
```bash
yum install git -y
```

#### Install net-tools
```bash
yum -y install net-tools
```

#### Install zsh
- [Go to mac_env Install zsh](https://github.com/hackshen/hdoc/blob/master/docs/mac_env.md#%E5%AE%89%E8%A3%85-oh-my-zsh)

#### Install docker
- [https://docs.docker.com/install/linux/docker-ce/centos/](https://docs.docker.com/install/linux/docker-ce/centos/)

#### Install docker-compose
```bash
# install
sudo curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.4/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

# Add permissions
sudo chmod +x /usr/local/bin/docker-compose
```

## 常用命令

#### 防火墙开启/关闭
```bash
# 开机启动防火墙
systemctl enable firewalld.service

# 开机禁用防火墙
systemctl disable firewalld.service

# 启动防火墙
systemctl start firewalld

# 关闭防火墙
systemctl stop firewalld

# 查看防火墙状态
systemctl status firewalld
```

#### 防火墙配置
```bash
# 查看防火墙状态
firewall-cmd --state

# 加载配置(添加端口后记得执行)
firewall-cmd --reload

# 查看开放的端口
firewall-cmd --list-ports

# 添加开放的端口
firewall-cmd --zone=public --add-port=3000/tcp --permanent

# 移除开放的端口
firewall-cmd --zone=public --remove-port=3000/tcp --permanent
```

#### docker
```bash
# 重启docker
systemctl restart docker
```

## 升级git到2.x版本
```bash
# centos默认git 是1.8版本的，如果你的项目里面有git hook 请升级到2.3版本以上
# 删除git版本
yum remove git

# 安装依赖确保本地有gcc编译环境
yum install -y curl-devel expat-devel gettext-devel openssl-devel zlib-devel asciidoc  gcc perl-ExtUtils-MakeMaker

# 下载新的git版本解压进入
wget https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.33.0.tar.gz tar -xzvf git-2.33.0.tar.gz && cd git-2.33.0

# 编译安装
make prefix=/usr/local/git all
make prefix=/usr/local/git install

# 报以下错误
#include <openssl/ssl.h> ^ compilation terminated. make: *** [fuzz-commit-

# 安装openssl
yum install -y curl-devel expat-devel gettext-devel openssl-devel

# 配置环境变量
echo "export PATH=$PATH:/usr/local/git/bin" >> .~/.bashrc

# 重新加载变量
source ~/.bashrc

# 验证git版本
git --version
```