# Compile the port for QNX

**NOTE**: QNX ports are only supported from a **Linux host** operating system

### Install automake/autoconf tools

`sudo apt install automake`

### Clone repository

`git clone git@gitlab.rim.net:qnx/osr/lighttpd1.4.git && cd lighttpd1.4`
	
### Checkout corresponding SDP branch

`git checkout qnx-sdp8-master`

or

`git checkout qnx-sdp71-master`

### Generate GNU build tool ./configure and all needed Makefiles

`./autogen.sh`

### Setup QNX SDP environment

`source <path-to-sdp>/qnxsdp-env.sh`

### Build examples and install asio headers into SDP

`JLEVEL=$(nproc) make -C qnx/build install`


**All binary files have to be installed to SDP**
* $QNX_TARGET/x86_64/usr/sbin/lighttpd
* $QNX_TARGET/x86_64/usr/sbin/lighttpd-angel
* $QNX_TARGET/aarch64le/usr/sbin/lighttpd
* $QNX_TARGET/aarch64le/usr/sbin/lighttpd-angel
