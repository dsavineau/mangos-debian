# MaNGOS Debian -- README

## Informations

mangos-debian contains all debian files to create MaNGOS package on GNU/Linux Debian/Ubuntu distributions.

There is one git branch for each MaNGOS version (classic, tbc, wotlk and cata).

You need to install debian specific tools and MaNGOS dependencies (can be found in control file).

You can customize package version (with MaNGOS revision and Debian/Ubuntu codename) in changelog file with sed.

MaNGOS revision can be found with :

    $ grep "define REVISION_NR" ${MANGOS_PATH}/src/shared/revision_nr.h|awk '{print $3}'|sed -e "s/\"//g"

Debian/Ubuntu codename can be found with (require lsb-release package) :

    $ lsb_release -c -s

You have to clone this repository into your mangos source in a directory called debian. 

    $ git clone -b classic git://github.com/dsavineau/mangos-debian debian
    $ sed -i -e "s/@@REVISION@@/2389/g;s/@@CODENAME@@/squeeze/g" changelog
    $ dpkg-buildpackage -b -us -uc
    (...)
    dpkg-deb: building package `mangos-classic' in `../mangos-classic_0.12.2+r2389~squeeze1_amd64.deb'.
     dpkg-genchanges -b >../mangos-classic_0.12.2+r2389~squeeze1_amd64.changes

These scripts use TBB (libtbb-dev) and ACE (libace-dev) from Debian/Ubuntu packages on mainstream repositories.

## Distributions

mangos-debian has been tested on GNU/Linux Debian/Ubuntu distributions :

* Debian Squeeze (6.0.x)
* Debian Wheezy (7.x)
* Debian Jessie (testing)
* Ubuntu Precise (12.04)
* Ubuntu Quantal (12.10)
* Ubuntu Raring (13.04)

## License

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 2 of the License, or
  (at your option) any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU General Public License
  along with this program.  If not, see <http://www.gnu.org/licenses/>.

  You can find the full license text in the file [COPYING](COPYING) delivered with this package.
