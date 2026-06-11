# Package Management

A package is a compressed archive of the files required for an application to run. Package managers ensure the integrity of files by verifying checksums, simplify managing packages, grouping packages to avoid duplicate dependencies, managing dependency versions. Debian uses DPKG with the APT-GET frontend, the modern version is called APT; Red Hat uses RPM, YUM is a front end for RPM and DNF is a newer more feature rich frontend for RPM. Linux distributions are usually categorised based on the package manager they use: either Debian or Red Hat (RPM).

## RPM and YUM

RPM (Red Hat Pckage Manager) packages have the .rpm extension. It has 5 modes: installation (`rpm -ivh`), uninstalling (`rpm -e`), upgrade (`rpm -Uvh`), query (`rpm -q`), verifying (`rpm -Vf`).

YUM (Yellowdog Updater, Modified) is a high level package manager built on RPM. It references software repositories and stores configuration about them under `/etc/yum.repos.d`. You can point the config files to newer versions of software, pointing to unofficial versions. It has automatic dependency resolution.

- `yum repolist` lists all of the configured software repositories.
- `yum provides <command>` tells you which package provides a command.

## DPKG, APT-GET and APT

DPKG (Debian Package Manager) packages have the .deb extension. It has 5 modes: installation / upgrade (`dpkg -i`), uninstalling (`dpkg -r`), list (`dpkg -l`), status (`dpkg -s`), verifying (`dpkg -p <path-to-file>`).

APT-GET is a frontend over DPKG which added automatic dependency resolution and a more user friendly interface. It came along with APT-CACHE, APT-CONFIG.

APT (Advanced Package Tool) relies on DPKG and is the default package manager installed on modern Debian based distros combining the older APT-* family of commands into one base command with more opinionated output — generally found to be more useful. It uses a software repository defined in `/etc/apt/sources.list`, this can be local or remote. `apt update` updates the sources, `apt upgrade` updates software based on the configured sources, `apt edit-sources` can be used to edit the sources directy. `apt install` for installation, `apt remove` to remove, `apt search` to search in the configured source repository. 

