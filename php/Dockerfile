#
# PHP Dockerfile
#
# https://github.com/erheme318/dockerfiles
#

# Pull base image.
FROM erheme318/base

MAINTAINER Erkhembayar Gantulga <erheme318@gmail.com>

# Install apt repository.
RUN add-apt-repository -y ppa:ondrej/php5
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" > /etc/apt/sources.list.d/pgdg.list &&\
  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | \
  apt-key add -

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
RUN echo "deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen" > /etc/apt/sources.list.d/mongodb.list

# Install packages.
RUN apt-get update && \
  apt-get install -y \
  php5-dev \
  php5-cli \
  php5-intl \
  php5-curl \
  php5-gd \
  php5-pgsql \
  php5-sqlite \
  graphicsmagick \
  libgraphicsmagick1-dev

# Install php extensions.
RUN pecl install \
  mongo \
  gmagick-1.1.7RC1 \
  xdebug

# Add modules configs.
ADD *.ini /etc/php5/mods-available/

# Enable php modules.
RUN php5enmod -s ALL mongo symfony gmagick

# Generate FR locale.
RUN locale-gen fr_FR.UTF-8

# Get php package manager.
RUN curl -sS https://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer
