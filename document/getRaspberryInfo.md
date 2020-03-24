## 获取 raspbery CPU RAM DISK IP 信息，驱动ssd1306

> [Luma.OLED](https://luma-oled.readthedocs.io/en/latest/install.html)

> [Luma.OLED github](https://github.com/rm-hull/luma.oled)

```bash
# 安装驱动
$ sudo apt install python-dev python-pip libfreetype6-dev libjpeg-dev build-essential libopenjp2-7 libtiff5
$ sudo -H pip install --upgrade luma.oled
```

```bash
# -*- coding:UTF-8 -*-
from luma.core.interface.serial import i2c, spi
from luma.core.render import canvas
from luma.oled.device import ssd1306
import time,os,socket,fcntl,struct

def getHostIp():
    try:
        my = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        my.connect(('8.8.8.8', 80))
        # ip = my.getsockname()[0]
        ipList = my.getsockname()
    finally:
        my.close()
    return ipList

# Return % of CPU used by user as a character string
def getCPUuse():
    return(str(os.popen("top -n1 | awk '/Cpu\(s\):/ {print $2}'").readline().strip()))

# Return CPU temperature as a character string
def getCPUtemperature():
    res = os.popen('vcgencmd measure_temp').readline()
    return(res.replace("temp=","").replace("'C\n",""))

def getRAMinfo():
    p = os.popen('free')
    i = 0
    while 1:
        i = i + 1
        line = p.readline()
        if i==2:
            return(line.split()[1:4])


def getDiskSpace():
    p = os.popen("df -h /")
    i = 0
    while 1:
        i = i +1
        line = p.readline()
        if i==2:
            return(line.split()[1:5])

def ramTotal():
    return(round(int(getRAMinfo()[0]) / 1000,1))

def ramUsed():
    return(round(int(getRAMinfo()[1]) / 1000,1))

def ramFree():
    return(round(int(getRAMinfo()[3]) / 1000,1))


# 创建 IIC 设备
serial = i2c(port=1, address=0x3C)

# 如果使用 SPI，换成这个
# serial = spi(device=0, port=0)

# 创建屏幕的驱动实例
device = ssd1306(serial)

while True:
       with canvas(device) as draw:
            draw.rectangle(device.bounding_box, outline="white", fill="black")
            draw.text((18, 5), "Hshen raspberry" , fill="white")
            draw.text((2, 14), "CPU:" + getCPUuse() , fill="white")
            draw.text((62, 14), "Temp:" + getCPUtemperature() , fill="white")
            draw.text((2, 23), "RAM:" + str(ramUsed()) + "/" + str(ramTotal()) , fill="white")
            draw.text((2, 33), "Disk:" + str(getDiskSpace()[1]) + "/" + str(getDiskSpace()[0]) , fill="white")
            draw.text((2, 42), "ip:" + getHostIp()[0] , fill="white")
            draw.text((2, 52),time.strftime("%Y-%m-%d %H:%M:%S", time.localtime())  , fill="white")
       time.sleep(2)
```
