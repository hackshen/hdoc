#### Sh 执行方式
- sh test.sh
- ./test.sh 这种方式需要给文件加上可执行权限(chmod +x test.sh)

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
