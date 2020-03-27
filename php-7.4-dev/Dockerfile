FROM registry.gitlab.com/mypie/docker-images/php-7.4:latest

MAINTAINER Vitaly Losev <vitaly.losev93@gmail.com>

RUN apt-get update && apt-get install -y \
    openssl \
    git \
    unzip \
    curl \
    wget \
    make \
    zip

RUN pecl install xdebug

COPY conf.d/docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/
COPY conf.d/docker-php-ext-memlimit.ini /usr/local/etc/php/conf.d/
COPY conf.d/docker-php-ext-opcache.ini /usr/local/etc/php/conf.d/

RUN docker-php-ext-enable opcache \
    && docker-php-ext-enable xdebug

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('SHA384', 'composer-setup.php') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php --filename=composer \
    && php -r "unlink('composer-setup.php');" \
    && mv composer /usr/local/bin/composer
