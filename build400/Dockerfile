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


#ADD jdk-9.0.1_linux-x64_bin.tar.gz /src/jdk/
#RUN mkdir -p /usr/lib/jvm/ && \
#  mv /src/jdk/jdk-9.0.1 /usr/lib/jvm/ && \
#  update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk-9.0.1/bin/javac 1 && \
#  update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-9.0.1/bin/java 1 && \
#  update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/jdk-9.0.1/bin/javaws 1

#RUN groupadd -r --gid 1000 builder && useradd -r --uid 1000 -g builder -G audio,video builder \
#    && mkdir -p /home/builder/Downloads && chown -R builder:builder /home/builder
#USER builder

RUN sed 's/main$/main universe/' -i /etc/apt/sources.list && \
    apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:webupd8team/java -y && \
    apt-get update && \
    echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
    apt-get install -y oracle-java8-installer libxext-dev libxrender-dev libxtst-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*

# Install libgtk as a separate step so that we can share the layer above with
# the netbeans image
RUN apt-get update && apt-get install -y libgtk2.0-0 libcanberra-gtk-module

RUN wget http://eclipse.c3sl.ufpr.br/technology/epp/downloads/release/luna/SR1/eclipse-java-luna-SR1-linux-gtk-x86_64.tar.gz -O /tmp/eclipse.tar.gz -q && \
    echo 'Installing eclipse' && \
    tar -xf /tmp/eclipse.tar.gz -C /opt && \
    rm /tmp/eclipse.tar.gz

ADD run /usr/local/bin/eclipse

RUN chmod +x /usr/local/bin/eclipse && \
    mkdir -p /home/developer && \
    echo "developer:x:1000:1000:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:1000:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown developer:developer -R /home/developer && \
    chown root:root /usr/bin/sudo && chmod 4755 /usr/bin/sudo

USER developer
ENV HOME /home/developer
WORKDIR /home/developer
CMD /usr/local/bin/eclipse

