#
# Nginx Dockerfile
#
# https://github.com/erheme318/dockerfiles
#

# Pull base image.
FROM nginx:1.9

MAINTAINER Erkhembayar Gantulga <erheme318@gmail.com>

COPY nginx.conf /etc/nginx/nginx.conf

# Copy virtual host configuration
COPY app.conf /etc/nginx/sites-available/

# Create symbolic link
RUN mkdir /etc/nginx/sites-enabled
RUN ln -s /etc/nginx/sites-available/app.conf /etc/nginx/sites-enabled/app

# Set default user
RUN usermod -u 1000 www-data

# Set default home directory
WORKDIR /var/www
