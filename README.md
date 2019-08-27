# systemd with systemd-shim support for MX Linux
This repo contains the debian directory necessary to build a Debian Buster based debian package for MX Linux that has support for systemd-shim (available here: https://github.com/knelsonmeister/systemd-shim)

Changes:
  - Propped forward 4 patches from old systemd that were removed when systemd-shim was removed
  - Updated debian/patches/series file to add the 4 patches
  - Updated debian/control to modify dependency for libpam-systemd to allow systemd-shim or systemd-sysv

How To Build:
- tar xf systemd_241.orig.tar.gz
- cd systemd-241
- tar xf ../systemd-241-5.knelsonmeister.debian.tar.xz
- ln -s debian/patches .
- quilt push -a
- dpkg-buildpackage -uc -us -b
- cd ..
