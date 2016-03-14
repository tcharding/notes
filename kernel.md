Kernel Dev Notes
================
** scr = kernel source i.e ~/build/linux-trees/torvalds **

Source code
-----------
# Greg KH's tree
`$ git clone -b staging-testing \
   git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging.git`

# Torvalds' tree
git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
   
Compilation
-----------
`$ cd $KERNEL_TREE`

`$ zcat /proc/config.gz > .config`
`$ make nconfig`

`$ make mrproper`
`$ make -j6`

`# make modules_install`
`# cp arch/x86/boot/bzImage /boot/vmlinuz-custom`
`# cd /boot`
`# mkinitcpio -g initramfs-custom.img -k [tab to select]`

Documentation 
-------------
See src/HOWTO for list of prerequisite reading.
