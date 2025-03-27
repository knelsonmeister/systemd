# systemd with systemd-shim support for MX Linux
This repo contains the debian directory necessary to build a Debian Bookworm based debian package for MX Linux that has support for systemd-shim.  It needs a modified systemd-shim (available here: https://salsa.debian.org/knelsonmeister/systemd-shim or https://github.com/knelsonmeister/systemd-shim)

## Background:
Systemd-shim allows a system to boot up using a SYSV init, but still be able to support the modern programs that depend on systemd.  It is not perfect, but it allows for a Linux distribution to support both SYSV init and systemd as a choice in the grub boot menu.  MX Linux does just that.
Debian used to support systemd-shim, but support was dropped in Debian Buster.  This repo and the systemd-shim repo linked above are an effort to maintain the systemd-shim support in Debian Bookworm.

## Changes:
  - Propped forward 4 patches from old systemd that were removed when systemd-shim was removed
  - Updated debian/patches/series file to add the 4 patches
  - Added a new patch for Debian Bookworm

## How To Build:
NOTE: The tests phase of the compile will fail if compiling on a system not running systemd as init.  By default MX Linux does not run systemd as init, but it can be selected in the grub menu on boot.
```
git clone https://salsa.debian.org/knelsonmeister/systemd.git
or
git clone https://github.com/knelsonmeister/systemd.git
cd systemd
git checkout debian/bookworm
dpkg-buildpackage -uc -us -b
cd ..
```

![Systemd](http://brand.systemd.io/assets/page-logo.png)

System and Service Manager

[![Semaphore CI 2.0 Build Status](https://the-real-systemd.semaphoreci.com/badges/systemd/branches/main.svg?style=shields)](https://the-real-systemd.semaphoreci.com/projects/systemd)<br/>
[![Coverity Scan Status](https://scan.coverity.com/projects/350/badge.svg)](https://scan.coverity.com/projects/350)<br/>
[![OSS-Fuzz Status](https://oss-fuzz-build-logs.storage.googleapis.com/badges/systemd.svg)](https://oss-fuzz-build-logs.storage.googleapis.com/index.html#systemd)<br/>
[![CIFuzz](https://github.com/systemd/systemd/workflows/CIFuzz/badge.svg)](https://github.com/systemd/systemd/actions)<br/>
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/1369/badge)](https://bestpractices.coreinfrastructure.org/projects/1369)<br/>
[![CentOS CI - CentOS 8](https://jenkins-systemd.apps.ocp.ci.centos.org/buildStatus/icon?subject=CentOS%20CI%20-%20CentOS%208&job=upstream-centos8)](https://jenkins-systemd.apps.ocp.ci.centos.org/job/upstream-centos8/)<br/>
[![CentOS CI - Arch](https://jenkins-systemd.apps.ocp.ci.centos.org/buildStatus/icon?subject=CentOS%20CI%20-%20Arch&job=upstream-vagrant-archlinux)](https://jenkins-systemd.apps.ocp.ci.centos.org/job/upstream-vagrant-archlinux/)<br/>
[![CentOS CI - Arch (sanitizers)](https://jenkins-systemd.apps.ocp.ci.centos.org/buildStatus/icon?subject=CentOS%20CI%20-%20Arch%20(sanitizers)&job=upstream-vagrant-archlinux-sanitizers)](https://jenkins-systemd.apps.ocp.ci.centos.org/job/upstream-vagrant-archlinux-sanitizers/)<br/>
[![CentOS CI - Rawhide (SELinux)](https://jenkins-systemd.apps.ocp.ci.centos.org/buildStatus/icon?subject=CentOS%20CI%20-%20Rawhide%20(SELinux)&job=upstream-vagrant-rawhide-selinux)](https://jenkins-systemd.apps.ocp.ci.centos.org/view/Upstream/job/upstream-vagrant-rawhide-selinux/)<br/>
[![Fossies codespell report](https://fossies.org/linux/test/systemd-main.tar.gz/codespell.svg)](https://fossies.org/linux/test/systemd-main.tar.gz/codespell.html)</br>
[![Coverage Status](https://coveralls.io/repos/github/systemd/systemd/badge.svg?branch=main)](https://coveralls.io/github/systemd/systemd?branch=main)</br>
[![Packaging status](https://repology.org/badge/tiny-repos/systemd.svg)](https://repology.org/project/systemd/versions)</br>
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/systemd/systemd/badge)](https://api.securityscorecards.dev/projects/github.com/systemd/systemd)

## Details

Most documentation is available on [systemd's web site](https://systemd.io/).

Assorted, older, general information about systemd can be found in the [systemd Wiki](https://www.freedesktop.org/wiki/Software/systemd).

Information about build requirements is provided in the [README file](README).

Consult our [NEWS file](NEWS) for information about what's new in the most recent systemd versions.

Please see the [Code Map](docs/ARCHITECTURE.md) for information about this repository's layout and content.

Please see the [Hacking guide](docs/HACKING.md) for information on how to hack on systemd and test your modifications.

Please see our [Contribution Guidelines](docs/CONTRIBUTING.md) for more information about filing GitHub Issues and posting GitHub Pull Requests.

When preparing patches for systemd, please follow our [Coding Style Guidelines](docs/CODING_STYLE.md).

If you are looking for support, please contact our [mailing list](https://lists.freedesktop.org/mailman/listinfo/systemd-devel) or join our [IRC channel](irc://irc.libera.chat/%23systemd).

Stable branches with backported patches are available in the [stable repo](https://github.com/systemd/systemd-stable).
