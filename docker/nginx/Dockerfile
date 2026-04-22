FROM nginx:alpine
WORKDIR /app
RUN apk update && apk upgrade --no-cache && \
    touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid /var/cache/nginx /var/log/nginx
COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf
RUN chown nginx:nginx /etc/nginx/conf.d/default.conf
USER nginx
HEALTHCHECK --interval=10s --timeout=3s \
  CMD curl -f http://localhost || exit 1