FROM php:8.0.30-fpm

RUN apt-get update -y && \
    docker-php-ext-install pdo pdo_mysql sockets && \
    apt-get install -y zip unzip libzip-dev libwebp-dev libjpeg-dev libpng-dev libfreetype6-dev libjpeg62-turbo-dev && \
    docker-php-ext-install zip && \
    docker-php-ext-install bcmath && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install -j$(nproc) gd && \
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    mv composer.phar /usr/local/bin/composer

ARG CACHEBUST=1

## Copy all files from your project directory into /var/www/html/CateringService3
COPY CateringService3/ /var/www/html/CateringService3

## Navigate to /var/www/html/CateringService3 and run composer install
WORKDIR /var/www/html/CateringService3
RUN composer update

EXPOSE 9000
