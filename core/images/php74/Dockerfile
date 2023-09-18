FROM php:7.4.33-fpm

MAINTAINER peter <peter@xulukun.cn>

RUN apt-get update

RUN apt-get install -y vim

# 安装 GD 库
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev libwebp-dev && \
    docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp && \
    docker-php-ext-install -j$(nproc) gd

# 安装 intl
RUN apt-get install -y libicu-dev && docker-php-ext-install intl

# 安装 simplexml
RUN apt-get install -y libxml2-dev && docker-php-ext-install simplexml

# 安装 soap
RUN apt-get install -y libssl-dev && docker-php-ext-install soap

# 安装 xsl
RUN apt-get install -y libxslt-dev && docker-php-ext-install xsl

# 安装 zip
RUN apt-get install -y zlib1g-dev libzip-dev && docker-php-ext-install zip

# 安装其他扩展
RUN docker-php-ext-install mysqli pdo_mysql bcmath xsl opcache

# 开启 PNG、JPEG 支持
RUN docker-php-ext-install exif

# Set Workdir
WORKDIR /var/www/html

# Expose ports
EXPOSE 9000

# Entry point
CMD ["php-fpm", "-R", "--nodaemonize"]