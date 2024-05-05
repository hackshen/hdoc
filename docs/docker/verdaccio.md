# [verdaccio](https://github.com/verdaccio/verdaccio)

> Verdaccio是一个简单的、无需配置的本地私有npm注册表。不需要一个完整的数据库才开始!
> Verdaccio开箱即用，拥有自己的小型数据库，并且能够代理其他注册表(例如。Npmjs.org)
> ，在此过程中缓存下载的模块。对于那些希望扩展存储能力的人来说，Verdaccio支持各种社区制作的插件，可以连接到亚马逊的s3、谷歌云存储等服务，或者创建自己的插件。

#### [Installation](https://verdaccio.org/docs/installation/)

```bash
# 注册环境变量
V_PATH=$PWD/verdaccio
docker run -it --rm --name verdaccio \
  -p 4873:4873 \
  -v $V_PATH/conf:/verdaccio/conf \
  -v $V_PATH/storage:/verdaccio/storage \
  -v $V_PATH/plugins:/verdaccio/plugins \
  verdaccio/verdaccio
```
