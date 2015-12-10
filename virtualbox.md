Virtual Box 
===========

Host Setup
----------
ref: https://wiki.archlinux.org/index.php/VirtualBox

# install virtual box and kernel modules
pacman virtualbox  
pacman virtualbox-host-dkms -S  
dkms install vboxhost/5.0.10

# reload the modules (see /etc/modules-load.conf for auto load)
vboxreload

# command line frontend
vboxsdl

# create VDMK file
VBoxManage internalcommands createrawvmdk -filename sda5.vmdk -rawdisk /dev/sda \
-partitions 5


