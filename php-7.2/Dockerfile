FROM php:7.2-fpm

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
    libmemcached-dev \
    git

RUN pecl install xdebug \
    && pecl install ssh2-1.1.2 \
    && pecl install mcrypt-1.0.2

RUN docker-php-ext-install pdo \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install calendar \
    && docker-php-ext-install intl \
    && docker-php-ext-install gd \
    && docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
    && docker-php-ext-install imap \
    && docker-php-ext-install xsl \
    && docker-php-ext-install xml \
    && docker-php-ext-install simplexml \
    && docker-php-ext-install xmlwriter \
    && docker-php-ext-install xmlrpc \
    && docker-php-ext-install zip \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install bz2 \
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
    && docker-php-ext-enable bz2 \
    && docker-php-ext-enable ssh2

COPY conf.d/docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('SHA384', 'composer-setup.php') === 'a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php --filename=composer \
    && php -r "unlink('composer-setup.php');" \
    && mv composer /usr/local/bin/composer

WORKDIR /var/www