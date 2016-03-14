Install Packages from AUR 
=========================
1. get the tarball from https://aur.archlinux.org/
2. mv it to ~/build/aur
3. extract it and cd into it

# -s / --syncdeps resolve and install dependencies
# -r / --rmdeps removes the build-time dependencies after build
4. makepkg -sr

5. pacman -U pkg.tar.xz
