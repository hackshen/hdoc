# Frp

### 群辉内网穿透
- frp版本0.29.0(synology 718+测试通过)
- 可以直接下载镜像: `docker pull hackshen/frp`
- 镜像里面包含了frpc和frps默认运行 `./frpc -c /frp/frpc.ini`
- 网络使用host只支持linux
##### [The host networking driver only works on Linux hosts, and is not supported on Docker Desktop for Mac, Docker Desktop for Windows, or Docker EE for Windows Server.](https://docs.docker.com/network/host/)
```bash
# 客户端运行
docker run \
    -d \
    --name frp_c \
    --network host \
    -v <local frpc.ini path>:/frp/frpc.ini \
    hackshen/frp
# 服务端运行
docker run \
    -itd \
    --name frp_s \
    --network host \
    -v <local frps.ini path>:/frp/frps.ini \
    hackshen/frp /bin/sh -c './frps -c frps.ini'
```

> frpc.ini
```bash
[common]
# 服务器地址
server_addr = xxx.xxx.xxx.xxx
server_port = 7002
admin_addr =  127.0.0.1
admin_port = 7400
admin_user = admin
admin_pwd = admin

[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 6007
```

>  frps.ini
```bash
[common]
dashboard_port = 7500
#dashboard 用户名密码，默认都为 admin
dashboard_user = admin
dashboard_pwd = admin
bind_port=7002
vhost_http_port = 81
```

