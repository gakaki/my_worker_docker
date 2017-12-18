FROM docker.elastic.co/elasticsearch/elasticsearch:6.0.1

COPY --chown=elasticsearch:elasticsearch elasticsearch.yml /usr/share/elasticsearch/config/

# 注意在国外速度超慢
# https://github.com/elastic/elasticsearch-docker
# elastic search 官方dockerfile地址


# 安装 elasticsearch ik 插件

MAINTAINER gakaki <gakaki@qq.com>

RUN echo "http://mirrors.aliyun.com/alpine/latest-stable/main/" > /etc/apk/repositories \
    && apk update \
    && apk add  --no-cache gd-dev pcre-dev linux-headers wget build-base autoconf re2c tar make file \
    libtool git mysql-client curl-dev libmcrypt libmcrypt-dev openssh-client icu-dev \
    libxml2-dev freetype-dev libpng-dev libjpeg-turbo-dev g++ autoconf \
    libgcrypt libcurl libedit ncurses-libs \
    gcc libc-dev pkgconf openssl-dev sqlite-dev \
    && docker-php-source extract

# XDEBUG NOT SUPPORT 7.2 RC VERSION using the git version can be mcrypt is delete from php72
RUN pecl install redis mongodb yaf swoole-2.0.9 \
    && docker-php-ext-enable redis mongodb yaf swoole \
    && docker-php-source delete \
    && docker-php-ext-install curl gd opcache  pdo_mysql soap intl zip json xml phar \
    iconv  bcmath dom pcntl \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer config -g repo.packagist composer https://packagist.phpcomposer.com \
    && rm -rf /tmp/*

COPY php_append.ini $PHP_INI_DIR/conf.d/

USER www-data
WORKDIR /var/www

EXPOSE 9000
CMD ["php-fpm"]


# docker tag 7d9495d03763 gc/php:latest

