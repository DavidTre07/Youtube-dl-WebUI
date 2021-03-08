FROM bitnami/php-fpm

LABEL org.label-schema.url="https://github.com/hukoeth/Youtube-dl-WebUI" \
      org.label-schema.name="youtube-dl-webui-php" \
      org.label-schema.description="Youtube-dl-webui-php" \
      org.label-schema.docker.schema-version="1.0"

RUN install_packages curl ca-certificates ffmpeg python\
  && groupadd --gid 1001 ydl \
  && useradd --uid 1001 --gid ydl ydl

COPY common.conf /opt/bitnami/php/etc/common.conf

RUN curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl \
  && chmod +x /usr/local/bin/youtube-dl

EXPOSE 9000

#With this following line, a restart of docker will update yutube-dl
CMD youtube-dl -U && php-fpm --nodaemonize