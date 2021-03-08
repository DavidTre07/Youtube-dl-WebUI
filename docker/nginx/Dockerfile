FROM nginx

# Metadata
LABEL org.label-schema.url="https://www.nginx.com" \
      org.label-schema.name="Nginx-Webui" \
      org.label-schema.description="Webui" \
      org.label-schema.docker.schema-version="1.0"

COPY default.conf /etc/nginx/conf.d/

EXPOSE 8080

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]