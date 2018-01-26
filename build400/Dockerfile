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

RUN apt-get install -y \
  cppcheck \
  libx11-dev \
  software-properties-common \
  libxext-dev \
  libxrender-dev \
  libxtst-dev \
  libgtk2.0-0 \
  libcanberra-gtk-module

RUN apt-get install -y \
  scite \
  vim

ADD jdk-9.0.1_linux-x64_bin.tar.gz /src/jdk/
RUN mkdir -p /usr/lib/jvm/ && \
  mv /src/jdk/jdk-9.0.1 /usr/lib/jvm/ && \
  update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-9.0.1/bin/javac 1 && \
  update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-9.0.1/bin/java 1 && \
  update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/jdk-9.0.1/bin/javaws 1


# Install libgtk as a separate step so that we can share the layer above with
# the netbeans image
RUN apt-get install -y libgtk2.0-0 libcanberra-gtk-module

RUN apt-get install -y \
  supervisor

RUN apt-get install -y \
  openssh-server pwgen sudo vim-tiny

RUN apt-get install -y \
  net-tools

RUN apt-get install -y \
  gtk2-engines-murrine

RUN apt-get install -y \
  nginx

RUN apt-get install -y \
  python-pip python-dev build-essential

RUN apt-get install -y \
  gtk2-engines-pixbuf gtk2-engines-murrine

RUN apt-get install -y \
  dbus-x11 x11-utils
  
RUN apt-get install -y \
  x11vnc
  
RUN apt-get install -y \
  xvfb

#RUN apt-get install -y \
#  lxde

RUN apt-get install -y \
  mesa-utils libgl1-mesa-dri
  
RUN apt-get install -y \
  ttf-ubuntu-font-family \
  fonts-wqy-microhei \
  gnome-themes-standard

RUN apt-get autoclean \
  && apt-get autoremove \
  && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /home/developer && \
    echo "developer:x:1000:1000:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:1000:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown developer:developer -R /home/developer && \
    chown root:root /usr/bin/sudo && chmod 4755 /usr/bin/sudo

USER developer
ENV HOME /home/developer
WORKDIR /home/developer


