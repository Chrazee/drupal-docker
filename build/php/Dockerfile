FROM php:7.4-fpm-alpine

RUN apk update; \
    apk upgrade;

RUN apk add libxml2-dev libpng-dev

RUN docker-php-ext-install pdo pdo_mysql dom gd

RUN docker-php-ext-configure opcache --enable-opcache \
    && docker-php-ext-install opcache

COPY ./opcache.ini /usr/local/etc/php/conf.d/opcache.ini