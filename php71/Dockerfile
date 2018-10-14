FROM alpine:latest

MAINTAINER peter <peter@xulukun.cn>

# Environments
# ENV TIMEZONE            Asia/Jakarta
# ENV PHP_MEMORY_LIMIT    512M
# ENV MAX_UPLOAD          50M
# ENV PHP_MAX_FILE_UPLOAD 200
# ENV PHP_MAX_POST        100M

# Mirror mirror switch to Ali-OSM (Alibaba Open Source Mirror Site) - http://mirrors.aliyun.com/
RUN echo 'https://mirrors.aliyun.com/alpine/v3.7/main' > /etc/apk/repositories  && \
	echo 'https://mirrors.aliyun.com/alpine/v3.7/community' >> /etc/apk/repositories
	# && echo "http://dl-4.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories

# ensure www-data user exists
RUN set -x \
	&& addgroup -g 82 -S www-data \
	&& adduser -u 82 -D -S -G www-data www-data
# 82 is the standard uid/gid for "www-data" in Alpine

RUN apk update && apk upgrade && \
    apk add --update --no-cache \
        php7 \
		php7-common \
		php7-cgi \
		php7-dev \
		php7-doc \
		php7-ftp \
		php7-pcntl \
		php7-pear \
		php7-sockets \
		php7-tokenizer \
		php7-xml \
        php7-mbstring \
        php7-intl \
        php7-fileinfo \
		php7-simplexml \
		php7-xsl \
		php7-phar \
		php7-xmlwriter \
		php7-session \
        php7-mcrypt \
		php7-soap \
		php7-openssl \
		php7-gmp \
		php7-pdo_odbc \
		php7-json \
		php7-dom \
		php7-pdo \
		php7-zip \
		php7-mysqli \
		php7-sqlite3 \
		php7-pdo_pgsql \
		php7-bcmath \
		php7-gd \
		php7-odbc \
		php7-pdo_mysql \
		php7-pdo_sqlite \
		php7-gettext \
		php7-xmlreader \
		php7-xmlrpc \
		php7-bz2 \
		php7-iconv \
		php7-pdo_dblib \
		php7-curl \
		php7-ctype \
		php7-fpm \
        php7-opcache && \
# Cleaning up
    # mkdir -p /www && \
    # apk del tzdata && \
    rm -rf /var/cache/apk/*

# Set Workdir
WORKDIR /var/www/html

# Expose ports
EXPOSE 9000

# Entry point
CMD ["/usr/sbin/php-fpm7", "-R", "--nodaemonize"]