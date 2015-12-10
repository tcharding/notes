Kernel Dev Notes
================
** scr = kernel source i.e ~/build/linux-trees/torvalds **

Source code
-----------
$ cd ~/build/linux-kernels/grepkh

$ git clone -b staging-testing \
   git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging.git 

Config
------
$ zcat /proc/config.gz > .config
$ make nconfig

Build
-----
make mrproper
make -j6

# cp vmlinux /boot/vmlinuz-custom
# cd /boot
# mkinitcpio -g initramfs-custom -k vmlinuz-custom

Documentation 
-------------
See src/HOWTO for list of prerequisite reading.


Misc 
----

