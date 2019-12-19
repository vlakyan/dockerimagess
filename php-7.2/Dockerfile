FROM php:7.2-fpm

MAINTAINER Vitaly Losev <vitaly.losev93@gmail.com>

RUN apt-get update && \
    apt-get install -y \
    zlib1g-dev \
    libmcrypt-dev \
    libicu-dev \
    libgd-dev \
    libc-client-dev \
    libkrb5-dev \
    libxslt-dev \
    libbz2-dev \
    libssh2-1-dev \
    libmemcached-dev

RUN pecl install ssh2-1.1.2 \
    && pecl install mcrypt-1.0.2

RUN docker-php-ext-install pdo \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install calendar \
    && docker-php-ext-install intl \
    && docker-php-ext-install gd \
    && docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
    && docker-php-ext-configure pcntl --enable-pcntl \
    && docker-php-ext-install imap \
    && docker-php-ext-install xsl \
    && docker-php-ext-install xml \
    && docker-php-ext-install simplexml \
    && docker-php-ext-install xmlwriter \
    && docker-php-ext-install xmlrpc \
    && docker-php-ext-install zip \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install bz2 \
    && docker-php-ext-install pcntl \
    && docker-php-ext-enable intl \
    && docker-php-ext-enable gd \
    && docker-php-ext-enable imap \
    && docker-php-ext-enable xsl \
    && docker-php-ext-enable xml \
    && docker-php-ext-enable simplexml \
    && docker-php-ext-enable xmlwriter \
    && docker-php-ext-enable xmlrpc \
    && docker-php-ext-enable zip \
    && docker-php-ext-enable bcmath \
    && docker-php-ext-enable pcntl \
    && docker-php-ext-enable bz2 \
    && docker-php-ext-enable ssh2

WORKDIR /var/www