FROM nginx

ARG CACHEBUST=1

ADD docker/nginx/default.conf /etc/nginx/conf.d/default.conf

COPY CateringService3/public/ /var/www/html/CateringService3/public

EXPOSE 80
