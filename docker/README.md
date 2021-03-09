# Youtube-dl-webui

## Prepare webui

- clone repo

  ```bash
  cd /data/ydl
  git clone https://... www
  ```

- Adapt configuration

  ```bash
  cd www/config
  cp config.sample.php config.php
  vi config.php
  ```

  You can find an example of a working config.php in this folder

## Build docker images

```bash
cd www/docker/php
docker build -t ydl-webui-php:latest .
```

## Example on how to use it with docker-compose

```yml
version: "3"
services:
  ydl-nginx:
    image: nginx
    container_name: ydl-nginx
    volumes:
      - /data/ydl/download:/download/:rw
      - /data/ydl/logs:/logs:rw
      - /etc/localtime:/etc/localtime:ro
      - /data/ydl/www:/www:rw
    ports:
      - 80:80
    restart: always

  ydl-php:
    image: ydl-webui-php:latest
    container_name: ydl-php
    volumes:
      - /data/ydl/download:/download:rw
      - /data/ydl/logs:/logs:rw
      - /data/ydl/www:/www:rw
    ports:
      - 9000:9000
    restart: always
```
