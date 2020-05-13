# docker-compose Using environment variables in nginx configuration

> 想在docker-compose里面配置nginx的变量，参考了dockerhub nginx的文档[文档地址](https://hub.docker.com/_/nginx/)  内容如下

```bash
# 官方Demo
web:
  image: nginx
  volumes:
   - ./mysite.template:/etc/nginx/conf.d/mysite.template
  ports:
   - "8080:80"
  environment:
   - NGINX_HOST=foobar.com
   - NGINX_PORT=80
  command: /bin/bash -c "envsubst < /etc/nginx/conf.d/mysite.template > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"
```

按照官方给的文档我顺利的解决了NGINX传递变量的问题，但是配置文件mysite.template里面比如有些NGINX自己的变量比如 $request_uri、$server_name 都会被替换为空，既然这样我们就替换我们需要的变量

```bash
"envsubst < /etc/nginx/conf.d/mysite.template > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"
# 将上面的代码修改为
"envsubst '$NGINX_HOST $NGINX_PORT' < /etc/nginx/conf.d/mysite.template > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"
```

但是这样并没解决我的问题，NGINX报错找不到这个变量，又是一顿谷够，找到了一片文档[传送门](https://github.com/docker-library/docs/issues/496)按照大神的意思是需要对变量转义，如下

```bash
"envsubst '$$NGINX_HOST $$NGINX_PORT' < /etc/nginx/conf.d/mysite.template > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"
```
至此顺利的解决了我的问题
