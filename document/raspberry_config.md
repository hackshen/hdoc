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