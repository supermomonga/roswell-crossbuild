FROM debian:latest
MAINTAINER supermomonga

## Install dependencies
## automake, build-essential and libcurl for roswell
## zlib1g for sbcl
RUN apt-get update\
    && apt-get install -y automake git build-essential libcurl4-openssl-dev zlib1g-dev\
    && rm -rf /var/lib/apt/lists/*

## Install roswell
RUN git clone git://github.com/snmsts/roswell.git\
    && cd roswell\
    && sh bootstrap\
    && ./configure\
    && make\
    && make install\
    && ros setup

RUN ros install sbcl --verbose

CMD ros version