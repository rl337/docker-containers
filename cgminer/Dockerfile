FROM aarch64/debian:stretch-slim

MAINTAINER	Richard Lee <rlee@tokyo3.com>

ENV	LD_LIBRARY_PATH=/usr/lib32:${LIBRARY_PATH}

RUN		apt-get update -qq

RUN		apt-get -qqy install autoconf autogen libtool uthash-dev libjansson-dev libcurl4-openssl-dev libusb-dev libncurses-dev git-core
RUN		apt-get -qqy install libgcrypt20 libgcrypt20-dev pkg-config libevent-2.0-5 libevent-dev ocl-icd-opencl-dev build-essential
RUN		apt-get -qqy install libusb-1.0

RUN		git clone https://github.com/vthoang/cgminer.git
RUN             cd cgminer && CFLAGS="-O2" ./autogen.sh --enable-gekko
RUN             cd cgminer && make -j 2

WORKDIR		/cgminer
ENTRYPOINT	["./cgminer"]

