FROM ubuntu:18.04

RUN apt-get update && \
    apt-get install -y \
    unzip \
    php7.2-bcmath \
    php7.2-cli \
    php7.2-curl \
    php7.2-gd \
    php7.2-imap \
    php7.2-intl \
    php7.2-fileinfo \
    php7.2-mbstring \
    php7.2-mysql \
    php7.2-xml \
    php7.2-zip \
    php7.2-igbinary \
    php7.2-ssh2 \
    php7.2-xdebug

COPY conf.d/ /etc/php/7.2/mods-available/

RUN phpdismod xdebug \
    && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && php -r "unlink('composer-setup.php');" \
    && composer clear-cache > /dev/null \
    && rm -rf /tmp/*
