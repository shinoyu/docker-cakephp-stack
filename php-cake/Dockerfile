FROM php:7.2-apache

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt-get update && \
  docker-php-ext-install pdo_mysql mysqli mbstring
RUN a2enmod rewrite