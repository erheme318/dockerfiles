#
# Dockerfile
#
# https://github.com/erheme318/dockerfiles
#

# Pull base image.
FROM php:5.6-fpm

MAINTAINER Erkhembayar Gantulga <erheme318@gmail.com>

# Install packages.
RUN apt-get update && \
  apt-get install -y \
  git \
  wget \
  vim

ADD app.pool.conf /etc/php5/fpm/pool.d/

# Add modules configs.
ADD *.ini /usr/local/etc/php/conf.d/

# Install extensions
RUN docker-php-ext-install pdo_mysql

# Install PHP package manager
ADD scripts/composer.sh /var/www/composer.sh
RUN bash /var/www/composer.sh

RUN usermod -u 1000 www-data

WORKDIR /var/www
