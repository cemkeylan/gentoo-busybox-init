Gentoo Busybox-init
===================

This program swaps OpenRC and SysVinit on Gentoo, 
and effectively replaces it with busybox-init 
and busybox runit. It is quite hacky and you may
need to change the `rc.boot` script to fit your
purposes. 

You may also need to manually edit your system set
to remove sysvinit and openrc so they don't
reinstall when you are doing a system upgrade.


Instructions
------------

Just type `sudo ./install` and that's it.

You can revert anytime by running `sudo ./revert`


This program downloads the busybox source tarball, builds 
with the given configuration and installs it to 
/usr/local/bin/busybox-init. We backup the configurations
and the binaries of sysvinit with quickpkg, and then remove 
sysvinit and install our own init scripts and inittab.
We do a `/usr/local/bin/busybox-init --install` to make 
sure all init and runit programs are set in place.


Notes
-----

* Runit is set to run all services from `/var/service` by default
* Init scripts are installed to `/usr/lib/init`
* Init scripts read the OpenRC configuration files on `/etc/conf.d`
* The initscripts were originally taken from [Carbs Linux init](https://git.carbslinux.org/init/log.html)
