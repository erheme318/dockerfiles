#
# Dockerfile
#
# https://github.com/erheme318/dockerfiles
#

# Pull base image.
FROM erheme318/php

MAINTAINER Erkhembayar Gantulga <erheme318@gmail.com>

# Install packages.
RUN apt-get update && \
  apt-get install -y \
  php5-fpm

ADD app.pool.conf /etc/php5/fpm/pool.d/

RUN usermod -u 1000 www-data

EXPOSE 9000

WORKDIR /var/www

CMD ["php5-fpm","-F"]
