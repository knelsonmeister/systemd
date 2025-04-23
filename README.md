# systemd with systemd-shim support for MX Linux
This repo contains the debian directory necessary to build a Debian Trixie based debian package for MX Linux that has support for systemd-shim.  It needs a modified systemd-shim (available here: https://salsa.debian.org/knelsonmeister/systemd-shim or https://github.com/knelsonmeister/systemd-shim)

## Background:
Systemd-shim allows a system to boot up using a SYSV init, but still be able to support the modern programs that depend on systemd.  It is not perfect, but it allows for a Linux distribution to support both SYSV init and systemd as a choice in the grub boot menu.  MX Linux does just that.
Debian used to support systemd-shim, but support was dropped in Debian Buster.  This repo and the systemd-shim repo linked above are an effort to maintain the systemd-shim support in Debian Trixie.

## Changes:
  - Propped forward 4 patches from old systemd that were removed when systemd-shim was removed
  - Updated debian/patches/series file to add the 4 patches
  - Added a new patch for Debian Trixie

## How To Build:
NOTE: The tests phase of the compile will fail if compiling on a system not running systemd as init.  By default MX Linux does not run systemd as init, but it can be selected in the grub menu on boot.
```
# Clone from Salsa or...
git clone https://salsa.debian.org/knelsonmeister/systemd.git
# Clone from GitHub
git clone https://github.com/knelsonmeister/systemd.git
# To build just the binary packages
cd systemd
git checkout debian/trixie
dpkg-buildpackage -uc -us -b
cd ..
# To build both the binary and source packages
wget http://deb.debian.org/debian/pool/main/s/systemd/systemd_257.5.orig.tar.gz
cd systemd
git checkout debian/trixie
# NOTE: the "-i.*" will ignore all changes to the repo from the
# orig.tar.gz above (ex: this README.md file)
dpkg-buildpackage -uc -us -i.*
cd ..
```

![Systemd](http://brand.systemd.io/assets/page-logo.png)

System and Service Manager

[![Semaphore CI 2.0 Build Status](https://the-real-systemd.semaphoreci.com/badges/systemd/branches/main.svg?style=shields)](https://the-real-systemd.semaphoreci.com/projects/systemd)<br/>
[![Coverity Scan Status](https://scan.coverity.com/projects/350/badge.svg)](https://scan.coverity.com/projects/350)<br/>
[![OSS-Fuzz Status](https://oss-fuzz-build-logs.storage.googleapis.com/badges/systemd.svg)](https://oss-fuzz-build-logs.storage.googleapis.com/index.html#systemd)<br/>
[![CIFuzz](https://github.com/systemd/systemd/workflows/CIFuzz/badge.svg)](https://github.com/systemd/systemd/actions)<br/>
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/1369/badge)](https://bestpractices.coreinfrastructure.org/projects/1369)<br/>
[![Fossies codespell report](https://fossies.org/linux/test/systemd-main.tar.gz/codespell.svg)](https://fossies.org/linux/test/systemd-main.tar.gz/codespell.html)</br>
[![Weblate](https://translate.fedoraproject.org/widgets/systemd/-/master/svg-badge.svg)](https://translate.fedoraproject.org/engage/systemd/)</br>
[![Coverage Status](https://coveralls.io/repos/github/systemd/systemd/badge.svg?branch=main)](https://coveralls.io/github/systemd/systemd?branch=main)</br>
[![Packaging status](https://repology.org/badge/tiny-repos/systemd.svg)](https://repology.org/project/systemd/versions)</br>
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/systemd/systemd/badge)](https://securityscorecards.dev/viewer/?platform=github.com&org=systemd&repo=systemd)

## Details

Most documentation is available on [systemd's web site](https://systemd.io/).

Assorted, older, general information about systemd can be found in the [systemd Wiki](https://www.freedesktop.org/wiki/Software/systemd).

Information about build requirements is provided in the [README file](README).

Consult our [NEWS file](NEWS) for information about what's new in the most recent systemd versions.

Please see the [Code Map](docs/ARCHITECTURE.md) for information about this repository's layout and content.

Please see the [Hacking guide](docs/HACKING.md) for information on how to hack on systemd and test your modifications.

Please see our [Contribution Guidelines](docs/CONTRIBUTING.md) for more information about filing GitHub Issues and posting GitHub Pull Requests.

When preparing patches for systemd, please follow our [Coding Style Guidelines](docs/CODING_STYLE.md).

If you are looking for support, please contact our [mailing list](https://lists.freedesktop.org/mailman/listinfo/systemd-devel), join our [IRC channel #systemd on libera.chat](https://web.libera.chat/#systemd) or [Matrix channel](https://matrix.to/#/#systemd-project:matrix.org)

Stable branches with backported patches are available in the [stable repo](https://github.com/systemd/systemd-stable).

We have a security bug bounty program sponsored by the [Sovereign Tech Fund](https://www.sovereigntechfund.de/) hosted on [YesWeHack](https://yeswehack.com/programs/systemd-bug-bounty-program)
