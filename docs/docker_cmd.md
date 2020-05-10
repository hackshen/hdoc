# Dcoker Command

```bash
# docker 开机启动
systemctl enable docker

docker run 
    -d    #后台运行容器，并返回容器ID
    -i    #以交互式模式运行容器，常与-t参数同时使用
    -t    #给容器重新分配一个伪终端，常与-i参数同时使用
    –name #给容器指定一个名称
    -m    #指定容器使用内存的最大值
    –net  #指定容器使用的网络类型
    –link #链接到另一个容器
    <Demo>: docker run -itd -p 3001:3000 -v /node:/node --name node_demo node
        
docker rm
    -f #强制删除一个运行中的容器
    -l #删除指定的链接
    -v #删除与容器关联和卷

docker exec
    -d #在后台运行
    -i #保持STDIN打开
    -t #分配一个伪终端

docker ps
    -a #列出所有容器包括停止的
    -f #根据条件过滤显示内容
    -l #列出最近创建的容器
    -n #列出最近创建的N个容器，N为数字
    -q #只显示容器ID
    -s #显示总文件大小

docker inspect
    -f #指定返回值格式或模板文件
    -s #显示总文件大小
    –type #为指定类型返回JSON

docker logs
    -f : 跟踪日志输出
    --since :显示某个开始时间的所有日志
    -t : 显示时间戳
    --tail :仅列出最新N条容器日志
docker port
    <Demo>: docker port node

docker commit
    -a #提交的镜像作者
    -c #使用Dockerfile指令来创建镜像
    -m #提交时附上说明文字
    -p #在commit时，将容器暂停

docker images
    -a #列出所有的镜像（含中间映像层，默认，过滤掉中间映像层）
    –digests #显示镜像的摘要信息
    -f #显示满足条件的镜像
    –format #指定返回值的模板文件
    –no-trunc #显示完整的镜像信息
    -q #只显示镜像ID

docker rmi
    -f #强制删除
```

### redis

```bash
docker run \
    --name redis
    -p 6379:6379 
    -d redis
```

### [webssh](https://github.com/huashengdun/webssh)

```bash
docker run \
    --name wssh \
    -p 8888:8888 \
    -itd python:3.7 /bin/sh -c 'pip install webssh && wssh --fbidhttp=False'
```

