FROM ubuntu:16.04

RUN apt-get update && apt-get install -y \
  make \
  unzip \
  bc \
  nodejs \
  npm \
  luajit \
  lib32z1 \
  gcc-multilib \
  mtd-utils \
  subversion \
  patch \
  patchutils \
  bison \
  libc6-dev \
  libxml-dom-perl \
  zlib1g \
  zlib1g-dev \
  libcurl4-openssl-dev \
  libncurses5 \
  python-numpy \
  doxygen \
  libpcre3-dev \
  php7.0-cli

RUN npm i -gq grunt-cli bower coveralls
RUN ln -s nodejs /usr/bin/node
RUN ln -fs bash /bin/sh

