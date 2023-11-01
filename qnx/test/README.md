# Testing lighttpd1.4 web server on QNX

**NOTE**: QNX ports are only supported from a **Linux host** operating system

lighttpd web server normally wants to be tested on the same machine it was built on. This obviously doesn't work when cross-compiling for QNX. The gist is to build, then copy the whole lighttpd tests tree on a target. This will include all the relevant files and directory structure which lighttpd expects when running its test suite.

# Running the Test Suite

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

### Build and install all lighttpd tests into SDP

`JLEVEL=$(nproc) CPULIST=x86_64 make -C qnx/build install check`

### Then build your QNX image using mkqnximage and the following options:

`export LIGHTTPD_ROOT=$PWD`

`mkdir test_image && cd test_image`

`mkqnximage --extra-dirs=$LIGHTTPD_ROOT/qnx/test/mkqnximage --clean --run --force --test-lighttpd=$QNX_TARGET/x86_64/usr/bin/lighttpd_tests`

### Once the target has booted, the lighttpd tests will be located in /data/lighttpd_tests:

`cd /data/lighttpd`
    
`./base_testsuite.sh`

### Test execution summary

```
...
==========================================
Unit tests summary for lighttpd 1.4.71
==========================================
# TOTAL: 3
# PASS: 3
# FAIL: 0
==========================================
...
All tests successful.
Files=4, Tests=224,  2 wallclock secs ( 0.10 usr  0.00 sys +  1.13 cusr  0.00 csys =  1.23 CPU)
Result: PASS
...
==========================================
Perl tests summary for lighttpd 1.4.71
==========================================
# TOTAL: 3
# PASS: 3
# FAIL: 0
==========================================
```
