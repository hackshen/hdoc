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