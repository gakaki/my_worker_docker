FROM php:7.1-fpm-alpine

MAINTAINER gakaki <gakaki@qq.com>


RUN echo "http://mirrors.aliyun.com/alpine/latest-stable/main/" > /etc/apk/repositories \
    && apk update \
    && apk add  --no-cache gd-dev pcre-dev linux-headers wget build-base autoconf re2c tar make file \
    libtool git mysql-client curl-dev libmcrypt libmcrypt-dev openssh-client icu-dev \
    libxml2-dev freetype-dev libpng-dev libjpeg-turbo-dev g++ autoconf \
    libgcrypt libcurl libedit ncurses-libs \
    gcc libc-dev pkgconf openssl-dev sqlite-dev \
    && docker-php-source extract \
    && pecl install xdebug redis mongodb yaf swoole-2.0.7 \
    && docker-php-ext-enable xdebug redis mongodb yaf swoole \
    && docker-php-source delete \
    && docker-php-ext-install gd opcache mcrypt pdo_mysql soap intl zip json xml phar \
    iconv mcrypt bcmath dom pcntl \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer config -g repo.packagist composer https://packagist.phpcomposer.com \
    && rm -rf /tmp/*

COPY php_append.ini $PHP_INI_DIR/conf.d/

USER www-data
WORKDIR /var/www

EXPOSE 9000
CMD ["php-fpm"]