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

RUN		apt-get install -qqy git
RUN		git clone https://github.com/doe300/VC4CL.git

RUN             mv /VC4CL /VC4CL-src
COPY            DumpAnalyzer.diff /VC4CL-src
RUN             cd /VC4CL-src && patch -p1 < DumpAnalyzer.diff

RUN             mkdir /VC4CL && cd /VC4CL && cmake ../VC4CL-src
RUN             cd /VC4CL && make
RUN             mkdir -p /etc/OpenCL/vendors/
RUN		cp -a /VC4CL/VC4CL.icd /etc/OpenCL/vendors/VC4CL.icd && cp -a /VC4CL/build/libVC4CL* /usr/local/lib

