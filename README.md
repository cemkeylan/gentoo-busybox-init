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


What this program does is, it copies the busybox 
configuration to /etc/portage/savedconfig and installs
busybox with the config file. Busybox is then built with
`static` and `savedconfig` USE flags. It then removes
sysvinit and installs its own init scripts and inittab.
We do a `busybox --install` to make sure all init and
runit programs are set in place.


Notes
-----

* Runit is set to run all services from `/var/service` by default
* Init scripts are installed to `/usr/lib/init`
* Init scripts read the OpenRC configuration files on `/etc/conf.d`
