#
# Vim plugin development Dockerfile
#
# https://github.com/erheme318/dockerfiles
#

# Pull base image.
FROM debian:jessie

RUN echo 'deb http://httpredir.debian.org/debian jessie main' > /etc/apt/sources.list

# Install dependencies
RUN apt-get update \
  && apt-get install --no-install-recommends -q -o Dpkg::Options::="--force-confold" --force-yes -y \
  libncurses5-dev  libgnome2-dev libgnomeui-dev \
  libgtk2.0-dev libatk1.0-dev libbonoboui2-dev \
  libcairo2-dev libx11-dev libxpm-dev \
  libxt-dev python-dev python3-dev \
  openssh-server \
  make \
  gcc \
  git

RUN mkdir /root/.ssh/ \
  && ssh-keyscan github.com >> /root/.ssh/known_hosts

# Compile vim
RUN git clone git://github.com/vim/vim.git

WORKDIR "/vim"
RUN ./configure --with-features=huge --enable-cscope --enable-gui=auto
RUN make install

# Install Vroom
RUN git clone git://github.com/google/vroom.git /vroom
WORKDIR "/vroom"
RUN python3 setup.py build && python3 setup.py install

CMD /bin/bash
