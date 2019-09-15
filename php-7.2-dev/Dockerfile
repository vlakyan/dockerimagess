FROM registry.gitlab.com/mypie/docker-images/php-7.2:latest

MAINTAINER Vitaly Losev <vitaly.losev93@gmail.com>

RUN apt-get update && apt-get install -y \
    openssl \
    git \
    unzip \
    curl \
    wget \
    make \
    zip

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

COPY conf.d/docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/
COPY conf.d/docker-php-ext-memlimit.ini /usr/local/etc/php/conf.d/

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('SHA384', 'composer-setup.php') === 'a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php --filename=composer \
    && php -r "unlink('composer-setup.php');" \
    && mv composer /usr/local/bin/composer
