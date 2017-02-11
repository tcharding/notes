Linux Kernel Selftest
=====================

reference:
http://www.elinux.org/images/6/61/Linux_Kernel_Selftest_Framework_-_Quality_Control_for_New_Releases.pdf 
git:
https://git.kernel.org/cgit/linux/kernel/git/shuah/linux-kselftest.git/

## Test machine

Product: Intel(R) Core(TM) i5-4590 CPU @ 3.30GHz
Description:	Ubuntu 16.04.1 LTS
Kernel: Linux 4.10.0-rc6+ x86_64 GNU/Linux

## Build on Ubuntu

The following packages are required

libcap-ng-dev
libnuma-dev
libcap-dev
libpopt-dev

$ KTREE = /path/to/kernel/tree
$ cd $KTREE/tools/testing/selftests
$ make

## Run

$ sudo make run_tests <!-- some tests require root to run -->

(don't be alarmed, your machine may appear to die as the tests start)

runs in approx 10 minutes on 
