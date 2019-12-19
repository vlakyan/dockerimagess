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

RUN pecl install xdebug

COPY conf.d/docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/
COPY conf.d/docker-php-ext-memlimit.ini /usr/local/etc/php/conf.d/

RUN docker-php-ext-enable xdebug

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('SHA384', 'composer-setup.php') === 'baf1608c33254d00611ac1705c1d9958c817a1a33bce370c0595974b342601bd80b92a3f46067da89e3b06bff421f182') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php --filename=composer \
    && php -r "unlink('composer-setup.php');" \
    && mv composer /usr/local/bin/composer
