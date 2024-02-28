# Compile the port for QNX

**NOTE**: QNX ports are only supported from a **Linux host** operating system

### Install dependencies

`sudo apt install automake`

`sudo apt install pkg-config`

### Generate GNU build tool ./configure and all needed Makefiles

`./autogen.sh`

### Setup QNX SDP environment

`source <path-to-sdp>/qnxsdp-env.sh`

### Build and install lighttpd binaries into SDP

`JLEVEL=$(nproc) make -C qnx/build install`


**All binary files have to be installed to SDP**
* $QNX_TARGET/x86_64/usr/sbin/lighttpd
* $QNX_TARGET/x86_64/usr/sbin/lighttpd-angel
* $QNX_TARGET/aarch64le/usr/sbin/lighttpd
* $QNX_TARGET/aarch64le/usr/sbin/lighttpd-angel
