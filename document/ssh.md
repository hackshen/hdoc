
#### Sh 执行方式
```bash
sh test.sh
./test.sh 这种方式需要给文件加上可执行权限(chmod +x test.sh)
```

#### Sh sudo 免输密码
```bash
#!/bin/bash
sudo -S nginx -s reload << EOF
#password要换成你的密码
password
EOF
```
#### 远程(下载||上传)文件
```bash
#!/bin/bash
# -r: 递归复制整个目录。
# -P: 注意是大写的P, port是指定数据传输用到的端口号
scp -r <user_name>@<server_ip>:<remote_file_path> <local_file_path>

复制文件: scp -r root@192.168.1.100:~/test/a.js ~/a.js
指定ssh端口: scp -P 2222 -r root@192.168.1.100:~/test/a.js ~/a.js
```
#### 映射本地端口到远程

```bash
ssh -Nf -R 2222:127.0.0.1:22 root@<remote address>
```

#### SSH password free login

```bash
ssh-copy-id root@<remote address>
```

#### SSH agent

```bash
# 🌰: 有一下三台机器 S1、S2、S3 ===> S1的公钥分别放在了S2和S3上面，当然也可以免密分别登录S2和S3，
# 但是当你从S1登录到S2，如果再想从S2登录到S3是需要密码，因为你S2的公钥没有放在S3上面，不过我们可以让S2充当代理的角色
方案1: 编辑本地 vi /etc/ssh/ssh_config 将ForwardAgent值设置为yes，表示允许客户端进行转发
方案2: ssh -A root@xxx.xxx.xxx.xxx
```
