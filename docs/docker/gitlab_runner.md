# gitlab Runner

#### [Run GitLab Runner in a container](https://docs.gitlab.com/runner/install/docker.html)

#### 安装

```bash
docker run -d \
  --name gitlab-runner \ 
  --restart always \
  -v /srv/gitlab-runner/config:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:latest
```

#### 注册

```bash
# 进入到runner容器注册
gitlab-runner register --url 'gitlab地址' --registration-token 'token' 
```
