FROM php:7.2-fpm
RUN apt-get update \
  && apt-get install -y git libzip-dev zip unzip libicu-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
  && docker-php-ext-install zip \
  && docker-php-ext-install pdo_mysql \
  && docker-php-ext-configure intl \
  && docker-php-ext-install intl \
  && docker-php-ext-configure gd \
  && docker-php-ext-install gd

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html
