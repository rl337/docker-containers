FROM aarch64/debian:stretch-slim

MAINTAINER	Richard Lee <rlee@tokyo3.com>

RUN		apt-get update -qq

RUN		apt-get install -qqy gcc automake libtool pkg-config libcurl4-gnutls-dev libudev-dev yasm git make

RUN		git clone https://github.com/ghostlander/nsgminer.git

RUN		cd nsgminer && ./autogen.sh
RUN		cd nsgminer && ./configure CFLAGS="-O3"
RUN		cd nsgminer && make

WORKDIR		/nsgminer
ENTRYPOINT	["./nsgminer"]
