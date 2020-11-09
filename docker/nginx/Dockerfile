FROM nginx:1.17.8-alpine

RUN apk add certbot \
    && mkdir /letsencrypt /cron
COPY docker/nginx/nginx.conf  /etc/nginx/
COPY docker/nginx/default.conf /etc/nginx/conf.d/
RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf
COPY docker/nginx/cron/crontab /cron/crontab
RUN crontab /cron/crontab

EXPOSE 80
EXPOSE 443
