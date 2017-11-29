FROM ubuntu:12.04.5

RUN apt-get update
RUN apt-get install -y \
  build-essential \
  libreadline-dev \
  libcurses-ocaml-dev \
  file

RUN apt-get autoclean \
  && apt-get autoremove \
  && rm -rf /var/lib/apt/lists/*



