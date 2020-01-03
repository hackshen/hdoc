# Samba
> Samba是在Linux和UNIX系统上实现SMB协议的一个免费软件

```bash
# 安装samba
yum install -y samba

# 关掉防火墙
systemctl stop firewalld
systemctl disable firewalld

# 用户创建&删除
useradd test # 在系统中创建用户test
smbpasswd -a test # 添加用户 test
smbpasswd -x test # 删除用户 test

# 启动Samba服务
systemctl start smb
systemctl enable smb
systemctl restart smb
systemctl status smb

# 测试(remote_ip 安装samba服务的ip)
在Mac浏览器中输入 smb://remote_ip 
```
