FROM resin/rpi-raspbian

MAINTAINER	Richard Lee <rlee@tokyo3.com>

ENV	LD_LIBRARY_PATH=/usr/lib32:${LIBRARY_PATH}

RUN		apt-get update -qq

RUN		apt-get install -qqy pkg-config
RUN		apt-get install -qqy build-essential
RUN		apt-get install -qqy cmake
RUN		apt-get install -qqy ocl-icd-opencl-dev ocl-icd-dev
RUN		apt-get install -qqy opencl-headers
RUN		apt-get install -qqy libc6 libc6-dev
RUN		apt-get install libraspberrypi0 libraspberrypi-dev libraspberrypi-bin

RUN		apt-get install -qqy apt-utils
RUN		apt-get install -qqy libtool
RUN		apt-get install -qqy libcurl4-openssl-dev

RUN		apt-get install -qqy git
RUN		apt-get install -qqy automake libudev-dev yasm
RUN		apt-get install -qqy clang-3.9
RUN		apt-get install -qqy mesa-opencl-icd

RUN		git clone https://github.com/doe300/VC4CL.git
COPY            VC4CL-DumpAnalyzer.diff /VC4CL
RUN             cd /VC4CL && patch -p1 < VC4CL-DumpAnalyzer.diff
RUN		git clone https://github.com/doe300/VC4C.git
COPY            VC4C-main.diff /VC4C
RUN             cd /VC4C && patch -p1 < VC4C-main.diff
RUN		git clone https://github.com/doe300/VC4CLStdLib.git

RUN             cd VC4C && cmake . && make all install
RUN             cd VC4CL && cmake . && make all install

RUN		git clone https://github.com/xmrig/xmrig-amd.git


