```bash
# ln 软连
ln -s 源文件 目标文件 

# 设置文件权限
chmod 755 ~/.ssh
chmod 600 ~/.ssh/id_rsa
```


> Centos

```bash
# 查看linux版本
uname -a 

# 查看磁盘使用情况
df -h

# 查看cpu核心数
cat /proc/cpuinfo

# 查看进程
top

# 查看内存情况
free

# 查看协议信息
netstat -s

# 登录用户
who -u

# 内网ip
ifconfig

# 
```

## Vim

```bash
:w  # 快速保存
0   # 快速移动到行首
gg  # 快速移动到文件首
G   # 快速移动到文件尾
zz  # 快速把光标移动至本屏幕中间
dd  # 剪切本行
yy  # 复制本行

```

## 必备软件

- [jq](https://stedolan.github.io/jq/manual/) 是一款命令行的 json 处理工具。类似于 lodash 一样，它可以对 json 做各种各样的处理: pick，get，filter，sort，map
- git
- htop
