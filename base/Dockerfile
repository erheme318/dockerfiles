#
# Base Dockerfile
#
# https://github.com/erheme318/dockerfiles
#

# Pull base image.
FROM ubuntu:precise

MAINTAINER Erkhembayar Gantulga <erheme318@gmail.com>

RUN LANG="en_US.UTF-8"
RUN echo "export LANG=fr_FR.UTF-8" >> ~/.bashrc

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 36A1D7869245C8950F966E92D8576A8BA88D21E9
RUN apt-get update

# Install base.
RUN apt-get install -y python-software-properties &&\
  apt-get install -y \
  wget \
  curl \
  vim \
  git-core \
  openssh-server

# gather github.com ssh public key
RUN mkdir /root/.ssh/ \
    && ssh-keyscan github.com >> /root/.ssh/known_hosts
