FROM php:7.2-fpm

COPY conf /usr/local/etc/php

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    git \
    libz-dev libmemcached-dev libmemcached11 libmemcachedutil2 build-essential memcached \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) mysqli \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && docker-php-ext-install -j$(nproc) zip \
    && docker-php-ext-install -j$(nproc) opcache \
    && pecl install memcached \
    && echo extension=memcached.so >> /usr/local/etc/php/conf.d/memcached.ini

RUN curl -sL https://deb.nodesource.com/setup_8.x | apt-get install -y nodejs

WORKDIR /usr/share/apache2/htdocs/flowbusiness_co

COPY --from=composer:1 /usr/bin/composer /usr/bin/composer
