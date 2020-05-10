# Raspberry pie

#### Mac烧录树莓派镜像

```bash
# 查看挂在的所有硬盘
diskutil list

# 取消挂在的硬盘
diskutil unmountDisk

# 烧录镜像 等待几分钟就好了
sudo dd bs=4m if=pi.img of=/dev/rdisk1
```

#### 无显示器、鼠标、键盘、网线 直连SSH

```bash
# 经上步完成后，在内存卡根目录建立 wpa_supplicant.conf 文件，这样树莓派启动就能直接连接上无线网络了

country=CN
ctrl_interface=/var/run/wpa_supplicant
update_config=1
network={
    ssid="WIFI_NAME"
    scan_ssid=1
    psk="WIFI_PASSWORD"
    key_mgmt=WPA-PSK
    priority=1
}

# 连接SSH(在你的路由器中找到树莓派的IP,Mac可以直接ssh连接，默认用户:pi 密码: raspberry)
ssh pi@you_ip
```

## Docker install

```bash
curl -sSL https://get.docker.com| sh
```
但是装完之后你运行docker可能提示你没权限，必须要加sudu 比如 `sudo docker`,遇到这样的情况你可以吧docker加进管理组
```bash
pi@raspberrypi:~ $ sudo groupadd docker # 添加docker用户组
groupadd: group 'docker' already exists # 提示用户组已存在
pi@raspberrypi:~ $ sudo gpasswd -a $USER docker # 添加登录用户到docker用户组
Adding user pi to group docker 
pi@raspberrypi:~ $ newgrp docker # 更新用户组
pi@raspberrypi:~ $ docker ps # 测试是否可用
```

## docker-compose install [官网地址](https://docs.docker.com/compose/install/)
我直接用pip安装了
```bash
sudo apt-get update
sudo apt-get install libffi-dev # 一定要装libffi-dev不然会报错 #include <ffi.h>

sudo apt-get install -y python python-pip
sudo pip install docker-compose
```

添加pip源,将下面文件写入 ~/.pip/pip.conf文件里，没有就新建

```bash
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
trusted-host=mirrors.aliyun.com
```




