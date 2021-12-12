> Chrome58以后对https的证书认证较为严格，证书里必须带有正确的Common Name，也就是必须有Subject Alternative Name. [Google官网介绍链接地址](https://support.google.com/chrome/a/answer/7391219?hl=zh-Hans)

#### 本机环境
- Mac： 10.12.6
- NGINX：nginx/1.12.2
- nginx 配置文件

    ```javscript
    server {
        listen       80;
        server_name  git.hackshen.com;
        #charset koi8-r;
        #access_log  logs/host.access.log  main;
        location / {
            root   /Users/hackshen/nginx-web/;
            index  index.html index.htm;
        }
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    }

    server {
        listen 443;
        server_name git.hackshen.com;
        ssl on;
        ssl_certificate  /usr/local/etc/nginx/hackshen.crt;
        ssl_certificate_key  /usr/local/etc/nginx/hackshen.key;
        location / {
             root   /Users/hackshen/nginx-web;
             index  index.html index.htm;
        }
    }
    ```

#### 生成证书

1、在[ req ]一节下找到req_extensions = v3_req 取消注释
2、在[ v3_req ] 一节 增加 subjectAltName = @alt_names
3、在[ v3_req ] 一节 的上方增加一节
    DNS.1 = i.alicdn.com
    IP.1 = 127.0.0.1
4、生成csr

```bash
openssl req -new -nodes -keyout server.key -out server.csr -config openssl.cnf
```
5、生成公钥

```bash
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt -extensions v3_req -extfile openssl.cnf
```

6、关于 [`openssl.cnf 点我`](./document/openssl.cnf)


#### 安装证书
- 双击`server.crt`安装证书到钥匙串里，且在钥匙串里面要选择`始终信任`



