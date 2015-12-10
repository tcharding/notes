Arch Linux Stuff
================

### Get Source Code #
`# abs [package_name] `
`cp -i /var/abs/<pkg> /home/tobin/build/abs`
`cd /home/tobin/build/abs/<pkg>`
`makepkg -od`
use `makepkg -e` to build local package and  
`pacman -U name-of-pkg.xz` to install it.
