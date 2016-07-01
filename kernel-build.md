Linux Kernel Build
==================

`$ cd $KERNEL_TREE`
`$ make mrproper`

`$ zcat /proc/config.gz > .config`
`$ make nconfig`


`$ make -j8 EXTRA-CFLAGS=-W` <!-- get extra compiler warnings -->

`# make modules_install`
`# cp arch/x86/boot/bzImage /boot/vmlinuz-custom`
`# cd /boot`
`# mkinitcpio -g initramfs-custom.img -k [tab to select]`

`# make tags`
