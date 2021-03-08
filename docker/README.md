# Youtube-dl-webui

## Build docker images

```bash
cd docker/nginx
docker build -t ydl-webui-nginx:latest .
cd docker/php
docker build -t ydl-webui-php:latest .
```

## Example on how to use it with docker-compose

```yml
version: "3"
services:
  ydl-nginx:
    image: ydl-webui-nginx:latest
    container_name: ydl-nginx
    volumes:
      - /data/ydl/download:/download/:rw
      - /data/ydl/logs:/logs:rw
      - /etc/localtime:/etc/localtime:ro
#      - /data/docker/config/ydl/www:/www:rw
    ports:
      - 80:80
    restart: always

  ydl-php:
    image: ydl-webui-php:latest
    container_name: ydl-php
    volumes:
      - /data/ydl/download:/download:rw
      - /data/ydl/logs:/logs:rw
#      - /data/docker/config/ydl/www:/www:rw
    restart: always
```
