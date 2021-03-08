FROM nginx

# Metadata
LABEL org.label-schema.url="https://www.nginx.com" \
      org.label-schema.name="Nginx-Webui" \
      org.label-schema.description="Webui" \
      org.label-schema.docker.schema-version="1.0"

RUN apt-get update \
  && apt-get install -y apt-utils \
  && apt-get install -y git \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/hukoeth/Youtube-dl-WebUI /www

COPY default.conf /etc/nginx/conf.d/
COPY config.php /www/config/

EXPOSE 8080

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]