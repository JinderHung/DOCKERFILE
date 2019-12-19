FROM ubuntu:16.04

RUN apt-get update && apt-get install -y \
  software-properties-common gcc-multilib mtd-utils subversion patch patchutils bison libc6-dev rand bc openssh-client libxml-dom-perl zlib1g zlib1g-dev libz-dev libcurl4-openssl-dev libncurses5 libncurses5 python-numpy doxygen cppcheck libpcre3-dev php7.0-cli wget curl make autoconf automake libtool m4 flex rsync python3-dev python-dev python-pip ruby util-linux fakeroot unzip lcov
RUN apt-get install -y git pkg-config lib32z1

RUN apt-get autoremove
RUN apt-get clean

RUN pip install --upgrade pip
RUN pip install boto logging argparse
#RUN easy_install hashlib
RUN pip install sentry-sdk
RUN pip install gitpython
