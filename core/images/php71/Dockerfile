FROM mhart/alpine-node:10.15.0

MAINTAINER peter <peter@xulukun.cn>

RUN npm install -g cnpm --registry=https://registry.npm.taobao.org && \
    yarn config set registry https://registry.npm.taobao.org && \
    cnpm i -g grunt-cli

# Mirror mirror switch to Ali-OSM (Alibaba Open Source Mirror Site) - http://mirrors.aliyun.com/
RUN echo 'https://mirrors.aliyun.com/alpine/v3.7/main' > /etc/apk/repositories  && \
	echo 'https://mirrors.aliyun.com/alpine/v3.7/community' >> /etc/apk/repositories
	# && echo "http://dl-4.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories

# ensure www-data user exists
RUN set -x \
	&& addgroup -g 1000 -S www-data \
	&& adduser -u 1000 -D -S -G www-data www-data
# 1000 is the standard uid/gid for "www-data" in Alpine

RUN apk update && apk upgrade && \
    apk add --update --no-cache \
        curl \
        php7 \
		php7-common \
        php7-fpm \
        php7-dom \
        php7-mbstring \
        php7-json \
        php7-bcmath \
        php7-ctype \
        php7-curl \ 
        php7-gd \ 
        php7-intl \
        php7-mcrypt \
        php7-openssl \
        php7-pdo \
        php7-pdo_mysql \
        php7-simplexml \
        php7-soap \
        php7-xsl \ 
        php7-zip \
        php7-iconv \
        php7-phar \ 
        php7-xmlwriter \
        php7-opcache \
        php7-tokenizer \
        php7-session \
        php7-fileinfo \
        php7-xml && \
# Cleaning up
    rm -rf /var/cache/apk/*

# Set Workdir
WORKDIR /var/www/html

# Expose ports
EXPOSE 9000

# Entry point
CMD ["/usr/sbin/php-fpm7", "-R", "--nodaemonize"]