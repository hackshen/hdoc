# docker portainer

#### [Install Portainer CE with Docker on Linux](https://docs.portainer.io/start/install-ce/server/docker/linux)

```bash
docker run -d \
  -p 8000:8000 \
  -p 9443:9443 \
  -p 9000:9000 \
  --name portainer \ 
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data portainer/portainer-ce:latest
```
