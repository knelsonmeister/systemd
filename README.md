# systemd with systemd-shim support for MX Linux
This repo contains the debian directory necessary to build a Debian Bullseye based debian package for MX Linux that has support for systemd-shim.  It needs a modified systemd-shim (available here: https://github.com/knelsonmeister/systemd-shim)

## Background:
Systemd-shim allows a system to boot up using a SYSV init, but still be able to support the modern programs that depend on systemd.  It is not perfect, but it allows for a Linux distribution to support both SYSV init and systemd as a choice in the grub boot menu.  MX Linux does just that.
Debian used to support systemd-shim, but support was dropped in Debian Buster.  This repo and the systemd-shim repo linked above are an effort to maintain the systemd-shim support in Debian Buster and Debian Bullseye.

## Current Version: 247.2-5
Based on: http://deb.debian.org/debian/pool/main/s/systemd/systemd_247.2-5.debian.tar.xz

## Changes:
  - Propped forward 4 patches from old systemd that were removed when systemd-shim was removed
  - Updated debian/patches/series file to add the 4 patches
  - Updated debian/control to modify dependency for libpam-systemd to allow systemd-shim or systemd-sysv
  - Restored old user runtime path functionality

## How To Build:
NOTE: The tests phase of the compile will fail if compiling on a system not running systemd as init.  By default MX Linux does not run systemd as init, but it can be selected in the grub menu on boot.
```
wget http://deb.debian.org/debian/pool/main/s/systemd/systemd_247.2.orig.tar.gz
tar xf systemd_247.2.orig.tar.gz
cd systemd-stable-247.2
git clone https://github.com/knelsonmeister/systemd.git
ln -s debian/patches .
quilt push -a
dpkg-buildpackage -uc -us -b
cd ..
```
