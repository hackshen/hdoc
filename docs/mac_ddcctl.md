# cli控制Mac外接显示器亮度
#### 起因
- 我显示器放在窗户旁边，晚上和白天需要手动调节显示器亮度，关键是物理按钮，心累呀所以找到了一个命令行调节显示器亮度的办法

#### 安装 ([传送门](https://github.com/kfix/ddcctl))
```bash
# 一定要先装Xcode
# clone作者的代码到本地

#进入项目的目录执行安装
make install 
make CCFLAGS=-DOSD clean ddcctl
# 设置显示器1为hdmi接口17
ddcctl -d 1 -i 17 
# 调节显示器1的亮度和对比对都为100%
ddcctl -d 1 -c 100 -b 100 

# 我个人在terminal新建了alias
alias d100='ddcctl -d 1 -c 100 -b 100'
alias d90='ddcctl -d 1 -c 90 -b 90'
alias d80='ddcctl -d 1 -c 80 -b 80'
alias d70='ddcctl -d 1 -c 70 -b 70'
alias d60='ddcctl -d 1 -c 60 -b 60'
alias d50='ddcctl -d 1 -c 50 -b 50'
alias d40='ddcctl -d 1 -c 40 -b 40'
alias d30='ddcctl -d 1 -c 30 -b 30'
```

