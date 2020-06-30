FROM node:12-alpine3.12 AS node
FROM php:7.3-fpm

ARG DOCKER_UID=1000
ARG DOCKER_USER=docker
ARG DOCKER_PASSWORD=docker

RUN apt-get update \
  && apt-get install -y git zip unzip libicu-dev sudo \
  && apt-get install -y vim \
  && docker-php-ext-install pdo_mysql intl mbstring

COPY --from=node /usr/local/bin/node /usr/local/bin/
COPY --from=node /usr/local/lib/node_modules/ /usr/local/lib/node_modules/
COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN useradd -m --uid ${DOCKER_UID} --groups sudo ${DOCKER_USER} \
  && echo ${DOCKER_USER}:${DOCKER_PASSWORD} | chpasswd

USER ${DOCKER_USER}

WORKDIR /var/www/html