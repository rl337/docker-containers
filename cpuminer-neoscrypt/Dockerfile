#
# Dockerfile for cpuminer
# usage: docker run creack/cpuminer --url xxxx --user xxxx --pass xxxx
# ex: docker run creack/cpuminer --url stratum+tcp://ltc.pool.com:80 --user creack.worker1 --pass abcdef
#
#

#FROM		ubuntu:12.10
FROM arm32v7/debian:stretch-slim

MAINTAINER	Guillaume J. Charmes <guillaume@charmes.net>

RUN		apt-get update -qq

RUN		apt-get install -qqy gcc
RUN		apt-get install -qqy automake
RUN		apt-get install -qqy libcurl4-openssl-dev
RUN		apt-get install -qqy git
RUN		apt-get install -qqy make

#RUN		git clone https://github.com/pooler/cpuminer
RUN		git clone https://github.com/ghostlander/cpuminer-neoscrypt.git

RUN		cd cpuminer-neoscrypt && ./autogen.sh
RUN		cd cpuminer-neoscrypt && ./configure CFLAGS="-O3"
RUN		cd cpuminer-neoscrypt && make

WORKDIR		/cpuminer-neoscrypt
ENTRYPOINT	["./minerd"]
