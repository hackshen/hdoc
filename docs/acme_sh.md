# docker-compose 部署 acme.sh申请Let's encrypt 证书

> acme.sh 实现了 acme 协议, 可以从 letsencrypt 生成免费的证书.

 > [acme.sh地址](https://github.com/acmesh-official/acme.sh/wiki/Run-acme.sh-in-docker)
 
 > [获取阿里云AccessKey](https://usercenter.console.aliyun.com/?spm=5176.12818093.nav-right.dak.488716d0qgnmuw#/manage/ak)
 
  [docker & docker-compose install](https://github.com/hackshen/hdoc/blob/master/document/centos_env.md#install-docker)


 ```bash
# 新建一个docker-compose.yml 
touch docker-compose.yml

# 填入下面配置
version: "3"
services:
  acme.sh:
    image: neilpang/acme.sh
    container_name: acme.sh
    restart: always
    command: daemon
    environment:
      - Ali_Key=xxxxxxx # 此处填获取的阿里云的AccessKey
      - Ali_Secret=xxxxxxx # 此处填获取的阿里云的AccessKey
    volumes:
      - ./ssl:/acme.sh

# 启动容器(启动后可以通过 docker ps 查看当前运行的容器)
docker-compose.yml up -d

# 生成证书 (生成证书放在当前ssl目录)
docker exec acme.sh \
    --issue \
    --dns dns_ali \
    -d '*.hackshen.com' 
```

