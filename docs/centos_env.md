# About centos env

#### Install git
```bash
yum install git -y
```

#### Install zsh
- [Go to mac_env Install zsh](https://github.com/hackshen/hdoc/blob/master/docs/mac_env.md#%E5%AE%89%E8%A3%85-oh-my-zsh)

#### Install docker
- [https://docs.docker.com/install/linux/docker-ce/centos/](https://docs.docker.com/install/linux/docker-ce/centos/)

#### Install docker-compose
```bash
# install
sudo curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.4/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

# Add permissions
sudo chmod +x /usr/local/bin/docker-compose
```
