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
