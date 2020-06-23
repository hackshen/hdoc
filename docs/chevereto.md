# 使用chevereto通过docker搭建图床
> [docker hub地址](https://hub.docker.com/r/nmtan/chevereto)

### Docker compose

```bash
version: '3'

services:
  db:
    image: mariadb
    volumes:
      - database:/var/lib/mysql:rw
    restart: always
    networks:
      - private
    environment:
      MYSQL_ROOT_PASSWORD: chevereto_root
      MYSQL_DATABASE: chevereto
      MYSQL_USER: chevereto
      MYSQL_PASSWORD: chevereto

  chevereto:
    depends_on:
      - db
    image: nmtan/chevereto
    restart: always
    networks:
      - private
    environment:
      CHEVERETO_DB_HOST: db
      CHEVERETO_DB_USERNAME: chevereto
      CHEVERETO_DB_PASSWORD: chevereto
      CHEVERETO_DB_NAME: chevereto
      CHEVERETO_DB_PREFIX: chv_
    volumes:
      - chevereto_images:/var/www/html/images:rw
    ports:
      - 8080:80

networks:
  private:
volumes:
  database:
  chevereto_images:
```
