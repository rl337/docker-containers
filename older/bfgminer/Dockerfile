FROM aarch64/debian:stretch-slim

MAINTAINER	Richard Lee <rlee@tokyo3.com>

ENV	LD_LIBRARY_PATH=/usr/lib32:${LIBRARY_PATH}

RUN		apt-get update -qq

RUN		apt-get -qqy install autoconf autogen libtool uthash-dev libjansson-dev libcurl4-openssl-dev libusb-dev libncurses-dev git-core
RUN		apt-get -qqy install libgcrypt20 libgcrypt20-dev pkg-config libevent-2.0-5 libevent-dev build-essential
RUN		apt-get -qqy install libusb-1.0

# RUN		git clone https://github.com/luke-jr/bfgminer.git
RUN             git clone https://github.com/jstefanop/bfgminer.git
RUN             cd bfgminer && git checkout futurebit2_driver
#RUN             cd bfgminer && git checkout bfgminer-5.4.2-futurebit2-beta2
#RUN             curl https://codeload.github.com/jstefanop/bfgminer/tar.gz/bfgminer-5.4.2-futurebit2-beta2 -o bfgminer-5.4.2-futurebit2-beta2.tar.gz
#RUN             tar xvfz bfgminer-5.4.2-futurebit2-beta2.tar.gz
#RUN             mv bfgminer-bfgminer-5.4.2-futurebit2-beta2 bfgminer
RUN             cd bfgminer && touch version.h
RUN             cd bfgminer && ./autogen.sh --enable-futurebit --enable-scrypt
RUN             cd bfgminer && ./configure --enable-futurebit --enable-scrypt
RUN             cd bfgminer && make

WORKDIR		/bfgminer
ENTRYPOINT	["./bfgminer"]

