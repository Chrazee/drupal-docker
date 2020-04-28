# Az image alapja
FROM php:7.2-fpm-alpine

# Csomagadatbázis frissítése és csomagok lefrissítése
RUN apk update; \
    apk upgrade;

# Szükséges csomagok a a php extension-okhoz
RUN apk add libxml2-dev libpng-dev

# PHP extension-ok telepítése
RUN docker-php-ext-install pdo pdo_mysql dom gd

# OPCache PHP extension telepítése
RUN docker-php-ext-configure opcache --enable-opcache \
    && docker-php-ext-install opcache

# OPCache config fájl
COPY ./opcache.ini /usr/local/etc/php/conf.d/opcache.ini