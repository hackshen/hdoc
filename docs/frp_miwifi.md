# 小米路由器后台frp映射

##### frp映射小米路由管理页面到外网 访问的时候一直502，当时的配置是把路由器的80端口映射到了外网，无奈又起了一个nginx做转发这才得以访问（路由器的nginx做了特殊处理）；
##### 但是frp还可以配置通过自定义域名来访问内网的web服务，于是修改了frpc的配置如下：

```bash
# frpc.ini
[miwifi]
type = http
local_port = 80
local_ip = 192.168.31.1
custom_domains = 你的域名
host_header_rewrite = 192.168.31.1
```

##### 上面的`host_header_rewrite`要修改为`miwifi.com` 或者小米路由器地址，不然外网的访问的时候会调跳转到`miwifi.com`这个域名；
##### [rewriting-the-host-header 配置说明](https://github.com/fatedier/frp/tree/v0.29.0?tab=readme-ov-file#rewriting-the-host-header)

